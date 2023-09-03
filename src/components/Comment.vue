<template>
    <div class="comment">
        <div class="comment_author">
            <div class="user">
                <div class="avatar"></div>
                <div class="name">Lorem, ipsum.</div>
            </div>
        </div>
        <div class="comment_content">Lorem ipsum dolor sit amet consectetur adipisicing elit. Consectetur, modi.</div>
        <div class="comment_rating">
            <div class="reply">Ответить</div>
            <div class="rating">
                <div class="like_counter">{{like_counter}}</div>
                <div @click="LikeClicked" class="like_button">
                <div v-if="!isLiked" class="like white_like"></div>
                <div v-else class="like green_like"></div>
                </div>
            </div>
        </div>
       
    </div>
</template>

<script>
export default{
    data(){
        return{
            name:'comment',
            isLiked:false,
            like_counter:10
        }
    },
    methods:{
        LikeClicked(){
            if(this.isLiked===true){
                this.like_counter--;
                this.isLiked=false;
            }
            else{
                this.like_counter++;
                this.isLiked=true;
            }
        }
    }
}
</script>

<style>
*{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
.comment{
    border:#9d9 5px solid;
    margin: 15px;
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
</style>