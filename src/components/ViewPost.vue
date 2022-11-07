<script>
import axios from "axios";

export default {
    name: "Posts",
    data() {
        return {
            postDetails: []
        };
    },

    mounted() {
        axios.get(
            'https://jsonplaceholder.typicode.com/posts',
            { title: this.title, body: this.body },
        ).then((response) => {
            console.log(response.data);
        });
    },
    methods: {
        ViewPosts(postDetails) {
            for (let key in postDetails) {
                this.postDetails.push({ ...postDetails[key], id: key })
            }
        }
    }
}
</script>

<template>
    <div>
        <h3>
            Details
<hr><hr>
        
        </h3>
        <form @submit.prevent="ViewPosts(postDetails)">
            <button type="submit" class="btn btn-primary" v-for="post in postDetails">
                Show
            </button>
        </form>
    </div>
</template>