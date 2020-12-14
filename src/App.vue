<template>
  <div id="app">
    <!-- <div id="molde-celular">
      
    </div> -->
    <div id="telas">
      <div id="tela-inicial">
        <div
          class="aplicativo"
          v-bind:class="{borrado: (appAberto === 'Menu')}"
          v-for="(item,index) in apps"
          v-bind:key="index"
          v-on:click="abrirApp(item)"
        >
          <img 
            v-bind:src="item.icon" 
            v-bind:alt="item.nome" 
            v-bind:title='item.nome'>
        </div>

        <div id="menu"
          v-if="(appAberto === 'Menu')"
        >
          <div
            class="aplicativo"
            v-for="(item,index) in apps_menu"
            v-bind:key="index"
            v-on:click="abrirApp(item)"
          >
            <img 
              v-bind:src="item.icon" 
              v-bind:alt="item.nome" 
              v-bind:title='item.nome'>
            <p>{{item.nome}}</p>
          </div>
        </div>
        
        <Telefone
          v-if="(appAberto === 'Telefone')"
        ></Telefone>

        <Chrome
          v-else-if="(appAberto === 'Chrome')"
        ></Chrome>

      </div>
    </div>
    
  </div>
</template>

<script>

import Telefone from './apps/telefone'
import Chrome from './apps/chrome'

export default {
  name: 'App',
  components: {
    Telefone,
    Chrome
  },
  data(){
    return({
      appAberto: '',
      apps: [
        {nome: "Telefone", icon: require('./assets/phone.png')},
        {nome: "Menu", icon: require('./assets/menu.png')},
        {nome: "SMS", icon: require('./assets/sms.png')}
      ],
      apps_menu: [
        {nome: "Whatsapp", icon: require('./assets/whatsapp.png')},
        {nome: "Instagram", icon: require('./assets/instagram.png')},
        {nome: "Facebook", icon: require('./assets/facebook.png')},
        {nome: "Messenger", icon: require('./assets/messenger.png')},
        {nome: "SMS", icon: require('./assets/sms.png')},
        {nome: "Chrome", icon: require('./assets/chrome.png')},
      ]
    })
  },
  methods:{
    abrirApp(item){
      this.appAberto = item.nome;
    }
  }
}
</script>

<style>
  *{
    margin: 0;
    padding: 0;
    box-sizing: border-box;

    font-family: 'Roboto', sans-serif;
    list-style: none;
  }

  #app{
    width: 40vh;
    height: 70vh;    

    position: absolute;
    right: 5%;
    bottom: 5%;

    border-radius: 30px;
    overflow: hidden;

    display: flex;
    justify-content: center;
    align-content: center;

    background-image: url('./assets/celular.png');
    background-repeat: no-repeat;
    background-size: 100% 100%;
  }

  #molde-celular{
    width: 100%;
    height: 100%;

    

    /* position: absolute;
    z-index: 1;

    padding: 6%; */
  }

  #telas{
    width: 97%;
    height: 98%;
    margin: auto;
    border-radius: 35px;
    overflow: hidden;
  }

  #tela-inicial{
    width: 100%;
    height: 100%;

    background-image: url('./assets/fundo.jpg');
    background-size: 95% 99%;
    background-position: center;
    background-repeat: no-repeat;

    display: flex;
    flex-direction: row;
    align-content: flex-end;    
    align-items: flex-end;
    justify-content: space-around;

    padding: 5vh;

    position: relative;
  }

  .aplicativo{
    width: 8vh;
    height: 8vh;
    
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    border-radius: 10px;
  }
  .aplicativo:hover{
    background-color: rgba(100, 100, 100, 0.5);
  }
  .aplicativo img{
    width: 80%;
    height: 80%;        
  }

  .aplicativo.borrado img{
    filter: blur(5px);
  }

  #menu .aplicativo{
    width: 8vh;
    height: 8vh;
    
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    border-radius: 10px;

    margin-right: 0.9vh;
    margin-bottom: 2vh;
  }

  #menu .aplicativo img{
    width: 5vh;
    height: 5vh;     
  }
  #menu .aplicativo p{
    margin-top: 0.5vh;
    font-size: 1.8vh;
    color: rgb(212, 211, 211);

    font-family: 'Roboto', sans-serif;
  }

  #menu{
    width: 100%;
    height: 100%;

    top: 0%;
    position: absolute;
    padding: 2vh 1.2vh;

    background-color: rgba(7, 7, 7, 0.5);
    
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: flex-start;
    align-content: flex-start;

    border-radius: 20px;

    animation: move-open;
    animation-duration: 0.3s;
  }
  @keyframes move-open{
    0%{
      top: 100%;
      opacity: 0.0;
    }
    100%{
      top: 0%;
      opacity: 1;
    }
  }
</style>
