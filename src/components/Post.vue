<template>
    <div>
        <div v-if="post!=null">
            <h1>{{post.title}}</h1>
            <div>
                {{post.body}}
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        post: null
    }
}
</script>

<style>

</style>