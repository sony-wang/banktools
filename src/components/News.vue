<template>
    <div class="News">
        
          <div class="announcement">
            <h2>公告信息</h2>
            <ul id="news">
              <li  :class="[item.status,'row' ]" v-for="(item,index) in info" :key="index">
                <span class="col-xl-1 col-lg-1 col-md-2 col-1"></span>
                <span class="col-xl-4 col-lg-3 col-md-10 col-4">{{ item.date }}</span>
                <span class="col-xl-5 col-lg-6 col-md-10 col-5">{{ item.title }}</span>
                <span class="col-xl-2 col-lg-1 col-md-2 col-2">{{ item.version }}</span>
              </li>
            </ul>
          </div>
        
    </div>
</template>

<script>
export default {
    data(){
        return{
            info:[
                {date:'2020/04/15',title:'网银工具',version:'[5.5]',status:'new'},
                {date:'2020/04/14',title:'农行代付小助手',version:'[3.3]',status:'new'},
                {date:'2020/04/06',title:'收付小助手',version:'[2.0]',status:''},
                {date:'2020/03/24',title:'工行收支小助手',version:'[2.1]',status:''},
                {date:'2020/03/03',title:'工行代付小助手',version:'[1.2]',status:''},
                {date:'2020/03/03',title:'中国收付小助手',version:'[1.0]',status:''},
                {date:'2020/02/27',title:'农行收支小助手',version:'[1.0]',status:''},
                {date:'2020/02/12',title:'建行代付小助手',version:'[1.2]',status:''},
                {date:'2020/02/12',title:'工行代付小助手',version:'[1.1]',status:''},
                {date:'2020/02/12',title:'云闪付小助手',version:'[2.4]',status:''},
                {date:'2020/02/12',title:'微信小助手',version:'[2.2]',status:''},
                {date:'2020/02/12',title:'微信店员通',version:'[2.2]',status:''},
                {date:'2020/02/12',title:'收支小助手',version:'[1.2]',status:''},
                {date:'2020/01/03',title:'QQ通',version:'[1.1.1]',islatest:''},
            ],
        }
    },
    
}
</script>



<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    #news{
        li{
            position: relative;
            list-style-type: none;
            margin: 5px 0 5px 0;
            padding-bottom: 5px;
            border-bottom: #ddd solid 1px;
            
            span:nth-child(1) {
                // width: 10%;
                text-align: left;
            }
            span:nth-child(2) {
                // width: 30%;
                text-align: center;
            }
            span:nth-child(3), 
            span:nth-child(4) {
                // width: 30%;
                text-align: right;
            }
            &.new:before{
                content: "New";
                position: absolute;
                top: 0px;
                background: #ef7171;
                color: #ffffff;
                padding: 2px;
                border-radius: 8px;
                font-size: xx-small;
            }
        }
    }
</style>


