<template>
  <div class="Tools">
        <div class="list_group row">
          <div class="col-xl-6 col-lg-6 col-md-6 col-6">
            <select class="form-control" v-model="input.type">
              <option>全部</option>
              <option>网银工具</option>
              <option>文件</option>
              <option>软件</option>
              <option>代收</option>
              <option>代付</option>
              <option>收支</option>
              <option>QQ通</option>
            </select>
          </div>
          <div class="col-xl-6 col-lg-6 col-md-6 col-6">
            <input type="text" class="form-control" v-model="input.name">
          </div>
          <div class="col-xl-6 col-lg-6 col-md-12 list_wrapper" v-for="(item,index) in nameList" :key="index">
            <!-- <a v-bind:class="item.class" :href="item.link" target="_blank">{{ item.name }}</a> -->
            <a v-bind:class="item.class" @click="link(item.name)" href="javascript:;">{{ item.name }}</a>
          </div>
        </div>
    
  </div>
</template>

<script>
// const downloadroot = 'https://cf2.pptest.xyz/downloads/china/'//中國載跟目錄
// const banktool = 'https://cf2.pptest.xyz/downloads/china/banktool/'//網銀工具
// const dai_fu = 'https://cf2.pptest.xyz/downloads/china/dai_fu/'//代付款
// const dai_shou = 'https://cf2.pptest.xyz/downloads/china/dai_shou/'//代收款
// const shou_zhi = 'https://cf2.pptest.xyz/downloads/china/shou_zhi/'//收支
// const wei_xin = 'https://cf2.pptest.xyz/downloads/china/wei_xin/'//微信

// const qq_ts = 'http://cf2m.pptest.xyz/uploads/document/app/app-release1.1.2_test.apk'
// const qq_lt = 'http://47.75.4.142/uploads/document/app/app-release1.1.2_lt.apk'
// const qq_qx = 'http://qxpay.xyz/uploads/document/app/app-release1.1.2_qx.apk'
// let qq = 'javascript:;'

export default {
  name: "Tools",
  props: {
    // title:String,
  },
  //代付-代收-收支-微信-軟件
  data(){
    return{
      user:'ts',
      list:[
        {type:'网银工具',name:'网银工具',link:'LongPay_4.6.rar',class:'bg_blue'},
        {type:'文件',name:'教学文件-pdf',link:'unionpay_tools_document_v1.0.0.pdf',class:'bg_red'},
        {type:'文件',name:'支转支信息获取方法-pdf',link:'z2z_method.pdf',class:'bg_red'},
        {type:'软件',name:'虚拟大师-apk',link:'vmos100117_2.apk',class:'bg_green'},
        {type:'软件',name:'云闪付-apk',link:'com.unionpay_v7.0.1.apk',class:'bg_green'},
        {type:'QQ通',name:'QQ通-apk',link:'javascript:;',class:'bg_green'},
        {type:'代收',name:'云闪付小助手-apk',link:``,class:'bg_green'},
        {type:'代付',name:'工行代付小助手-apk',link:``,class:'bg_green'},
        {type:'代付',name:'农行代付小助手-apk',link:``,class:'bg_green'},
        {type:'代付',name:'建行代付小助手-apk',link:``,class:'bg_green'},
        {type:'微信',name:'微信小助手-apk',link:``,class:'bg_green'},
        {type:'微信',name:'微信店员通-apk',link:``,class:'bg_green'},
        {type:'收支',name:'工行收支小助手-apk',link:``,class:'bg_yellow'},
        {type:'收支',name:'中國收支小助手-apk',link:``,class:'bg_yellow'},
        {type:'收支',name:'平安收支小助手-apk',link:``,class:'bg_yellow'},
        {type:'收支',name:'民生收支小助手-apk',link:``,class:'bg_yellow'},
        {type:'收支',name:'交通收支小助手-apk',link:``,class:'bg_yellow'},
        {type:'收支',name:'建行收支小助手-apk',link:``,class:'bg_yellow'},
        {type:'收支',name:'浦发收支小助手-apk',link:``,class:'bg_yellow'},
      ],
      input:{
        type:"全部",
        name:""
      },
     /*  srcURL:{
        downloadroot : 'https://cf2.pptest.xyz/downloads/china/',
        banktool : 'https://cf2.pptest.xyz/downloads/china/banktool/',
      },
      qqton:{
        ts:'http://cf2m.pptest.xyz/uploads/document/app/app-release1.1.2_test.apk',
        lt:'http://47.75.4.142/uploads/document/app/app-release1.1.2_lt.apk',
        qx:'http://qxpay.xyz/uploads/document/app/app-release1.1.2_qx.apk',
      } */
    }
  },
  methods:{
    link(name){
      alert(name)
    }
    //   switch(this.user){
    //   case 'ts':
    //     // qq = this.qqton.ts
    //     // qq = qq_ts
    //     alert('ss');
    //     console.log('ts')
    //     // console.log(qq)
    //     break
    //   case 'lt':
    //     // qq = this.qqton.lt
    //     console.log('lt')
    //     break
    //   case 'qx':
    //     // qq = this.qqton.qx
    //     console.log('qx')
    //     break
    //   }
    // }
  },
  beforeMounted(){
    /* switch(this.user){
      case 'ts':
        // qq = this.qqton.ts
        qq = qq_ts
        console.log('ts')
        console.log(qq)
        break
      case 'lt':
        qq = this.qqton.lt
        console.log('lt')
        break
      case 'qx':
        qq = this.qqton.qx
        console.log('qx')
        break

    } */
  },
  computed:{
    typeList(){
      if(this.input.type !== '全部'){
        return this.list.filter(item=>{
          return item.type === this.input.type
        })
      }else{
        return this.list
      }
    },
    nameList(){
      if(this.input.name){
        return this.typeList.filter(item=>{
          let content = item.name.toLowerCase()
          let keyword = this.input.name.toLowerCase()
          return content.indexOf(keyword) !== -1
        })
      }else{
        return this.typeList
      }
    }
  },
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
</style>
