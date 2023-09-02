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
            <div class="like white_like"></div>
            <div class="like green_like"></div>
            </div>
        </div>
       
    </div>
</template>

<script>

</script>

<style>
.comment{
    border:#9d9 5px solid;
    margin: 15px;
    padding: 10px;
    min-width:300px;
    width: max-content;
    max-width: 600px;
    display: flex;
    flex-direction: column;
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
}
.comment_content{
    font-size: 20px;
}
.like{
    width: 35px;
    height: 35px;
    position: absolute;
    right: 0;
    bottom: 0;
}
.white_like{
    background-image: url(../../мусорка/white_like.png);
    background-size: cover;
}
.green_like{
    background-image: url(../../мусорка/green_like.png);
    background-size: cover;
}
.reply{
    font-size: 24px;
    position: relative;
    display: flex;
    flex-direction: column-reverse;
}
.reply::after{
    content: "";
    position: absolute;
    background-image: url(../../мусорка/reply.png);
    background-size: 35px 35px;
    height: 35px;
    width: 35px;
    right: -40px;
    bottom: 0px;
}
.rating{
    margin-left: 50px;
    position: relative;
}
</style>