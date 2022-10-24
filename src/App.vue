<template>
    <form @submit.prevent>
        <h4> Создание поста</h4>
         <input 
         v-bind:value="title"
          @input="title = $event.target.value"
           class="input" 
           type="text" 
           placeholder="название">
         <input 
         v-bind:value="body"
          class="input"
           type="text"
            placeholder="описание"
            @input="body = $event.target.value">
         <button @click="createPosts" class="btn">Создать</button>
     </form>
 <div>
<div class="post" 
v-for="post in posts"
v-bind:key="post.id"
>
    <div><strong>{{post.title}}</strong></div>
    <div><strong>{{post.body}}</strong></div>
</div>



 </div>
</template>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
.post {
    padding: 15px;
    border: 2px solid teal;
    margin-top: 15px;
}

.app {
    padding: 20px;
}

.input {
    width: 100%;
    border: 1px solid teal;
    padding: 10px 15px;
    margin-top: 10px;
}
form {
    display: flex;
    flex-direction: column;
}

.btn {
    align-self: flex-start;
    padding: 10px 15px;
    background: none;
    color: teal;
    border: 1px solid teal;
    margin-top: 10px;
}

</style>

<script>
export default {
    data() {
        return {
            posts: [
                {id: 1,title: 'JavaScript 1', body: 'Описание поста 1'},
                {id: 2,title: 'JavaScript 2', body: 'Описание поста 2'},
                {id: 3,title: 'JavaScript 3', body: 'Описание поста 3'}
            ],
            title: '',
            body: ''
        }
    },

    methods: {
        createPosts() {
            const newPosts = {
                id: Date.now(),
                title: this.title,
                body: this.body
            }
            this.posts.push(newPosts)
            this.title = '',
            this.body = ''
        },
       
    }
    

    
}
</script>