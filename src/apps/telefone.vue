<template>
    <div id="telefone">
        <div class="digitado">
            <p v-html="digitado">Digite um número</p>
            <div v-on:click="removerDigito()"><img src="../assets/delete.png" alt=""></div>
        </div>
        <div class="teclado">
            <ul>
                <li v-on:click="digitar(1)"><p>1</p></li>
                <li v-on:click="digitar(2)"><p>2</p></li>
                <li v-on:click="digitar(3)"><p>3</p></li>
                <li v-on:click="digitar(4)"><p>4</p></li>
                <li v-on:click="digitar(5)"><p>5</p></li>
                <li v-on:click="digitar(6)"><p>6</p></li>
                <li v-on:click="digitar(7)"><p>7</p></li>
                <li v-on:click="digitar(8)"><p>8</p></li>
                <li v-on:click="digitar(9)"><p>9</p></li>
                <li v-on:click="digitar('*')"><p>*</p></li>
                <li v-on:click="digitar(0)"><p>0</p></li>
                <li v-on:click="digitar('#')"><p>#</p></li>
            </ul>
            <img src="../assets/phone.png" alt="">
        </div>
    </div>
</template>

<script>
    
export default {
    name:"Telefone",
    data(){
        return({
            digitado: ''
        })
    },
    methods:{
        digitar(num){
            this.digitado = this.digitado + num;
        },
        removerDigito(){
            if(this.digitado)
                this.digitado = this.digitado.slice(0, this.digitado.length-1);
        }
    }
}
</script>

<style>
    #telefone{
        width: 100%;
        height: 100%;

        top: 0%;
        position: absolute;
        padding: 2vh 1.2vh;

        background-color: whitesmoke;
        border-radius: 20px;

        animation: move-open;
        animation-duration: 0.3s;
    }

    #telefone *{
        font-family: 'Roboto', sans-serif;
    }

    .digitado{
        width: 100%;
        height: 6vh;
        padding: 1vh 0;

        border-bottom: 1px dotted gray;
        
        position: relative;
    }
    .digitado p{
        text-align: center;
        
        font-size: 3vh;
        font-weight: 700;
    }
    .digitado div{
        width: 10%;
        
        position: absolute;
        top: 50%;
        right: 5%;
        transform: translateY(-50%);
    }
    .digitado img{
        width: 100%;
    }
    .teclado ul{
        width: 100%;
    }
    .teclado li{
        display: inline-block;
        width: 32%;
        height: 8vh;

        text-align: center;
        
        /* background-color: gray; */
        margin-bottom: 1vh;
        margin-right: 1%;
        cursor: pointer;
    }

    .teclado li p{
        width: 50%;
        height: 50%;
        margin: auto;
        margin-top: 2vh;

        line-height: 4vh;

        /* background-color: black; */
        color: rgb(49, 122, 231);
        border-radius: 20px;
        font-size: 3vh;
        font-weight: 400;
        text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.233);
        border: 1px solid rgba(0, 0, 255, 0);
        
    }
    .teclado li:active p{
        box-shadow: 1px 1px 10px 10px rgba(34, 117, 241, 0.336);
    }
    .teclado li p:active{
        /* border: 1px solid rgba(34, 117, 241, 0.336); */
        box-shadow: 1px 1px 10px 10px rgba(34, 117, 241, 0.336);
    }

    .teclado{
        text-align: center;
    }

    .teclado img{
        width: 8vh;
        margin-top: 5vh;
    }
</style>