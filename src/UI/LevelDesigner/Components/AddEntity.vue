<template>
    <Box>
        <div class="columns is-mobile">
            <div class="column">
                <h1 class="title is-4">Add Entity</h1>
            </div>
            <div class="pointer column is-narrow">
                <div
                    class="icon is-medium has-tooltip-arrow hover-highlight"
                    @click="goTo('/scene')"
                >
                    <font-awesome-icon icon="arrow-left" size="lg" />
                </div>
            </div>
        </div>
        <div class="list">
            <div v-for="entityData in entities" :key="entityData.name" class="box">
                <div class="level">
                    <div class="level-left">
                        <div class="level-item">
                            {{ entityData.name }}
                        </div>
                    </div>
                    <div class="level-right">
                        <div class="level-item">
                            <div class="button is-info" @click="addEntity(entityData)">
                                Add Entity
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </Box>
</template>

<script>
import Box from "./Common/BoxContainer.vue";

import SceneManager from '../../../../lib/Trengine/src/SceneManager';

export default {
    methods: {
        addEntity(entityData) {
            const scene = this.$store.state.scene
            SceneManager.getEntityStore().addEntityToScene(entityData.name, scene)
        }
    },
    computed: {
        entities() {
            return SceneManager.getEntityStore().entities
        }
    },
    components: {
        Box,
    },
};
</script>

<style lang="scss" scoped>
</style>