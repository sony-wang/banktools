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
            <a v-bind:class="item.class" @click="link(item.type,item.link)" href="javascript:;">{{ item.name }}</a>
          </div>
        </div>
    
  </div>
</template>

<script>
const downloadroot = 'https://cf2.pptest.xyz/downloads/china/'//中國載跟目錄
const banktool = 'https://cf2.pptest.xyz/downloads/china/banktool/'//網銀工具
const dai_fu = 'https://cf2.pptest.xyz/downloads/china/dai_fu/'//代付款
const dai_shou = 'https://cf2.pptest.xyz/downloads/china/dai_shou/'//代收款
const shou_zhi = 'https://cf2.pptest.xyz/downloads/china/shou_zhi/'//收支
const wei_xin = 'https://cf2.pptest.xyz/downloads/china/wei_xin/'//微信

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
        {type:'网银工具',name:'网银工具',link:'LongPay_5.0.rar',class:'bg_blue'},
        {type:'文件',name:'教学文件-pdf',link:'unionpay_tools_document_v1.0.0.pdf',class:'bg_red'},
        {type:'文件',name:'支转支信息获取方法-pdf',link:'z2z_method.pdf',class:'bg_red'},
        {type:'软件',name:'虚拟大师-apk',link:'vmos100117_2.apk',class:'bg_green'},
        {type:'软件',name:'云闪付-apk',link:'com.unionpay_v7.0.1.apk',class:'bg_green'},
        {type:'QQ通',name:'QQ通-apk',link:'javascript:;',class:'bg_green'},
        {type:'代收',name:'云闪付小助手-apk',link:'云闪付小助手2.4_v2.4.0.apk',class:'bg_green'},
        {type:'代付',name:'工行代付小助手-apk',link:'工行代付小助手1.2_v1.2.0.apk',class:'bg_green'},
        {type:'代付',name:'农行代付小助手-apk',link:'农行代付小助手3.2_v3.2.0.apk',class:'bg_green'},
        {type:'代付',name:'建行代付小助手-apk',link:'建行代付小助手1.2_v1.2.0.apk',class:'bg_green'},
        {type:'微信',name:'微信小助手-apk',link:'微信小助手2.2_v2.2.0.apk',class:'bg_green'},
        {type:'微信',name:'微信店员通-apk',link:'微信店员通2.2_v2.2.0.apk',class:'bg_green'},
        {type:'收支',name:'工行收支小助手-apk',link:'工行收支小助手1.2_v1.2.0.apk',class:'bg_yellow'},
        {type:'收支',name:'中國收支小助手-apk',link:'中國收支小助手1.2_v1.2.0.apk',class:'bg_yellow'},
        {type:'收支',name:'平安收支小助手-apk',link:'平安收支小助手1.2_v1.2.0.apk',class:'bg_yellow'},
        {type:'收支',name:'民生收支小助手-apk',link:'民生收支小助手1.2_v1.2.0.apk',class:'bg_yellow'},
        {type:'收支',name:'交通收支小助手-apk',link:'交通收支小助手1.2_v1.2.0.apk',class:'bg_yellow'},
        {type:'收支',name:'建行收支小助手-apk',link:'建行收支小助手1.2_v1.2.0.apk',class:'bg_yellow'},
        {type:'收支',name:'浦发收支小助手-apk',link:'浦发收支小助手1.2_v1.2.0.apk',class:'bg_yellow'},
        {type:'收支',name:'农行收支小助手-apk',link:'农行收支小助手1.0_v1.0.0.apk',class:'bg_yellow'},
        {type:'收付',name:'中國收付小助手-apk',link:'中國收付小助手1.0_v1.0.0.apk',class:'bg_pink'},
      ],
      input:{
        type:"全部",
        name:""
      },
      qqton:{
        ts:'http://cf2m.pptest.xyz/uploads/document/app/app-release1.1.28_test.apk',
        lt:'http://47.75.4.142/uploads/document/app/app-release1.1.28_lt.apk',
        qx:'http://qxpay.xyz/uploads/document/app/app-release1.1.28_qx.apk',
      }
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
    link(fileType,fileName){
      let getFileURL
      let platform
      switch(fileType){
        case '网银工具':
          getFileURL = banktool + fileName
          // location.href = getFileURL;
          window.open(getFileURL, '_blank');
        break
        case '文件':
          getFileURL = downloadroot + fileName
          window.open(getFileURL, '_blank');
        break
        case '软件':
          getFileURL = downloadroot + fileName
          window.open(getFileURL, '_blank');
        break
        case 'QQ通':
          platform = prompt('请输入代号','')
          if(platform === 'ts'){
            getFileURL = this.qqton.ts
          }
          else if(platform === 'lt'){
            getFileURL = this.qqton.lt
          }
          else if(platform === 'qx'){
            getFileURL = this.qqton.qx
          }
          else if(platform === null){
            return
          }
          else {
             alert('请输入正确的代号')
            return
          }
          window.open(getFileURL, '_blank');
        break
        case '代收':
          getFileURL = dai_shou + fileName
          window.open(getFileURL, '_blank');
        break
        case '代付':
          getFileURL = dai_fu + fileName
          window.open(getFileURL, '_blank');
        break
        case '微信':
          getFileURL = wei_xin + fileName
          window.open(getFileURL, '_blank');
        break
        case '收支':
          getFileURL = shou_zhi + fileName
          window.open(getFileURL, '_blank');
        break
      }
        console.log(getFileURL);


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
