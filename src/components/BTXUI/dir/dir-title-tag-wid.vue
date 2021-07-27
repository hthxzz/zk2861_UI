<template>
    <b-hot @on_click="$_click"
           @on_move="$emit('on_move', $event)"
           @on_enter="$emit('on_enter', $event)"
           @on_leave="$emit('on_leave', $event)"
           :styles="`rel mrg-t-1 mrg-r-1 pad-v-.4 pad-l-.5 pad-r-1.7 round-sm line thick-1 line-${tag_colors.normal.line} color-${tag_colors.normal.text} bg-color-${tag_colors.normal.bg} w-${minWidth} flex-${headIcon? '4': '5'}`"
           :states="{
               act: {
                   style: `line thick-1 line-${tag_colors.act.line} bg-color-${tag_colors.act.bg} color-${tag_colors.act.text}`,
                   state: selected
               }
           }"
           :hover="`line thick-1 line-${tag_colors.hover.line} bg-color-${tag_colors.hover.bg} color-${tag_colors.hover.text}`">

        <!--项目图标-->
        <b-icon v-if="headIcon" styles="bg-size-contain bg-pos-5 mrg-r-.5 w-1.4 h-1.4 flex-5" v-bind="headIcon" />

        <b-text v-html="tag_text" />

        <!--下拉箭头-->
        <b-icon icon="arrow-right"
                styles="abs r-.4 trans-fast alpha-.6"
                :states="{
                    act: {
                        style: 'rotate-90',
                        state: selected
                    }
                }" />
    </b-hot>
</template>

<script>
    import BIcon from "@/components/BTXUI/core/b-icon"
    import TagWid from "@/components/BTXUI/tag/tag-wid"

    export default {
        extends: TagWid,
        name: "dir-title-tag-wid",
        components: {
            BIcon
        },
        props: {
            minWidth: {
                type: [Number, String],
                required: false
            },
            headIcon: {
                type: Object,
                required: false
            }
        }
    }
</script>