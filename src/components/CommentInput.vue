<template>
    <div class="comment_input">
        <div class="comment_header">
            Оставьте комментарий!
        </div>
        <textarea @keypress.enter="sendComment" v-model="comment.comment_content" name="comment_field" id="comment_field" cols="30" rows="10" placeholder="Напишите, что вы думаете..." ></textarea>
        <div class="comment_footer">
            <div class="send_button">
                <div @click="sendComment" class="send_text">Отправить!</div>
                <div class="send_icon"></div>
            </div>
        </div>
    </div>   
    </template>
        
        <script> 
        export default{
            props:{
                replylist:{
                    Array
                }
            },
            data(){
               
                return{
                    name:'comment-input',
                    comment: {
                        comment_author:"Ваше имя!",
                        comment_content:"",
                        isLiked:false,
                        like_counter:0
                    },
                    propinit:this.replylist
                }
            },
            methods:{
                sendComment(){
                    this.comment.id=Date.now();
                    this.$emit('send',this.comment,this.propinit);
                    this.comment={
                        comment_author:"Ваше имя!",
                        comment_content:"",
                        isLiked:false,
                        like_counter:0
                    }
                    }
            }
        }
        </script>
        
        <style scoped>
        .comment_input{
            color: white;
            display: flex;
            flex-direction: column;
            padding: 10px;
            background-color: #41B882;
        }
        textarea{
            outline : none;
            resize: none;
            background-color: #15784B;
            min-height: 100px;
            max-height: 300px;
            color: white;
        }
        textarea::placeholder{
            color: #41B882;
        }
        .comment_footer{
            display: flex;
            flex-direction: row;
            justify-content: flex-end;
            align-items: flex-end;
        }
        .send_button{
            margin: 2px 0 0 2px;
            padding: 2px;
            border-radius: 5px;
            display: flex;
            justify-content: flex-end;
            align-items: flex-end;
            background-color: #478A6C;
            color: #41B882;
            cursor: pointer;
        }
        .send_button:hover{
            color:#98E752 ;
            box-shadow:0 0 0 1px #98E752 ;
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