<template>
    <div id="app">
        <h1>{{postsCount}}</h1>
        <PostForm/>
        <div class="post" v-for="post in validPosts" :key="post.id">
            <h2>{{post.title}}</h2>
            <p>{{post.body}}</p>
        </div>
    </div>
</template>

<script>
    import {mapGetters, mapActions} from 'vuex';
    import PostForm from './components/PostForm';

    export default {
        name: 'App',
        computed: mapGetters(['allPosts', 'postsCount', 'validPosts']),
        methods: mapActions(['fetchPosts']),
        components: {PostForm},
        async mounted() {
            this.fetchPosts();
        }
    }
</script>

<style>
    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }

    .post {
        border: 1px solid black;
        margin-top: 20px;
    }
</style>
