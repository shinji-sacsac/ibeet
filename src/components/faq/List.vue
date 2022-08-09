<template>
    <div>
        <div v-if="faq">
            <h1 class="text-left pt-4">
                FAQ
            </h1>
            <div class="row">
                <div class="col">
                    <div v-for="n in faq" :key="n.slug" class="row c-table_row">
                        <div class="col-sm col-14 c-table_col">
                            <nuxt-link :to="`/faq/${n.topics_id}`">
                                {{ n.subject }}
                            </nuxt-link>
                        </div>
                    </div>
                </div>
            </div>
            <!-- <div v-for="n in faq" :key="n.slug">
                <nuxt-link :to="`/faq/${n.topics_id}`">
                    {{ n.subject }}
                </nuxt-link>
            </div> -->
        </div>
        <div v-else class="row">
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
