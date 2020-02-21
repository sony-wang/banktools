<template>
  <div class="wrapper">
    <div class="container">
      <h3>{{ title }}</h3>
      <h1>{{ datestamp }}</h1>
       <h1>{{ timestamp }}</h1>
      <div class="row bg_white pd20">
        <div class="list_group col-md-8 row">
          <div class="col-md-6">
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
          <div class="col-md-6">
            <input type="text" class="form-control" v-model="input.name">
          </div>
          <div class="col-md-6 list_wrapper" v-for="(item,index) in nameList" :key="index">
            <a v-bind:class="item.class" href="javascript:;">{{ item.name }}</a>
          </div>
        </div>
        <div class="col-md-4">
          <div class="announcement">
            <h2>公告信息</h2>
            <ul id="news" v-for="(item,index) in info" :key="index">
              <li class="row">
                <span></span>
                <span class="col-md-4">{{ item.date }}</span>
                <span class="col-md-6">{{ item.title }}</span>
                <span class="col-md-2">{{ item.version }}</span>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
        
export default {
  name: "Tools",
  props: {
    title:String
  },
  //代付-代收-收支-微信-軟件
  data(){
    return{
      list:[
        {type:"网银工具",name:"网银工具",link:"javascript:;",class:"bg_blue"},
        {type:"文件",name:"教学文件-pdf",link:"javascript:;",class:"bg_red"},
        {type:"文件",name:"支转支信息获取方法-pdf ",link:"javascript:;",class:"bg_red"},
        {type:"软件",name:"虚拟大师-apk",link:"javascript:;",class:"bg_green"},
        {type:"软件",name:"云闪付-apk",link:"javascript:;",class:"bg_green"},

        {type:"QQ通",name:"QQ通-apk",link:"javascript:;",class:"bg_green"},

        {type:"代收",name:"云闪付小助手-apk",link:"javascript:;",class:"bg_green"},
        
        {type:"代付",name:"工行代付小助手-apk",link:"javascript:;",class:"bg_green"},
        {type:"代付",name:"农行代付小助手-apk",link:"javascript:;",class:"bg_green"},
        {type:"代付",name:"建行代付小助手-apk",link:"javascript:;",class:"bg_green"},

        {type:"微信",name:"微信小助手-apk",link:"javascript:;",class:"bg_green"},
        {type:"微信",name:"微信店员通-apk",link:"javascript:;",class:"bg_green"},

        {type:"收支",name:"工行收支小助手-apk",link:"javascript:;",class:"bg_yellow"},
        {type:"收支",name:"中國收支小助手-apk",link:"javascript:;",class:"bg_yellow"},
        {type:"收支",name:"平安收支小助手-apk",link:"javascript:;",class:"bg_yellow"},
        {type:"收支",name:"民生收支小助手-apk",link:"javascript:;",class:"bg_yellow"},
        {type:"收支",name:"交通收支小助手-apk",link:"javascript:;",class:"bg_yellow"},
        {type:"收支",name:"建行收支小助手-apk",link:"javascript:;",class:"bg_yellow"},
        {type:"收支",name:"浦发收支小助手-apk",link:"javascript:;",class:"bg_yellow"},
      ],
      input:{
        type:"全部",
        name:""
      },
      info:[
        {date:"2020/02/14",title:"网银工具",version:"[4.6]",status:"new"},
        {date:"2020/02/12",title:"建行代付小助手",version:"[1.2]",status:"new"},
        {date:"2020/02/12",title:"农行代付小助手",version:"[3.2]",status:"new"},
        {date:"2020/02/12",title:"工行代付小助手",version:"1.1]",status:"new"},
        {date:"2020/02/12",title:"云闪付小助手",version:"[2.4]",status:"new"},
        {date:"2020/02/12",title:"微信小助手",version:"[2.2]",status:"new"},
        {date:"2020/02/12",title:"微信店员通",version:"[2.2]",status:"new"},
        {date:"2020/02/12",title:"收支小助手",version:"[1.2]",status:"new"},
        {date:"2020/01/03",title:"QQ通",version:"[1.1.1]",islatest:""},
      ],
      datestamp: "",
      timestamp: "",
    }
  },
  computed:{
    typeList(){
      if(this.input.type !== "全部"){
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
  mounted:function(){
     setInterval(this.currentTime, 1000);
  },
  methods:{
    currentTime: function() {
        const dt = new Date();
        const y = dt.getFullYear();
        const m = (dt.getMonth()+1<10?'0':'')+(dt.getMonth()+1);
        const d = (dt.getDate()<10?'0':'')+dt.getDate();
        const wObj = {0:"星期日",1:"星期一",2:"星期二",3:"星期三",4:"星期四",5:"星期五"}
        const w = dt.getDay().toString().replace(/0|1|2|3|4|5/gi,function(matched){return wObj[matched];})
        const h = (dt.getHours()<10?'0':'')+dt.getHours();
        const n = (dt.getMinutes()<10?'0':'')+dt.getMinutes();
        const s = (dt.getSeconds()<10?'0':'')+dt.getSeconds();
        const nowDate = y+"年"+m+"月"+d+"日"+" 【"+w+"】"
        const nowTime = h+":"+n+":"+s
        this.timestamp = nowTime;
        this.datestamp = nowDate
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "~@/assets/css/style.scss";
</style>
