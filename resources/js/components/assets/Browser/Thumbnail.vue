<template>

    <div class="">
        <img v-if="asset.is_image"
            :src="asset.thumbnail"
            class="asset-thumbnail rounded max-h-full max-w-full mx-auto rounded"
            loading="lazy"
            :class="{'w-8 h-8 fit-cover': square}"
            />
        <img v-else-if="asset.is_svg"
            :src="asset.url"
            class="asset-thumbnail rounded h-8 max-h-full max-w-full mx-auto rounded"
            loading="lazy"
            />
        <file-icon v-else :extension="asset.extension" class="p-px asset-thumbnail rounded w-full h-full" />
    </div>

</template>

<script>
export default {

    props: {
        'asset': Object,
        'square': {
            default: false,
            type: Boolean
        }
    },

    computed: {

        showSvg() {
            return this.asset.extension === 'svg';
        }

    }

}
</script>
