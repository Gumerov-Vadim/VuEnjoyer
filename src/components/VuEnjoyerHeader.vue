<template>
    <header>
    <img src="@/img/megusta1.png" alt="VuEnjoer" class="logo">
    <div class="menu">
    <div class="site_name">uEnjoyer</div>
        <div class="menu_button" v-for="button in buttons">
            <a :href='button.href'>{{ button.name }}</a>
        </div>
    </div>
    </header>
    </template>
    
    <script>
    export default{
        data(){
            return{
                name:'vu-enjoyer-header',
                buttons:[
                    {name:"О нас!",href:"#About"}
                ]
            }
        },
    }
    </script>
    
    <style scoped>
    header{
        top:0;
        position: fixed;
        width: 100%;
        height: 100px;
        background-color: #41B882;
        display: inline-flex;
        align-items: flex-end;
        z-index: 666;
        border-bottom: 1px solid #41B882;
    }
    .logo{
        height: 100%;
        width: auto;
    }
    .menu{
        height: 62%;
        width: 100%;
        background-color: #35495e;
        display: flex;
        align-items: flex-end;
    }
   a{
        color: #41B882;
        font-family: Arial;
        height: 100%;
        font-size: 300%;
        text-decoration: none;
   }
    .site_name{
        align-items: flex-end;
        color: #41B882;
        font-family: Arial;
        height: 100%;
        font-size: 300%;
    }
    *{
        border: border-box;
        margin: 0;
        padding: 0;
    }
    </style>