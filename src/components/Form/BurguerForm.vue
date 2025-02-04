<template>
    <div>
        <p>Componente de menssagem</p>

        <div>
            <form id="burger_form">
                <div class="input_container">
                    <label for="name">Name</label>
                    <input type="text" id="name" name="name" v-model="name" placeholder="Type your full name">
                </div>

                <div class="input_container">
                    <label for="bread">Select your bread</label>
                    <select type="select" name="bread" id="bread" v-model="bread">
                        <option value="">Select one bread</option>
                        <option value="brioche">Brioche</option>
                    </select>
                </div>

                <div class="input_container">
                    <label for="meat">Select your meat</label>
                    <select type="select" name="meat" id="meat" v-model="meat">
                        <option value="">Select one meat</option>
                        <option value="picanha">Picanha</option>
                    </select>
                </div>

                <div id="opcionais-container" class="input_container">
                    <label id="opcionais-title" for="opcionais">Select your extra</label>
                    <div class="checkbox-container">
                        <input type="checkbox" name="opcionais" v-model="opcionais" value="salame">
                        <span>Salame</span>
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
    export default{
        name:'BurgerForm'
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