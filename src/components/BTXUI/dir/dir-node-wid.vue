<template>
    <b-view :styles="`rel ${portrait? 'flex-column': 'flex'}`">
        <template v-for="(item, i) of treeData">
            <!--子级-->
            <b-view :key="i" v-if="item.sub_data" styles="mrg-b-2px">
                <dir-drawer-wid :ref="`drawer_${item.index_data.tag_data.id}`"
                                :tag-data="item.index_data.tag_data"
                                :spread="item.spread"
                                :min-width="minWidth"
                                :class="$_set_drawer_class(i)"
                                @on_title_enter="item.tooltip && $_show_tooltip(item.tooltip, $event)"
                                @on_title_move="item.tooltip && $_move_tooltip($event)"
                                @on_title_leave="item.tooltip && $_hide_tooltip()"
                                @on_toggle="$_content_toggle">
                    <b-view v-if="item.sub_data" styles="pad-l-2"
                            :class="`dir-node-sub-${portrait? 'v': 'h'}`">
                        <dir-node-wid :tree-data="item.sub_data"
                                      :content-id="item.index_data.tag_data.id"
                                      :min-width="minWidth"
                                      :portrait="portrait"
                                      @on_tooltip_show="$_show_tooltip"
                                      @on_tooltip_move="$_move_tooltip"
                                      @on_tooltip_hide="$_hide_tooltip"
                                      @on_select="$_item_select"
                                      @on_toggle="$_drawer_resize" />
                    </b-view>
                </dir-drawer-wid>
            </b-view>

            <!--选项-->
            <b-view v-else :key="i">
                <!--单选-->
                <dir-tag-wid v-bind="item.index_data.tag_data"
                             v-model="item.index_data.selected"
                             @on_click="$_item_select"
                             @on_enter="item.tooltip && $_show_tooltip(item.tooltip, $event)"
                             @on_move="item.tooltip && $_move_tooltip($event)"
                             @on_leave="item.tooltip && $_hide_tooltip()" />
            </b-view>
        </template>
    </b-view>
</template>

<script>
    import ContentNodeWid from "@/components/BTXUI/content/content-node-wid"
    import DirDrawerWid from "./dir-drawer-wid"
    import DirNodeWid from "./dir-node-wid"
    import DirTagWid from "./dir-tag-wid"

    export default {
        extends: ContentNodeWid,
        name: "dir-node-wid",
        components: {
            DirDrawerWid,
            DirNodeWid,
            DirTagWid
        },
        props: {
            minWidth: {
                type: [Number, String],
                required: false
            },
            portrait: {
                required: false,
                type: Boolean
            },
        },
        methods: {

            //编辑节点
            $_edit(){
                console.log(123)
            },

            //设置 dir-drawer 类样式
            $_set_drawer_class(i){
                return i === this.treeData.length - 1? "": `dir-drawer-${this.portrait? 'v': 'h'}`
            },

            //新增同级节点
            $_append(){
                console.log("1");
            },

            //新增子级节点
            $_insert(){
                console.log("2");
            },

        }
    }
</script>

<style scoped>
    .dir-drawer-h::before {
        content: "";
        box-sizing: border-box;
        position: absolute;
        width: 100%;
        height: 1px;
        left: 1rem;
        top: 2.2rem;
        background-color: rgba(110,110,110,.4);
    }
    .dir-drawer-v::before {
        content: "";
        box-sizing: border-box;
        position: absolute;
        width: 1px;
        height: 100%;
        left: .7rem;
        top: 1rem;
        background-color: rgba(110,110,110,.4);
    }
    .dir-node-sub-h::before {
        content: "";
        position: absolute;
        width: 1.2rem;
        height: 2.2rem;
        border-radius: 0 0 0 7px;
        left: .7rem;
        top: 1.8px;
        border: 1px solid rgba(110,110,110,.4);
        border-top: none;
        border-right: none;
    }
    .dir-node-sub-v::before {
        content: "";
        position: absolute;
        width: 1rem;
        height: 2.2rem;
        border-radius: 0 0 0 7px;
        left: 1rem;
        top: 1.8px;
        border: 1px solid rgba(110,110,110,.4);
        border-top: none;
        border-right: none;
    }
</style>