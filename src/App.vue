<template>
    <div class="app">
       <vu-enjoyer-header/>
       <about/>
       <div class="comment_box">
        <comment-input v-bind:replylist="this.comments" v-on:send="sendComment"/>
         
        <comment v-on:open="closeReplyDialogs" v-bind:propcomments="this.comments"/>
        </div>
        <vue-footer/>
    </div>
</template>
    
    <script>
    import About from "@/components/About.vue"
    import Comment from "@/components/Comment.vue"
    import CommentInput from "@/components/CommentInput.vue"
    import VuEnjoyerHeader from "@/components/VuEnjoyerHeader.vue"
    import VueFooter from "@/components/VueFooter.vue"
    import axios from "axios"
// import { pushScopeId } from "vue"
    export default{
        components:{
            Comment,CommentInput,VuEnjoyerHeader,VueFooter,About
        },
        data(){
            return{
                comments:[
                    // {id:0,comment_author:"Lorem ipsum",comment_content:"Lorem ipsum dolor sit amet consectetur adipisicing elit. Obcaecati, laudantium.",isReplyClicked:false,replylist:[{id:5,comment_author:"Vasya",comment_content:"Первый!",isReplyClicked:false,replylist:[],isLiked:false,like_counter:10}],isLiked:false,like_counter:10},
                    // {id:1,comment_author:"Aperiam perspiciatis",comment_content:"Possimus enim cupiditate ab omnis reiciendis, incidunt obcaecati ducimus officiis culpa aperiam illum rem eum ea earum sint quis nisi laborum et mollitia? Iste nostrum accusamus asperiores sequi, quae id!",isReplyClicked:false,replylist:[],isLiked:true,like_counter:50},
                    // {id:2,comment_author:"Exercitationem explicabo",comment_content:"Dolor sit amet consectetur adipisicing elit.",isReplyClicked:false,replylist:[],isLiked:false,like_counter:8},
                    // {id:3,comment_author:"Cumque Ullam",comment_content:"amet quia assumenda officia molestiae sed, rerum hic iure. Nulla ad amet, inventore vero voluptatem a.",isReplyClicked:false,replylist:[],isLiked:false,like_counter:5}
                
                ]
            }
        },
        methods:{
            sendComment(comment,comment_list){
                if(!comment.replylist){
                    comment.replylist=[];
                }
                this.comments.push(comment);
               // comment_list.push(comment);
            },
            async fetchComments(){
                try{
                    const response = await axios.get("https://jsonplaceholder.typicode.com/comments?_limit=10");
                    this.comments = response.data;
                }
                catch(e){
                    console.log("ошибка при загрузке комментариев");
                }
            },
            closeReplyDialogs(com,com_list){
                
                com_list.forEach(comment => {
                    if(comment!=com){
                        comment.isReplyClicked = false;
                    }
                    else{
                        // console.log(com.isReplyClicked);
                        // if(!com.isReplyClicked){com.isReplyClicked=true; console.log(1);}
                        // else{com.isReplyClicked = false;console.log(2);
                        // console.log(com.isReplyClicked);}
                        // //comment.isReplyClicked = !comment.isReplyClicked?true:false;
                    }
                    if(comment.replylist!=[]&&!comment.replylist){this.closeReplyDialogs(com,com_list.replylist);
                    }
                });
            }
            // inputContent(event){
            //     console.log(event);
            //     this.Content = event.target.value;
            // }
        },
        mounted(){
            this.fetchComments();
        }
    }
    </script>
    
    <style>
    *{
        border:border-box;
        margin: 0;
        padding: 0;
    }
    .comment_box{
        padding: 0 100px 0 100px;
    }
    body{
        padding-top: 100px;
        background-color: #8DDCB8;
    }
    </style>