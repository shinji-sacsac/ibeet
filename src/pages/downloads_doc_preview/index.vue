<template>
    <div>
        <h1 class="title c-text_bold">
            {{ response.details.subject }}
        </h1>
        <div class="post">
            <p
                v-for="(item, idx) in response.details.download_file"
                :key="idx"
                class="downloadslist"
            >
                <a :href="item.url" target="_blank">{{ item.desc }}</a>
            </p>
        </div>
    </div>
</template>

<script>
export default {
    async asyncData({ $axios, route }) {
        return {
            response: await $axios.$get('/rcms-api/3/downloads_doc_detail/preview', {
                params: {
                    preview_token: route.query.preview_token
                }
            })
        };
    }
};
</script>
