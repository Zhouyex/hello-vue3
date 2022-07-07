<template>
  <!-- vue3页面 -->
  <div>
	test:
	<el-select v-model="value1" placeholder="Select" filterable :filter-method="filterData" multiple @visible-change="blurSel">
		<el-option-group
			v-for="group in arr_new1"
			:key="group.label"
			:label="group.label"
		>
		<el-option
			v-for="(items,indexs) in group.options"
			:key="indexs"
			:label="items.name"
			:value="items.name"
		/>
		</el-option-group>
	</el-select>
	
  </div>
</template>

<script lang='ts'>
import { defineComponent, onMounted, reactive, ref } from "vue";
import { toRaw} from "@vue/reactivity"

export default defineComponent({
  name: "HelloWorld",
  setup() {
	const value1 = ref([])
	let arr_new1:any = ref([]);
	const arr1 = [
		{big:'A',small:'a',id:'尚艳东',name:'尚艳东'},
		{big:'A',small:'a',id:'尚艳东',name:'尚艳东'},
		{big:'A',small:'a',id:'尚艳东',name:'尚艳东'},
		{big:'B',small:'b',id:'尚艳东水电费',name:'尚艳东水电费'},
		{big:'B',small:'b',id:'尚艳东水电费',name:'尚艳东水电费'},
		{big:'B',small:'b',id:'尚艳东水电费',name:'尚艳东水电费'},
		{big:'C',small:'c',id:'尚艳东啥的',name:'尚艳东啥的'},
		{big:'C',small:'c',id:'尚艳东啥的',name:'尚艳东啥的'},
		{big:'D',small:'d',id:'尚艳东按时',name:'尚艳东按时'},
		{big:'E',small:'e',id:'尚艳东是大法官',name:'尚艳东是大法官'},
		{big:'F',small:'f',id:'尚艳东阿萨德',name:'尚艳东阿萨德'},
		{big:'G',small:'g',id:'尚艳东爱上对方答复',name:'尚艳东爱上对方答复'},
	];
	const filterData = (key:string)=>{
		// 这里要写关键字筛选
        console.log(key,'筛选')
		console.log(arr1)
		let res = arr1.filter(item=>{
			return item.big == key || item.id.includes(key) || item.name.includes(key) || item.small == key;
		})
		console.log(res)
		arr_new1.value = sortKey(res,'big')
	}
    const sortKey=(data:any,k:any)=>{
        let res = data.reduce((prev:any, cur:any) => {
            var key = cur[k];
            if (!prev[key]) {
            	prev[key] = []
            }
            prev[key].push(cur)
            return prev
        }, {});
        let tmparr = [];
        for(let i in res){
            tmparr.push({
                label: i,
                options: res[i]
            })
        }
        return tmparr;
    }
	const blurSel = (v:any) =>{
		console.log(v)
		setTimeout(()=>{
			arr_new1.value = sortKey(arr1,'big')
		})
	}
	onMounted(()=>{
        arr_new1.value = sortKey(arr1,'big')
		console.log(arr_new1,'arrnew11111111111')

		tt()
	})

	const sss = reactive({
		qqq:[],
		aaa:'',
		rrr:null,
		bbb:'00',
		ccc:['qq','aa']
	})

	const tt = ()=>{
		console.log(sss)
		for(let i in sss){
			console.log(i,'iiii')

			// console.log(sss.i,'======================')

			if(sss[i] == [] || sss[i] ==''){
				
			}
		}
	}




    return {
		filterData,
		value1,
		arr1,
		arr_new1,
        sortKey,
		blurSel
	};
  },
});
</script>

<style scoped>
</style>