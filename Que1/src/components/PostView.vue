<script>
import axios from 'axios';
export default {
    name: "Posts",
    data() {
        return {
            title: "",
            body: "",
            isSuccess: false,
        };
    },
    methods: {
        PostCreate() {
            axios.post(
                'https://jsonplaceholder.typicode.com/posts',
                { title: this.title, body: this.body },
            ).then((response) => {
                this.isSuccess = true;
                console.log(response);
            });
        },
    },
}
</script>

<template>
    <div>
        <h2>
            Create post
        </h2>
        <hr>
        <div class="alert alert-success" v-if="isSuccess">
            <h2>
                Post Created Successfully
            </h2>
        </div>
        <form @submit.prevent="PostCreate">
            <div class="form-group">
                <label>
                    Title
                </label>
                <input type="text" class="form-control" v-model="title" />
            </div>
            <div class="form-group">
                <label>
                    body
                </label>
                <input type="text" class="form-control" v-model="body" />
            </div>
            <div class="mt-3">
                <button type="submit" class="btn btn-primary" @click="PostCreate">
                    Create Post
                </button>
            </div>
        </form>

    </div>
</template>
<style scoped>
h2 {
    color: green;
}
</style>