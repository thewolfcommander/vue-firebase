<template>
    <div class="blog">
        <div class="multi">
            <div class="blog-post" v-for="post in posts" :key="post.id">
                <h2 class="blog-title">{{ post.title }}</h2>
                <button @click="viewPost(post.id)">View</button>
            </div>
        </div>
        <div class="single">
            <div class="single-blog-post">
                <h2 class="single-blog-title">{{ post.title }}</h2>
                <p class="single-blog-desc">{{ post.body }}</p>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    name: 'Blogs',
    data() {
        return {
            posts: [],
            post: {
                title: 'Hello'
            }
        }
    },
    methods: {
        viewPost(id) {
            axios.get(`https://jsonplaceholder.typicode.com/posts/${id}/`).then(response => {
                this.post = response.data
                console.log(this.post)
            }).catch(err => {
                console.log(err)
            })
        }
    },
    created() {
        axios.get('https://jsonplaceholder.typicode.com/posts/').then(response => {
            this.posts = response.data
        }).catch(err => {
            console.log(err)
        })
    }
}
</script>

<style>
.blog {
    margin-top: 20px;
    display: flex;
}

.multi,
.single {
    flex: 1;
}

.single {
    position: fixed;
    top: 150px;
    right: 40px;
}

.blog-post {
    padding: 20px;
    width: 400px;
    height: 200px;
    box-shadow: 0 2px 4px rgba(0,0,0,0.15);
    background: #d4d9d1;
    margin: 25px;
    border: 1px solid rgba(0,0,0,0.15)
}

.blog-title {
    font-size: 22px;
    color: teal;
    margin-bottom: 20px;
}

.blog-desc {
    font-size: 14px;
    color: midnightblue;
}

.single-blog-post {
    padding: 20px;
    width: 400px;
    height: 400px;
    box-shadow: 0 2px 4px rgba(0,0,0,0.15);
    background: #fff;
    margin: 25px;
}

.single-blog-title {
    font-size: 22px;
    color: orangered;
    margin-bottom: 20px;
}

.single-blog-desc {
    font-size: 14px;
    color: midnightblue;
}
</style>