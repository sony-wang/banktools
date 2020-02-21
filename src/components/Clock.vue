<template>
    <div class="Clock">
        <p>{{ datestamp }}</p>
        <p>{{ timestamp }}</p>
    </div>
</template>

<script>
export default {
    name:'Clock',
    data(){
        return{
            datestamp: "",
            timestamp: "",
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
<style scope lang="scss">
    p{
        color: #888;
        font-size: 18px;
        text-align: right;
        margin: 0;
    }
</style>