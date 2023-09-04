<template>
    <div>
    <ul>
    <li v-for="com in comments" class="comment">
        <div class="comment_author">
            <div class="user">
                <div class="avatar"></div>
                <div class="name">{{ com.comment_author }}</div>
            </div>
        </div>
        <div class="comment_content">{{com.comment_content}}</div>
        <div class="comment_rating">
            <div @click="ReplyClicked(com)" class="reply">Ответить</div>
            <div class="rating">
                <div class="like_counter">{{com.like_counter}}</div>
                <div @click="LikeClicked(com)" class="like_button">
                <div v-if="!com.isLiked" class="like white_like"></div>
                <div v-else class="like green_like"></div>
                </div>
            </div>
        </div>
        <comment-input v-bind:replylist="com.replylist" v-on:send="SendReply" v-if="com.isReplyClicked" class="reply_field"/>
        <comment v-bind:comments="com.replylist"></comment>
    </li>
    </ul>
    </div>
</template>

<script>
import Comment from "@/components/Comment.vue"
import CommentInput from "@/components/CommentInput.vue"

export default{   
    components:{
            Comment,CommentInput
        },
    
    props:{
        comments:{
        type: Array,
        required:true}
    },
    methods:{
        LikeClicked(com){
            if(com.isLiked===true){
               com.like_counter--;
                com.isLiked=false;
            }
            else{
                com.like_counter++;
                com.isLiked=true;
            }
        },
        ReplyClicked(com){
            if(com.isReplyClicked===true){
                com.isReplyClicked=false;
            }
            else{
                com.isReplyClicked=true;
            }

        },
        SendReply(com,replylist){
                if(!com.replylist){
                    com.replylist=[];
                }
                replylist.push(com);
               }
            }
}
</script>

<style scoped>
*{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
.comment{
    border:#9d9 5px solid;
    /* margin: 15px; */
    padding: 10px;
    min-width:300px;
    width: max-content;
    max-width: 600px;
    display: flex;
    flex-direction: column;
    background-color: rgb(66, 66, 66);
    color: white;
}
.comment_author{
    border-bottom:#9d9 1px solid;
    font-size: 28px;
}
.comment_rating{
    height: 50px;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    font-size: 24px;
}
.comment_content{
    font-size: 20px;
}
.like{
    width: 35px;
    height: 35px;
    position: absolute;
}
.white_like{
    background-image: url(@/img/white_like.png);
    background-size: cover;
}
.green_like{
    background-image: url(@/img/green_like.png);
    background-size: cover;
}
.reply{
    position: relative;
    display: flex;
    flex-direction: column-reverse;
    cursor: pointer;
    user-select: none;
}
.reply::after{
    content: "";
    position: absolute;
    background-image: url(@/img/reply.png);
    background-size: 35px 35px;
    height: 35px;
    width: 35px;
    right: -40px;
    bottom: 0px;
}

.rating{
    display: flex;
    align-items: flex-end;
}
.like_button{
    position: relative;
    width: 35px;
    height: 35px;
    cursor: pointer;
}
.like_counter{
    margin-right: 5px;
    user-select: none;
}
ul{
    /* background-color: #35495e; */
    /* padding: 20px 0 20px 0; */
    display: flex;
    /* flex-direction: column; */
    flex-wrap: wrap;
    align-items: center;
}
</style>