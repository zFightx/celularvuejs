<template>
    <div id="siteUber">
        <div class="site-uber-title">
            <img src="../../assets/uber.png" alt="">
            <p>Uber</p>
        </div>
        <div class="ubers">
            <p>Ubers trabalhando agora</p>
            <ul>
                <li>
                    <div>
                        <p>Nome</p>
                        <p>Carro</p>
                    </div>
                    
                    <p>Distância</p>
                </li>
                <li
                    v-for="(item, index) in trabalhando"
                    v-bind:key="index"
                >
                    <div>
                        <p>{{item.nome}}</p>
                        <p>{{item.carro}}</p>
                    </div>
                    
                    <p>{{item.distancia}} Km</p>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
    
export default {
    name: "SiteUber",
    data(){
        return({
            trabalhando:[
                {nome: "Alexandre Souza", carro: "Ford 102", distancia: 100.5},
                {nome: "Azazel", carro: "Chvrolete 102", distancia: 50.9},
                {nome: "Rodrigo Avlis", carro: "BMW 102", distancia: 200.0},
            ]
        })
    }
}
</script>

<style>

    .fundo_uber{
        background-color: rgb(0, 0, 0) !important;
    }
    .site-uber-title{
        width: 100%;
        text-align: center;
        color: white;
        margin-top: 3vh;
    }
    .site-uber-title img{
        width: 30%;
        box-shadow: 1px 1px 10px 5px rgb(177, 177, 177);
    }
    .site-uber-title > p{
        margin-top: 1vh;
        font-size: 4vh;
    }
    .ubers{
        width: 100%;
        margin: auto;
        margin-top: 5vh;

        background-color: whitesmoke;

        border-radius: 10px;
        
    }
    .ubers >  p{
        text-align: center;
        font-size: 2.4vh;
        padding: 2vh 0;
    }
    .ubers li{
        width: 100%;

        display: flex;
        flex-direction: row;
        justify-content: space-between;
        align-items: center;
        padding: 1vh;

        border-bottom: 1px dotted gray;
    }
    .ubers li div p{
        font-size: 1.8vh;
    }
    .ubers li:first-child p{
        color: black;
    }
    .ubers li:first-child{
        margin-bottom: 2vh;
    }
    .ubers li:last-child{
        border-bottom: 1px dotted rgba(128, 128, 128, 0);
    }

    .ubers li p{
        color: rgb(73, 73, 73);
    }
    .ubers li > p{
        font-size: 2vh;
        font-weight: 600;
    }
</style>