<template>
    <div id="chrome"
        v-bind:class="{
            fundo_chrome: true,
            fundo_uber: (accessUrl === sugestoes[2].link)
        }"
    >
        <div class="google-image"
            v-if="!inPesquisa && !accessUrl"
        >
            <img src="../assets/google.png" alt="">
        </div>
        <div class="pesquisa"
            v-bind:class="{google_trans: inPesquisa}"
        >
            <input type="text" placeholder="Digitar endereço da página que deseja entrar"
                v-on:focus="isInPesquisa(true)"
                v-on:blur="isInPesquisa(false)"
                v-model="url"
            >
        </div>
        <div class="sugestoes"
            v-if="!accessUrl"
        >
            <ul>
                <li
                    v-for="(item, index) in sugestoes"
                    v-bind:key="index"
                    v-on:click="acessarUrl(item.link)"
                >
                    <img 
                        v-bind:src="item.icon" 
                        v-bind:alt="item.nome"
                        v-bind:title="item.nome"
                    >
                    <p>{{item.nome}}</p>
                </li>
            </ul>
        </div>

        <SiteUber
            v-if="accessUrl === sugestoes[2].link"
        ></SiteUber>

    </div>
</template>

<script>

import SiteUber from '../components/sites/uber'

export default {
    name:'Chrome',
    components:{
        SiteUber
    },
    data(){
        return({
            inPesquisa: false,
            url: '',
            accessUrl: '',
            sugestoes: [
                {nome: "Mecanicos", link: "mecanica.com.br", icon: require('../assets/icon_mecanica.png')},
                {nome: "Consultas Hospital", link: "hospital.com.br", icon: require('../assets/icon_hospital.png')},
                {nome: "Peça já seu Uber", link: "uber.com.br", icon: require('../assets/icon_uber.png')},
                {nome: "Compre seu Carro", link: "concessionaria.com.br", icon: require('../assets/icon_concessionaria.png')}
            ]
        })
    },
    methods:{
        isInPesquisa(valor){
            this.inPesquisa = valor;
        },
        acessarUrl(link){
            this.url = link;
            this.accessUrl = link;
        }
    }
}
</script>

<style>
    #chrome{
        width: 100%;
        height: 100%;

        top: 0%;
        position: absolute;
        padding: 2vh 1.2vh;

        border-radius: 20px;        

        animation: move-open;
        animation-duration: 0.3s;
        overflow: auto;
    }

    .fundo_chrome{
        background-color: whitesmoke;
    }

    .google-image{
        width: 50%;
        
        margin: auto;
        margin-top: 10vh;
        margin-bottom: 2vh;
        overflow: hidden;
    }

    .google-image img{
        width: 100%;
    }

    .google_trans{
        animation: google-sumir;
        animation-duration: 0.5s;

        margin-top: 12vh;
    }

    .pesquisa{
        width: 90%;
        margin: auto;

        transition: 1s all;
    }

    .pesquisa input{
        width: 100%;
        border-style: none;
        border-radius: 20px;
        padding: 1.2vh;
        font-size: 1.8vh;

        background-color: rgb(218, 216, 216);
    }
    .pesquisa input:focus{
        outline: none;
    }

    .sugestoes{
        width: 90%;
        margin: auto;
        margin-top: 5vh;
    }
    .sugestoes ul li{
        
        width: 25%;
        height: 10vh;
        text-align: center;
        font-size: 1.7vh;
        font-weight: 500;
        color: rgb(92, 92, 92);

        display: inline-block;
        margin-right: 2vh;

        cursor: pointer;
    }

    .sugestoes ul li img{
        width: 80%;
        background-color: #ddd;
        padding: 1vh;

        border-radius: 20px;
    }
    .sugestoes ul li p{
        max-width: 10ch;
        text-overflow: ellipsis;
        overflow-wrap: normal;
        overflow: hidden;
        white-space: nowrap;
    }

    @keyframes google-sumir{
        0%{
            margin-top: 12vh;
        }
        100%{
           margin-top: 0;
        }
    }
</style>