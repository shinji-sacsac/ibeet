<template>
    <div>
        <h1 class="title c-text_bold">
            {{ response.details.subject }}
        </h1>
        <div class="post" v-html="response.details.contents" />
        <!-- <div class="post">
            <dl v-for="n in response.details" :key="n.faq_group_q">
                <dt>{{ n.faq_group_q }}</dt>
                <dd>{{ n.faq_group_a }}</dd>
            </dl>
        </div> -->
    </div>
</template>

<script>
export default {
    async asyncData({ $axios, params }) {
        return {
            response: await $axios.$get(`/rcms-api/4/faqdetail/${params.slug}`)
        };
    }
};
</script>
