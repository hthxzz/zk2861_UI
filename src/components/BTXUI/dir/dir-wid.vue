<template>
    <b-view styles="rel flex">
        <!--提示框组件-->
        <tooltip-wid ref="tooltip" v-bind="tooltipData" />

        <!--目录结构组件-->
        <dir-node-wid :tree-data="tree_data"
                      :min-width="minWidth"
                      :portrait="portrait"
                      @on_select="$_select"
                      @on_tooltip_show="$_show_tooltip"
                      @on_tooltip_move="$_move_tooltip"
                      @on_tooltip_hide="$_hide_tooltip" />
    </b-view>
</template>

<script>
    import ContentWid from "@/components/BTXUI/content/content-wid"
    import DirNodeWid from "./dir-node-wid"

    const desc = ["该组件用于实现文件目录结构操作，支持纵向及横向展示。"],
        extend = ["content-wid"],
        dependent = [],
        api = null,
        init_data = `{
        (参照：content-wid 组件入参。mode 属性无效；dataTree 属性的 checkbox 字段无效，新增 headIcon 字段),
        @dataTree: [
            {
                ...,
                headIcon: "项目图标"
            }...
        ],
        /* portrait: "纵向展示，默认横向" */,
        /* minWidth: "项目宽度，默认为：14rem" */,
    }`;

    export default {
        extends: ContentWid,
        name: "dir-wid",
        introduce: { desc, extend, dependent, api, init_data },
        components: {
            DirNodeWid
        },
        props: {
            minWidth: {
                type: [Number, String],
                required: false,
                default: 14,
            },
            colors: {
                required: false,
                type: Object,
                default: ()=>{
                    return {
                        normal: {
                            text: "dgray",
                            bg: "lgray",
                            line: "none",
                        },
                        act: {
                            text: "blue",
                            bg: "lgray",
                            line: "neutral",
                        },
                        hover: {
                            text: "dgray",
                            bg: "lgray",
                            line: "none",
                        }
                    }
                }
            },
            portrait: {
                required: false,
                type: Boolean
            },
        }
    }
</script>