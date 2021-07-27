<template>
    <article>
        <header-info v-bind="header_info" />

        <!--基础渲染-->
        <section>
            <h5>基础渲染</h5>
            <p>组件初始化数据机制及数据结构继承自 content-wid 组件，默认为横向展示；通过数据字段 <code>spread</code> 可以默认展开子级；<code>spread_fixed</code> 可以强制展开子级，禁止收起；<code>selected</code> 可以设置默认选中。</p>
            <div class="resize pad-1 round-sm over-scroll">
                <dir-wid v-bind="data_1.props" @on_select="$_select_1" />
            </div>
            <p>当前选择数据：
                <code v-if="data_1.selected">{{data_1.selected}}</code>
                <span v-else class="alpha-d4">暂无</span>
            </p>
            <hr>
            <p></p>
        </section>

        <!--自定义样式-->
        <section>
            <h5>自定义样式</h5>
            <p>通过 <code>min-width</code> 属性可以设置元素项的宽度。数据字段 <code>text</code> 支持富文本以实现自定义样式扩展；通过 <code>colors</code> 属性可以定义组件项目色彩方案。</p>
            <div class="resize pad-1 bg-color-dgray round-sm">
                <dir-wid v-bind="data_2.props" />
            </div>
            <hr>
            <p></p>
        </section>

        <!--纵向展示-->
        <section>
            <h5>纵向展示</h5>
            <p>通过 <code>vertical</code> 属性可以设置目录的纵向展示，此外通过 <code>headIcon</code> 数据字段可以设置项目图标，设置后其文本对齐方式自动变为居左。</p>
            <div class="resize bg-color-lgray round-sm grid">
                <div class="col-6 pad-1">
                    <dir-wid v-bind="data_3.props" />
                </div>
                <div class="col-6 pad-1 line-l line-neutral thick-1">
                    <dir-wid v-bind="data_3_2.props" />
                </div>
            </div>
            <hr>
            <p></p>
        </section>

        <!--提示浮框-->
        <section>
            <h5>提示浮框</h5>
            <p>数据字段 <code>tooltip</code> 支持富文本以实现悬停提示文本；通过 <code>tooltipData</code> 属性可以设置提示框色彩风格及定位。</p>
            <div class="resize pad-1 round-sm">
                <dir-wid v-bind="data_4.props" />
            </div>
        </section>
    </article>
</template>

