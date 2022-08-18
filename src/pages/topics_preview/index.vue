<template>
    <div>
        <v-col>
            <v-card class="d-flex justify-space-between mb-6" flat tile>
                <v-card flat>
                    <v-row>
                        <v-col class="pt-0">
                            <h1 class="mb-3 mt-0">
                                {{ response.details.subject }}
                            </h1>
                        </v-col>
                    </v-row>
                </v-card>
                <v-card flat>
                    {{ $dateFns.format(response.details.ymd, 'yyyy/MM/dd') }}
                </v-card>
            </v-card>
            <v-row class="p-article_content">
                <v-container fluid>
                    <v-card class="mx-auto" max-width="7000">
                        <div class="text--primary px-5 py-5" v-html="response.details.contents" />
                        </v-card-text>
                    </v-card>
                </v-container>
            </v-row>
        </v-col>
    </div>
</template>

<script>
export default {
    async asyncData({ $axios, route }) {
        return {
            response: await $axios.$get('/rcms-api/1/content/preview', {
                params: {
                    preview_token: route.query.preview_token
                }
            })
        };
    }
};
</script>
