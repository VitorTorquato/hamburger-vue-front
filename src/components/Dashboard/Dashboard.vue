<script>

    import Message from '../Message/Message.vue';
    export default{
        components:{
            Message
        },
        name:'Dashboard',
        data(){
            return{
                burgers: null,
                burger_id:null,
                status:[],
                msg:null
            }
        },
        methods:{
            async getOrders(){
                const req = await fetch("http://localhost:3000/burgers")
                const data = await req.json();

                this.burgers = data;

                //getting status
                this.getStatus();
            },
            async getStatus(){
                const req = await fetch("http://localhost:3000/status");
                const data = await req.json();

                this.status = data;
            },
            async deleteBurguer(id){
                const req = await fetch(`http://localhost:3000/burgers/${id}` , {
                    method: "DELETE"
                });

                this.msg =`Order deletead succesfully`

                //cleaning the message
                setTimeout(() => this.msg = "" , 3000)

                const res = await req.json();

                this.getOrders();

            },
            async updateBurger(e,id){

                   const option = e.target.value;
                   
                   const dataJson = JSON.stringify({status: option});

                   const req = await fetch(`http://localhost:3000/burgers/${id}` , {
                    method: "PATCH",
                    headers:{"Content-type": "application/json"},
                    body: dataJson
                   });

                   const res = await req.json();

                   console.log(res);
            }

        },
        mounted(){
            this.getOrders()
        }
    }
</script>

<template>
    <Message :msg="msg" v-show="msg"/>
   <div id="burger-table">
    <div>
      <div id="burger-table-heading">
      
        <div>Client:</div>
        <div>Bread:</div>
        <div>Meat:</div>
        <div>Options:</div>
        <div>Actions:</div>
      </div>
    </div>
    <div id="burger-table-rows">
      <div class="burger-table-row" v-for="burger in burgers" :key="burger.id">
   
        <div>{{ burger.name }}</div>
        <div>{{ burger.bread }}</div>
        <div>{{ burger.meat }}</div>
        <div>
          <ul>
            <li v-for="(option, index) in burger.options" :key="index">{{ option }}</li>
          </ul>
        </div>
        <div>
          <select name="status" class="status" @change="updateBurger($event , burger.id)">
            <option v-for="s in status" :key="s.id" :value="s.type" :selected="burger.status == s.type">
                {{ s.type }}                
            </option>
          </select>
          <button class="delete-btn" @click="deleteBurguer(burger.id)">Cancel</button>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>

#burger-table {
    max-width: 1200px;
    margin: 0 auto;
  }

  #burger-table-heading,
  #burger-table-rows,
  .burger-table-row {
    display: flex;
    flex-wrap: wrap;
  }

  #burger-table-heading {
    font-weight: bold;
    padding: 12px;
    border-bottom: 3px solid #333;
  }

  .burger-table-row {
    width: 100%;
    padding: 12px;
    border-bottom: 1px solid #CCC;
  }

  #burger-table-heading div,
  .burger-table-row div {
    width: 19%;
  }

  #burger-table-heading .order-id,
  .burger-table-row .order-number {
    width: 5%;
  }

  select {
    padding: 12px 6px;
    margin-right: 12px;
  }

  .delete-btn {
    background-color: #222;
    color:#fcba03;
    font-weight: bold;
    border: 2px solid #222;
    padding: 10px;
    font-size: 16px;
    margin: 0 auto;
    cursor: pointer;
    transition: .5s;
  }
  
  .delete-btn:hover {
    background-color: transparent;
    color: #222;
  }


</style>