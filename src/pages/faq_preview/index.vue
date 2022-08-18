<template>
    <div>
        <h1 class="title c-text_bold">
            {{ response.details.subject }}
        </h1>
        <div class="post">
            <dl v-for="(item, idx) in response.details.faq_group_q" :key="idx" class="faqlist">
                <dt>{{ item }}</dt>
                <dd>{{ response.details.faq_group_a[idx] }}</dd>
            </dl>
        </div>
    </div>
</template>

<script>
export default {
    async asyncData({ $axios, route }) {
        return {
            response: await $axios.$get('/rcms-api/4/faq/preview', {
                params: {
                    preview_token: route.query.preview_token
                }
            })
        };
    }
};
</script>
