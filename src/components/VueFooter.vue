<template>
<footer>
    <div class="footer_content">
        <div class="title">our contacts</div>
        <div v-for="contact in contacts" class="contact">
            <a :href="contact.href" class="contact_card">
            <img v-bind:src="contact.url" :alt="contact.name">
            <div class="contact_text">
                <div class="contact_text_top">{{ contact.name }}</div>
                <div class="contact_text_bottom">{{ contact.text }}</div>
            </div>
        </a>
        </div>

        <div class="contact">All icons by <a style="color: #75AED6;" target="_blank" href="https://icons8.com">Icons8.</a> Ty!</div>
    </div>
    <div class="footer_footer"></div>
</footer>
</template>

<script>
    export default{
        data(){
            return{
                name:'vue-footer',
                contacts:[
                    {url:require("@/img/contacts/github_icon.png"),name:"git hub",text:"my github",href:"https://github.com/"},
                    {url:require("@/img/contacts/mail_icon.png"),name:"mail",text:"mymail@mail.ru",href:"https://mail.google.com/"},
                    {url:require("@/img/contacts/phone_icon.png"),name:"phone",text:"88005553535", href:"#"}
                ]
            }
        }
    }
</script>

<style>
footer{
    font-family: Arial, Helvetica, sans-serif;
    height: 100px;
    width: 100%;
    background-color:#476981;
    border-top: #4481AD 10px solid;
}
.footer_content{
    height: 80px;
    width: 100%;
    background-color: #164B70;
    color:#4481AD;
    font-size: 300%;
    display: flex;
    align-items: center;
    flex-direction: row;
    justify-content: space-around;
}
.contact{
    font-size: 20px;
}
.contact_card{
    display: flex;
    align-items: center;
    justify-content: left;
}
.contact_text_top{
    color: #4481AD;
}
.contact_text_bottom{
    color: #75AED6;
}
a{
    font-style: normal;
    text-decoration: none;
}
</style>