<template>
    <section>
        <div v-if="downloads">
            <h1 class="text-left pt-4">
                DOWNLOAD
            </h1>
            <div class="row text-center">
                <div v-for="n in downloads" :key="n.slug" class="col-4 mb-6">
                    <nuxt-link :to="`/downloads_doc/${n.topics_id}`">
                        <v-img
                            v-if="n.download_icon"
                            :src="n.download_icon.url"
                            width="200"
                            height="200"
                            class="img-responsive mx-auto d-block mb-3"
                        />
                        </v-img>
                        {{ n.subject }}
                    </nuxt-link>
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
        downloads: {
            type: Array,
            required: false,
            default: () => []
        }
    }
};
</script>
