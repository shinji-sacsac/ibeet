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
    async asyncData({ $axios, params }) {
        return {
            response: await $axios.$get(
                `/rcms-api/3/downloads_doc_detail/${params.slug}`
            )
        };
    }
};
</script>
