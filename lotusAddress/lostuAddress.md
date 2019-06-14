# lotus-address

> 省市区三级联动选择组件 适用H5/APP/微信小程序

## how to use 

### 插件的方式引入使用
1.xx.vue 
```$xslt
    import lotusAddress from "../../components/Winglau14-lotusAddress/Winglau14-lotusAddress.vue";
```

2.vue页面内引用：<br/>
```
    <lotus-address v-on:choseVal="choseValue" :lotusAddressData="lotusAddressData"></lotus-address>
```
3.参数说明：<br/>
（1）参数定义
```$xslt
    data () {
        return {
            lotusAddressData:{
                visible:false,
                provinceName:'广东省',
                cityName:'广州市',
                townName:'天河区',
            },
			region:''
        }
    }
```

4.方法定义与调用：<br/>
```$xslt
    components:{
	    "lotus-address":lotusAddress
	},
    methods: {
        //打开picker
        openPicker() {
            this.lotusAddressData.visible = true;
        },
        //回传已选的省市区的值
        choseValue(res){
			//res数据源包括已选省市区与省市区code
			console.log(res);
            this.lotusAddressData.visible = res.visible;//visible为显示与关闭组件标识true显示false隐藏
            //res.isChose = 1省市区已选 res.isChose = 0;未选
            if(res.isChose){
                this.lotusAddressData.provinceName = res.provice;//省
                this.lotusAddressData.cityName = res.city;//市
                this.lotusAddressData.townName = res.town;//区
                this.region = `${res.provice} ${res.city} ${res.town}`; //region为已选的省市区的值
            }
        }
    }
```





