<template>
    <section>
        <div v-if="topics.length > 0" class="row">
            <div class="col">
                <div
                    v-for="item in topics"
                    :key="item.topics_id"
                    class="row c-table_row"
                >
                    <div class="col-sm-2 col-auto c-table_col">
                        {{ $dateFns.format(item.ymd, "yyyy/MM/dd") }}
                    </div>
                    <div class="col-sm col-12 c-table_col">
                        <NuxtLink
                            :to="
                                localePath({
                                    path: `/topics_detail/${item.topics_id}`,
                                })
                            "
                            no-prefetch
                        >
                            {{ item.subject }}
                        </NuxtLink>
                    </div>
                </div>
            </div>
        </div>
        <div v-else class="row">
            <div class="text-center py-4 grey--text col">
                No data available
            </div>
        </div>
    </section>
</template>

<script>
export default {
    props: {
        topics: {
            type: Array,
            required: false,
            default: () => []
        }
    }
};
</script>
