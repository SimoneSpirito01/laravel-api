<template>
    <main>
        <div class="container">
            <h1>Post list</h1>
            <ul>
                <li v-for="(post, i) in visiblePosts" :key="i">
                    {{ post.title }}
                </li>
            </ul>
        </div>
    </main>
</template>

<script>
export default {
    name: "Main",
    data() {
        return {
            visiblePosts: [],
        };
    },
    created() {
        axios
            .get("/api/posts")
            .then((response) => {
                this.visiblePosts = [...response.data];
            })
            .catch(function (error) {
                console.log(error);
            });
    },
};
</script>

<style lang="scss" scoped>

main {
    margin-top: 70px;

    .container {
        width: 80%;
        max-width: 1200px;
        margin: 0 auto;

        h1 {
            margin-bottom: 20px;
        }

        ul {
            padding-left: 20px;
            
            li {
                margin: 5px 0;
            }
        }
    }
}

</style>
