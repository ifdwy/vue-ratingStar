<template>
  <div id="star">
    <div class="ritings">
      <img v-for="(star, index) in stars" :src="star.src" @click="rating(index)" class="rating-item">
    </div>
  </div>
</template>

<script>
  export default{
    data(){
      return{
        stars: [{
          src: "/static/image/goods/star.png",
          active: false
        },
        {
          src: "/static/image/goods/star.png",
          active: false
        },
        {
          src: "/static/image/goods/star.png",
          active: false
        },
        {
          src: "/static/image/goods/star.png",
          active: false
        },
        {
          src: "/static/image/goods/star.png",
          active: false
        }
        ],

        starNum: 0,
      }
    },
    methods:{
      rating(index){
        var total = this.stars.length;
        var idx= index+1;
        // console.log(idx)
        
        if(this.starNum == 0){
          this.starNum = idx;

          for(var i=0; i< idx; i++){
            this.stars[i].src = "/static/image/goods/fullstar.png";
            this.stars[i].active= true;
          }

        }else{
          if(idx == this.starNum){
            for(var i=index; i<total; i++){
              this.stars[i].src = "/static/image/goods/star.png";
              this.stars[i].active= false;
            }
          }
        }

        if(idx <this.starNum){
          for(var i=idx; i<this.starNum; i++){
              this.stars[i].src = "/static/image/goods/star.png";
              this.stars[i].active= false;
            }
        }

        if(idx >this.starNum){
          for(var i=0; i<idx; i++){
              this.stars[i].src = "/static/image/goods/fullstar.png";
              this.stars[i].active= true;
            }
        }


        var count=0;
        for(var i=0; i<total; i++){
          if(this.stars[i].active){
            count ++;
          }
        }
        this.starNum = count;


      }
    }

  }
</script>

<style>
.ritings{
  width: 150px;
  height: 30px;
}

.rating-item{
  width: 30px;
  height: 30px;
}
</style>