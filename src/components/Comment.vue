<template>
    <div>
    <ul>
    <li v-for="com in propcomments" class="comment">
        <div class="comment_author">
            <div class="user">
                <div class="avatar"></div>
                <div class="name">{{ com.name }}</div>
            </div>
        </div>
        <div class="comment_content">{{com.body}}</div>
        <div class="comment_rating">
            <div class="comment_button">
            <div @click="ReplyShowClicked(com)" class="show_reply_button">Показать {{ com.reply_counter }}</div>
            <div @click="ReplyClicked(com)" class="reply">Ответить</div>
            </div>
            <div class="rating">
                <div class="like_counter">{{com.like_counter}}</div>
                <div @click="LikeClicked(com)" class="like_button">
                <div v-if="!com.isLiked" class="like white_like"></div>
                <div v-else class="like green_like"></div>
                </div>
            </div>
        </div>
        <comment-input v-bind:replylist="com.replylist" v-on:send="SendReply" v-if="com.isReplyClicked" class="reply_field"/>
        <comment class="reply_list" v-show="com.IsReplyShow" v-bind:propcomments="com.replylist"></comment>
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
        propcomments:{
        type: Array,
        required:true}
    },
    data(){
        return{
            comments:this.propcomments
        }
    },
    methods:{
        ReplyShowClicked(com){
          com.IsReplyShow = !com.IsReplyShow;
          com.reply_counter = this.CommentsCount(com.replylist);
           
        },
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
           com.isReplyClicked=!com.isReplyClicked;
            this.$emit('open',com,this.comments);
        },
        SendReply(com,replylist){
                if(!com.replylist){
                    com.replylist=[];
                }
                replylist.push(com);
                this.updateReplyCount();
                },
        CommentsCount(com_list){
            let length = 0;
            length += com_list.length;
            com_list.forEach(com => {
                if(com.replylist){
                length+=this.CommentsCount(com.replylist);
            }
            });
            return length;
            },
        updateReplyCount(){
            this.$nextTick(()=>{
            this.comments.forEach(com=>{
               com.reply_counter = this.CommentsCount(com.replylist); 
            })
            });
        }
        },
        watch: {
            propcomments(newVal) {
                //инициализация комментариев
                this.comments = newVal;
                this.comments.forEach(com => {
                    if(!com.like_counter){com.like_counter = 0;}
                    if(!com.replylist){com.replylist=[];}
                //    com.reply_counter = this.CommentsCount(com.replylist);
                this.updateReplyCount();
                });
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
    min-width:420px;
    width: max-content;
    max-width: 900px;
    display: flex;
    flex-direction: column;
    background-color: rgb(66, 66, 66);
    color: white;
}
.comment_author{
    border-bottom:#9d9 1px solid;
    font-size: 28px;
}
.comment_button{
    display: flex;
    align-items: flex-end;
    flex-direction: row;
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
    margin: 0 0 0 65px;
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
.show_reply_button{
    position: relative;
    display: flex;
    flex-direction: column-reverse;
    cursor: pointer;
    user-select: none;
}
.show_reply_button::after{
    content: "";
    position: absolute;
    background-image: url(@/img/show_reply.png);
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