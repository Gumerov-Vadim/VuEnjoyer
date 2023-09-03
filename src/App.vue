<template>
<div class="comment_input">
    <div class="comment_header">
        Оставьте комментарий!
    </div>
    <input type="text">
    <div class="send">
        <div class="send_text">Отправить!</div>
        <div class="send_icon"></div>
    </div>
</div>   
</template>
    
    <script>
    export default{
        data(){
            return{
            }
        }
    }
    </script>
    
    <style scoped>
    .comment_input{
        display: flex;
        flex-direction: column;
        width: 600px;
        padding: 10px;
        background-color: #8DDCB8;
    }
    input{
        background-color: #8DDCB8;
    }
    .send{
        color:#71DCAB;
        background-color: #15784B;
        display: flex;
        flex-direction: row;
        justify-content: flex-end;
    }
    .send_icon{
        height: 26px;
        width: 26px;
        background-size: cover;
        background-image: url(@/img/send.png);
    }
    *{
        font-family: Arial, Helvetica, sans-serif;
    }
    </style>