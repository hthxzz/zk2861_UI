<template>
    <b-view styles="rel flex-1 flex-column">
        <!--标题-->
        <dir-title-tag-wid v-bind="tagData"
                           :icon-data="iconData"
                           :arrow-fixed="arrowFixed"
                           :checkbox="checkbox"
                           :min-width="minWidth"
                           v-model="tag_spread"
                           @on_move="$emit('on_title_move', $event)"
                           @on_enter="$emit('on_title_enter', $event)"
                           @on_leave="$emit('on_title_leave', $event)" />

        <!--内容-->
        <b-view styles="rel no-scroll trans-fast t-f2px alpha-0" ref="cont"
                @on_transitionend="$_set_state"
                :dynamic="`h-${cont_height} ${cont_show}`"
                :states="{
                    spread: {
                        style: 'alpha-1',
                        state: tag_spread
                    }
                }">
            <slot />
        </b-view>
    </b-view>
</template>

<script>
    import DrawerWid from "@/components/BTXUI/drawer/drawer-wid"
    import DirTitleTagWid from "./dir-title-tag-wid"

    export default {
        extends: DrawerWid,
        name: "dir-drawer-wid",
        components: {
            DirTitleTagWid
        },
        props: {
            minWidth: {
                type: [Number, String],
                required: false
            }
        },
    }
</script>