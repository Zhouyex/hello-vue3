<template>
    <!-- vue3页面 -->
    
    <div>
        <h1 style="margin-bottom:50px"></h1>
        <p>1. 实时搜索：实现了 耶 </p>
        <p>2. 默认展开到第二层 但终止中组合不展开</p>
        <p>3. 终止中组合 颜色改变 </p>
        <el-button @click="getData">取值</el-button>
        <el-input v-model="filterText" placeholder="Filter keyword" />

        <el-scrollbar height="500px">
            <el-tree
                ref="treeRef"
                class="filter-tree"  
                :data="treeSyd" 
                :props="defaultProps"
                node-key="node_type" 
                :default-expanded-keys="defaultExpand"
                :filter-node-method="filterNode"
        ></el-tree>
        </el-scrollbar>
        
    
    </div>
</template>

<script lang='ts'>
import { defineComponent, onMounted, reactive, ref,watch } from 'vue'
import type Node from 'element-plus/es/components/tree/src/model/node'

import { ElTree } from 'element-plus'
export default defineComponent({
    name: 'App',
    setup() {
        let treeSyd:any = ref([]);
        const filterText = ref('');
        let defaultExpand = ref([]);
        const treeRef = ref<InstanceType<typeof ElTree>>()
        let syd = reactive(
        [
            {
                node_type_name:'运营中组合',
                node_type:'01',
                sub_nodes:[
                    {
                        node_type_name:'第一层',
                        node_type:'wwwwww',
                        sub_nodes:[
                            {
                                node_type_name:'第二层',
                                node_type:'04',
                                node_value:[
                                    {
                                        asset_name:'最后一层尚',code:'11'
                                    },
                                    {
                                        asset_name:'最后一层艳',code:'11123'
                                    },
                                    {
                                        asset_name:'最后一层东',code:'111234'
                                    },
                                ]

                            },
                            {
                                node_type_name:'第二层',
                                node_type:'02',
                                node_value:[
                                    {
                                        asset_name:'最后一层',code:'11aaa'
                                    },
                                    {
                                        asset_name:'最后一层',code:'11123sss'
                                    },
                                    {
                                        asset_name:'最后一层',code:'111234ddd'
                                    },
                                ]

                            },
                            {
                                node_type_name:'第二层',
                                node_type:'02',
                                node_value:[
                                    {
                                        asset_name:'最后一层',code:'11fff'
                                    },
                                    {
                                        asset_name:'最后一层',code:'11123ggg'
                                    },
                                    {
                                        asset_name:'最后一层',code:'111234hhh'
                                    },
                                ]

                            },
                        ]
                    },
                    {
                        node_type_name:'第一层',
                        node_type:'wwwwwwsdff',
                        sub_nodes:[
                            {
                                node_type_name:'第二层',
                                node_type:'04',
                                node_value:[
                                    {
                                        asset_name:'最后一层',code:'11'
                                    },
                                    {
                                        asset_name:'最后一层',code:'11123'
                                    },
                                    {
                                        asset_name:'最后一层',code:'111234'
                                    },
                                ]

                            },
                            {
                                node_type_name:'第二层',
                                node_type:'02',
                                node_value:[
                                    {
                                        asset_name:'最后一层',code:'11aaa'
                                    },
                                    {
                                        asset_name:'最后一层',code:'11123sss'
                                    },
                                    {
                                        asset_name:'最后一层',code:'111234ddd'
                                    },
                                ]

                            },
                            {
                                node_type_name:'第二层',
                                node_type:'02',
                                node_value:[
                                    {
                                        asset_name:'最后一层',code:'11fff'
                                    },
                                    {
                                        asset_name:'最后一层',code:'11123ggg'
                                    },
                                    {
                                        asset_name:'最后一层',code:'111234hhh'
                                    },
                                ]

                            },
                        ]
                    },
                    {
                        node_type_name:'第一层',
                        node_type:'wwwwwwasdf',
                        sub_nodes:[
                            {
                                node_type_name:'第二层',
                                node_type:'04',
                                node_value:[
                                    {
                                        asset_name:'最后一层',code:'11'
                                    },
                                    {
                                        asset_name:'最后一层',code:'11123'
                                    },
                                    {
                                        asset_name:'最后一层',code:'111234'
                                    },
                                ]

                            },
                            {
                                node_type_name:'第二层',
                                node_type:'02',
                                node_value:[
                                    {
                                        asset_name:'最后一层',code:'11aaa'
                                    },
                                    {
                                        asset_name:'最后一层',code:'11123sss'
                                    },
                                    {
                                        asset_name:'最后一层',code:'111234ddd'
                                    },
                                ]

                            },
                            {
                                node_type_name:'第二层',
                                node_type:'02',
                                node_value:[
                                    {
                                        asset_name:'最后一层',code:'11fff'
                                    },
                                    {
                                        asset_name:'最后一层',code:'11123ggg'
                                    },
                                    {
                                        asset_name:'最后一层',code:'111234hhh'
                                    },
                                ]

                            },
                        ]
                    },
                ]
            },
            {
                node_type_name:'终止中组合',
                node_type:'02',
                sub_nodes:[
                    {
                        node_type_name:'第一层',
                        node_type:'wwwwwww',
                        sub_nodes:[
                            {
                                node_type_name:'第二层',
                                node_type:'04',
                                node_value:[
                                    {

                                        asset_name:'最后一层',code:'11w'
                                    },
                                    {
                                        asset_name:'最后一层',code:'1112e3'
                                    },
                                    {
                                        asset_name:'最后一层',code:'11123w4'
                                    },
                                ]

                            },
                            {
                                node_type_name:'第二层',
                                node_type:'02',
                                node_value:[
                                    {
                                        asset_name:'最后一层',code:'11aaa'
                                    },
                                    {
                                        asset_name:'最后一层',code:'11123sss'
                                    },
                                    {
                                        asset_name:'最后一层',code:'111234ddd'
                                    },
                                ]

                            },
                            {
                                node_type_name:'第二层',
                                node_type:'02',
                                node_value:[
                                    {
                                        asset_name:'最后一层',code:'11fff'
                                    },
                                    {
                                        asset_name:'最后一层',code:'11123ggg'
                                    },
                                    {
                                        asset_name:'最后一层',code:'111234hhh'
                                    },
                                ]

                            },
                        ]
                    },
                    {
                        node_type_name:'第一层',
                        node_type:'wwww1ww',
                        sub_nodes:[
                            {
                                node_type_name:'第二层',
                                node_type:'04',
                                node_value:[
                                    {
                                        asset_name:'最后一层',code:'11'
                                    },
                                    {
                                        asset_name:'最后一层',code:'11123'
                                    },
                                    {
                                        asset_name:'最后一层',code:'111234'
                                    },
                                ]

                            },
                            {
                                node_type_name:'第二层',
                                node_type:'02',
                                node_value:[
                                    {
                                        asset_name:'最后一层',code:'11aaa'
                                    },
                                    {
                                        asset_name:'最后一层',code:'11123sss'
                                    },
                                    {
                                        asset_name:'最后一层',code:'111234ddd'
                                    },
                                ]

                            },
                            {
                                node_type_name:'第二层',
                                node_type:'02',
                                node_value:[
                                    {
                                        asset_name:'最后一层',code:'11fff'
                                    },
                                    {
                                        asset_name:'最后一层',code:'11123ggg'
                                    },
                                    {
                                        asset_name:'最后一层',code:'111234hhh'
                                    },
                                ]

                            },
                        ]
                    }
                    
                ]
            }
        ]
        )
        interface Tree {
            id: number
            label: string
            isPenultimate?: boolean
            children?: Tree[],
            nodeKey:number,
            node_type_name:string,
            defaultExpand:[]
        }
        
        const customNodeClass = (data: Tree, node: Node) => {
            if (data.isPenultimate) {
                return 'is-penultimate'
            }
            return null
        }
        const defaultProps = {
            children: 'sub_nodes',
            label: 'node_type_name',
            class: customNodeClass
        }

		const recurrence = (data:Array<object>) => {
			for(let i in data)
			{	
				let element:any = data[i];
				let element1:any = data[1];
				if(element.node_value){
                    element.node_value.forEach((item:any)=>{
                        // item.label = item.asset_name;
                        // item.name = item.asset_name;
                        item.node_type_name = item.asset_name
                    })
                    element.sub_nodes = element.node_value
                    
                    
				}else if(element.sub_nodes)
				{
                    //默认展开到第二层
                    element.nodeKey = 999
                    //添加颜色
                    element1.isPenultimate = true
					recurrence(element.sub_nodes)
				}
               
			}
		}
		
		const getData = () => {
			recurrence(syd);
            treeSyd.value = syd;
            console.log(treeSyd.value,'syd')

            defaultExpand.value.push(treeSyd.value[0].node_type);

            for(let i in treeSyd.value[0].sub_nodes)
            {   
                let ele = treeSyd.value[0].sub_nodes[i];
                defaultExpand.value.push(ele.node_type);
            }
            console.log(defaultExpand,'defaultExpand')
            // defaultExpand

		}

        watch(filterText, (val) => {
            console.log(treeRef.value,'treeRef.value')
            console.log(val,'val')
            treeRef.value!.filter(val)
        })

        const filterNode = (value: string, data: Tree) => {
            console.log(value,'value')
            if (!value) return true
            return data.node_type_name.includes(value)
        }

        onMounted(()=>{
            getData();
        })

        return {
            syd,
			recurrence,
			getData,
            defaultProps,
            treeSyd,
            filterNode,
            filterText,
            treeRef,
            defaultExpand
        }
    }
})
</script>

<style scoped>
.el-tree-node .is-penultimate  > .el-tree-node__content{
  color: forestgreen !important;
}
</style>