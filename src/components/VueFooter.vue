<template>
<footer>
    <div class="footer_content">
        <div class="title">our contacts</div>
        <div v-for="contact in contacts" class="contact">
            <div class="contact_icon"><img v-bind:src="contact.url" :alt="contact.text">{{ contact.text }}</div>
            <div class="contact_text"></div>
        </div>
        <div>All icons by <a target="_blank" href="https://icons8.com">Icons8.</a> Ty!</div>
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
                    {url:require("@/img/contacts/github_icon.png"),text:"git hub"},
                    {url:require("@/img/contacts/mail_icon.png"),text:"mail"},
                    {url:require("@/img/contacts/phone_icon.png"),text:"phone"}
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
    padding-left: 20px;
    display: flex;
    align-items: center;
    flex-direction: row;
    justify-content: space-around;
}
</style>