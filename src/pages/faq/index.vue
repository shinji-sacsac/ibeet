<template>
    <div>
        <h1 class="text-left pt-4">
            FAQ
        </h1>
        <div v-for="n in response.list" :key="n.slug">
            <nuxt-link :to="`/faq/${n.topics_id}`">
                {{ n.ymd }} {{ n.subject }}
            </nuxt-link>
        </div>
    </div>
</template>

<script>
export default {
    async asyncData({ $axios }) {
        return {
            response: await $axios.$get('/rcms-api/4/faq')
        };
    }
};
</script>
