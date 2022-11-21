<template>
    <div>
        <li v-for="post in posts" :key="post.id">{{post.title}}</li>
    </div>
</template>

<script>
export default {
    props:["posts"]
}
</script>