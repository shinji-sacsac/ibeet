<template>
    <div>
        <h1 class="title">
            {{ response.details.subject }}
        </h1>
        <div class="post" v-html="response.details.contents" />
    </div>
</template>

<script>
export default {
    async asyncData({ $axios, params }) {
        return {
            response: await $axios.$get(`/rcms-api/3/downloaddetail/${params.slug}`)
        };
    }
};
</script>
