<template>
    <div>
            <Message :msg="msg" v-show="msg"/>

        <div>
            <form id="burger_form" @submit="createBurguer($event)">
                <div class="input_container">
                    <label for="name">Name</label>
                    <input type="text" id="name" name="name" v-model="name" placeholder="Type your full name">
                </div>

                <div class="input_container">
                    <label for="breads">Select your bread</label>
                    <select type="select" name="breads" id="breads" v-model="breads">
                        <option value="">Select one bread</option>
                        <option v-for="bread in breads" :key="bread.id" value="bread.tipo">{{ bread.type }}</option>
                    </select>
                </div>

                <div class="input_container">
                    <label for="meat">Select your meat</label>
                    <select type="select" name="meat" id="meat" v-model="meat">
                        <option value="">Select one meat</option>
                        <option v-for="meat in meats" :key="meat.id" value="meat.type">{{ meat.type }}</option>
                    </select>
                </div>

                <div id="opcionais-container" class="input_container">
                    <label id="opcionais-title" for="options">Select your extra</label>
                    <div class="checkbox-container" v-for="option in optiondata" :key="option.id">
                        <input type="checkbox" name="options" v-model="options" :value="option.type">
                        <span>{{ option.type }}</span>
                    </div>
                </div>

                <div class="input_container">
                    <input type="submit" class="submit-btn" value="Create my burger">
                </div>
            </form>
        </div>
    </div>
</template>

<script>
    import Message from '../Message/Message.vue';

    export default{
        components:{
            Message
        },
        name:'BurgerForm',
        data(){
            return{
                breads:null,
                meats: null,
                optiondata:null,
                name:null,
                brad:null,
                meat:null,
                options:[],
                msg:null,

            }
        },
        methods:{
            async getIngredients(){
                const req = await fetch("http://localhost:3000/ingredientes");
                const data = await req.json();

                //console.log(data);
                this.breads = data.breads;
                this.meats = data.meats;
                this.optiondata = data.options;
            },
            async createBurguer(e){
                e.preventDefault()

                const data = {
                    name: this.name,
                    meat: this.meat,
                    bread:this.bread,
                    options: Array.from(this.options),
                    status: "Requested"
                }

                const dataJson = JSON.stringify(data);

                const req = await fetch("http://localhost:3000/burgers" ,{
                    method: 'POST',
                    headers: {"Content-Type" : "apllication/json"},
                    body: dataJson
                });

                const res = await req.json();

                this.msg =`Order created succesfully`

                //cleaning the message
                setTimeout(() => this.msg = "" , 3000)

                this.name = '';
                this.meat = '';
                this.bread = '';
                this.options = '';


            }

        },
        mounted(){
            this.getIngredients();
        }
    }
</script>

<style scoped>
        #burger_form{
            max-width: 400px;
            margin: 0 auto;
        }

        .input_container{
            display: flex;
            flex-direction: column;
            margin-bottom: 20px;

        }

        label{
            font-weight: bold;
            margin-bottom: 15px;
            color: #222;
            padding: 5px 10px;
            border-left:  4px solid #FCBA03;
        }

        input,select{
            padding:5px 10px;
            width: 300px;
        }

        #opcionais-container{
            flex-direction: row;
            flex-wrap: wrap;
        
        }

        #opcionais-title{
            width: 100%;
        }

        .checkbox-container{
            display: flex;
            align-items: flex-start;
            width: 50%;
            margin-bottom: 20px;
        }

        .checkbox-container span,
        .checkbox-container input{
            width: auto;
        }

        .checkbox-container span{
            margin-left: 6px;
            font-weight: bold;
        }

        .submit-btn{
            background-color: #222;
            color: #FCBA03;
            font-weight: bold;
            border: 2px solid #222;
            padding: 10px;
            font-size: 16px;
    
            cursor: pointer;
            transition: .5s;

        }

        .submit-btn:hover{
            background-color: transparent;
            color: #222;
        }
</style>