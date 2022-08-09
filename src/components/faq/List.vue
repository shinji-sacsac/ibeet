<template>
    <div>
        <div v-if="faq">
            <h1 class="text-left pt-4">
                FAQ
            </h1>
            <div v-for="n in faq" :key="n.slug">
                <nuxt-link :to="`/faq/${n.topics_id}`">
                    {{ n.subject }}
                </nuxt-link>
            </div>
        </div>
        <div v-else>
            <div class="text-center py-4 grey--text col">
                No data available
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        faq: {
            type: Array,
            required: false,
            default: () => []
        }
    }
};
</script>
