<template>
    <div class="app">
       <vu-enjoyer-header/>
       <div class="content">
        <about/>
        <comment-input v-bind:replylist="comments" v-on:send="sendComment"/>
         
        <comment v-bind:comments="comments"/>
        </div>
        <vue-footer/>
    </div>
</template>
    
    <script>
    import About from "@/components/About.vue"
    import Comment from "@/components/Comment.vue"
    import CommentInput from "@/components/CommentInput.vue"
    import VuEnjoyerHeader from "@/components/VuEnjoyerHeader.vue"
    import VueFooter from "./components/VueFooter.vue"
// import { pushScopeId } from "vue"
    export default{
        components:{
            Comment,CommentInput,VuEnjoyerHeader,VueFooter,About
        },
        data(){
            return{
                comments:[
                    {id:0,comment_author:"Lorem ipsum",comment_content:"Lorem ipsum dolor sit amet consectetur adipisicing elit. Obcaecati, laudantium.",isReplyClicked:false,replylist:[{id:5,comment_author:"Vasya",comment_content:"Первый!",isReplyClicked:false,replylist:[],isLiked:false,like_counter:10}],isLiked:false,like_counter:10},
                    {id:1,comment_author:"Aperiam perspiciatis",comment_content:"Possimus enim cupiditate ab omnis reiciendis, incidunt obcaecati ducimus officiis culpa aperiam illum rem eum ea earum sint quis nisi laborum et mollitia? Iste nostrum accusamus asperiores sequi, quae id!",isReplyClicked:false,isLiked:true,like_counter:50},
                    {id:2,comment_author:"Exercitationem explicabo",comment_content:"Dolor sit amet consectetur adipisicing elit.",isReplyClicked:false,isLiked:false,like_counter:8},
                    {id:3,comment_author:"Cumque Ullam",comment_content:"amet quia assumenda officia molestiae sed, rerum hic iure. Nulla ad amet, inventore vero voluptatem a.",isReplyClicked:false,isLiked:false,like_counter:5}
                
                ]
            }
        },
        methods:{
            sendComment(comment,comment_list){
                
                comment_list.push(comment);
            }
            // inputContent(event){
            //     console.log(event);
            //     this.Content = event.target.value;
            // }
        }
    }
    </script>
    
    <style>
    *{
        border:border-box;
        margin: 0;
        padding: 0;
    }
    .content{
        padding: 100px 100px 0 100px;
    }

    </style>