<script>
    import HeaderInfo from "@/components/header-info"
    import DirWid from "@/components/BTXUI/dir/dir-wid"

    export default {
        name: "content_wid_demo",
        components: {
            HeaderInfo,
            DirWid
        },
        data(){
            return {

                //初始化入参
                header_info: {
                    name: DirWid.name,
                    ...DirWid.introduce,
                },

                data_1: {
                    props: {
                        dataTree: [
                            {
                                id: "html_1",
                                text: "html",
                                children: [
                                    {
                                        id: "div_1_1",
                                        text: "div 标签"
                                    }
                                ]
                            },
                            {
                                id: "css_2",
                                text: "css",
                                spread: true,
                                children: [
                                    {
                                        id: "color_2_1",
                                        text: "color 文字颜色",
                                        spread: true,
                                        spread_fixed: true,
                                        children: [
                                            {
                                                id: "color_2_1_1",
                                                text: "rgba 色彩模式",
                                            }
                                        ]
                                    },
                                    {
                                        id: "background_2_2",
                                        text: "background 背景样式",
                                    },
                                ]
                            },
                            {
                                id: "javascript_3",
                                text: "javascript",
                                selected: true
                            }
                        ]
                    },
                    selected: "javascript_3"
                },

                data_2: {
                    props: {
                        dataTree: [
                            {
                                id: "html_1",
                                text: "<b style='font-size: 17px'>html</b>",
                                children: [
                                    {
                                        id: "div_1_1",
                                        text: "div 标签",
                                    },
                                    {
                                        id: "span_1_2",
                                        text: "span 标签",
                                    },
                                    {
                                        id: "a_1_3",
                                        text: "a 标签",
                                    },
                                ]
                            },
                            {
                                id: "css_2",
                                text: "<b style='color: orange'>css</b>",
                                spread: true,
                                children: [
                                    {
                                        id: "color_2_1",
                                        text: "color 文字颜色",
                                        children: [
                                            {
                                                id: "color_3_1",
                                                text: "red 玫红",
                                            },
                                            {
                                                id: "color_3_2",
                                                text: "yellow 橙黄",
                                            },
                                        ]
                                    },
                                    {
                                        id: "background_2_2",
                                        text: "<b style='color: #02b9a1'>background</b> 背景样式",
                                    },
                                ]
                            }
                        ],
                        colors: {
                            normal: {
                                text: "mgray",
                                bg: "dgray",
                                line: "dark"
                            },
                            act: {
                                text: "blue",
                                bg: "dark",
                                line: "dark"
                            },
                            hover: {
                                text: "mgray",
                                bg: "dgray",
                                line: "dark"
                            }
                        },
                        minWidth: 10
                    },
                    selected: ""
                },

                data_3: {
                    props: {
                        dataTree: [
                            {
                                id: "html_1",
                                text: "html",
                                children: [
                                    {
                                        id: "div_1_1",
                                        text: "div 标签"
                                    },
                                    {
                                        id: "span_1_2",
                                        text: "span 标签"
                                    },
                                    {
                                        id: "a_1_3",
                                        text: "a 标签"
                                    },
                                ]
                            },
                            {
                                id: "css_2",
                                text: "css",
                                children: [
                                    {
                                        id: "color_2_1",
                                        text: "color 文字颜色",
                                        children: [
                                            {
                                                id: "color_3_1",
                                                text: "red 玫红"
                                            },
                                            {
                                                id: "color_3_2",
                                                text: "yellow 橙黄"
                                            },
                                        ]
                                    },
                                    {
                                        id: "background_2_2",
                                        text: "background 背景样式"
                                    },
                                ]
                            },
                            {
                                id: "javascript_3",
                                text: "javascript"
                            },
                        ],
                        portrait: true,
                        colors: {
                            normal: {
                                text: "dgray",
                                bg: "light",
                            },
                            act: {
                                text: "light",
                                bg: "blue",
                            },
                            hover: {
                                text: "dark",
                                bg: "light",
                            }
                        },
                    }
                },
                data_3_2: {
                    props: {
                        dataTree: [
                            {
                                id: "html_1",
                                text: "html",
                                headIcon: {
                                    bgImg: require("@/assets/img/dir.png")
                                },
                                children: [
                                    {
                                        id: "div_1_1",
                                        text: "div 标签",
                                        headIcon: {
                                            icon: "book"
                                        }
                                    },
                                    {
                                        id: "span_1_2",
                                        text: "span 标签",
                                        headIcon: {
                                            icon: "book"
                                        }
                                    },
                                    {
                                        id: "a_1_3",
                                        text: "a 标签",
                                        headIcon: {
                                            icon: "book"
                                        }
                                    },
                                ]
                            },
                            {
                                id: "css_2",
                                text: "css",
                                headIcon: {
                                    bgImg: require("@/assets/img/dir.png")
                                },
                                children: [
                                    {
                                        id: "color_2_1",
                                        text: "color 文字颜色",
                                        children: [
                                            {
                                                id: "color_3_1",
                                                text: "red 玫红",
                                                headIcon: {
                                                    icon: "book"
                                                }
                                            },
                                            {
                                                id: "color_3_2",
                                                text: "yellow 橙黄",
                                                headIcon: {
                                                    icon: "book"
                                                }
                                            },
                                        ]
                                    },
                                    {
                                        id: "background_2_2",
                                        text: "background 背景样式"
                                    },
                                ]
                            },
                            {
                                id: "javascript_3",
                                text: "javascript",
                                headIcon: {
                                    icon: "book"
                                }
                            },
                        ],
                        portrait: true,
                        colors: {
                            normal: {
                                text: "dgray",
                                bg: "lgray",
                                line: "mgray"
                            },
                            act: {
                                text: "blue",
                                bg: "light",
                                line: "blue"
                            },
                            hover: {
                                text: "dark",
                                bg: "lgray",
                                line: "mgray"
                            }
                        },
                        minWidth: "auto"
                    }
                },

                data_4: {
                    props: {
                        dataTree: [
                            {
                                id: "css_2",
                                text: "css",
                                spread: true,
                                tooltip: "<span class='color-red bold'>展示相关 css 样式值</span>",
                                children: [
                                    {
                                        id: "color_2_1",
                                        text: "color 文字颜色",
                                        spread: true,
                                        children: [
                                            {
                                                id: "color_3_1",
                                                text: "red 玫红",
                                                tooltip: "【色值】：#ec4334;"
                                            },
                                            {
                                                id: "color_3_2",
                                                text: "yellow 橙黄"
                                            },
                                        ]
                                    },
                                    {
                                        id: "background_2_2",
                                        text: "background 背景样式",
                                        tooltip: "<span class='color-blue bold'>【exp】</span>：background: red;"
                                    },
                                ]
                            }
                        ],
                        tooltipData: {
                            colors: {
                                text: "#ddd",
                                bg: "dgray",
                                line: "dark",
                                point: "blue"
                            },
                            offset: {
                                x: -40,
                                y: -70
                            }
                        }
                    }
                },

            }
        },
        methods: {

            $_select_1(id){
                this.data_1.selected = id;
            },

        }
    }
</script>