<template>
    <div class="app">
       <vu-enjoyer-header/>
       <div class="content">
        <comment-input/>
        <comment/>
        </div>
    </div>
</template>
    
    <script>
    import Comment from "@/components/Comment.vue"
    import CommentInput from "@/components/CommentInput.vue"
    import VuEnjoyerHeader from "@/components/VuEnjoyerHeader.vue"
    export default{
        components:{
            Comment,CommentInput,VuEnjoyerHeader
        },
        data(){
            return{
                // Content:"123"
            }
        },
        methods:{
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
        padding: 100px 0 0 0;
    }
    </style>