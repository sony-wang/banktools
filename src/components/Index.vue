<template>
  <div class="Index">
		 <h3>{{ title }}</h3>    
    <div class="container">
			<section class="bd1 pd20 shadow">
				<Clock></Clock>
				<hr>
				<div class="row">
					<div class="col-md-7">
						<Tools></Tools>
					</div>
					<div class="col-md-5">
						<News></News>
					</div>
				</div>
		</section>
    </div>
		
  </div>
</template>

<script>
import Clock from './Clock'
import Tools from './Tools'
import News from './News'

export default {
  name: "Index",
  components:{Clock,News,Tools},
  // props: {
  //   title:String
  // },
	props: [
    'title'
  ],
  data(){
    return{
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
@import "~@/assets/css/style.scss";
</style>
