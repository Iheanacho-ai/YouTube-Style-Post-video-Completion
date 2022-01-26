<template>
  <div>

    <video 
    id= "video-player"
    class="cld-video-player"
    >
    </video> 
    <div class="overlay"  v-if = 'overlay'>
      <div class="cards">
        <a href="https://www.youtube.com/watch?v=1wkPMUZ9vX4">
          <div :style="{ 'backgroundImage': 'url(https://images.pexels.com/photos/15286/pexels-photo.jpg?auto=compress&cs=tinysrgb&dpr=1&w=500)' }"></div>
        </a>
        <a href="https://www.youtube.com/watch?v=IUN664s7N-c">
          <div :style="{ 'backgroundImage': 'url(https://images.pexels.com/photos/3408744/pexels-photo-3408744.jpeg?auto=compress&cs=tinysrgb&dpr=1&w=500)' }"></div>
        </a>
        <a href="https://www.youtube.com/watch?v=Faow3SKIzq0">
          <div :style="{ 'backgroundImage': 'url(https://images.pexels.com/photos/572897/pexels-photo-572897.jpeg?auto=compress&cs=tinysrgb&dpr=1&w=500)' }"></div>
        </a>
        <a href="https://www.youtube.com/watch?v=7bOptq-NPJQ">
          <div :style="{ 'backgroundImage': 'url(https://images.pexels.com/photos/624015/pexels-photo-624015.jpeg?auto=compress&cs=tinysrgb&dpr=1&w=500)' }"></div>
        </a>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    data(){
      return{
        cld: null,
        player: null,
        video: "production_ID_4456999_gr6iy4",
        overlay: false
      }
    },

    mounted(){
      this.cld= cloudinary.Cloudinary.new({
        cloud_name:  "amarachi-2812",
        secure:  true
      })
      this.player = this.cld.videoPlayer(
        'video-player', {
          controls: true
        }
      )

      this.player.source(this.video);

      this.player.on('ended', ()=> {
        this.overlay= true;
      })
      this.player.on('play', ()=> {
        this.overlay = false;
      })

      

     
      
    }

  }


</script>

<style scoped>

@import url('https://fonts.googleapis.com/css2?family=Nunito:wght@300&display=swap');


div{
  display: flex;
  align-items: center;
  justify-content: center;

}

.cld-video-player{
  width: 500px;
  height: 500px;
}
.overlay{
  width: 500px;
  height: 500px;
  position: absolute;
  background-color: rgba(0,0,0, 0.70);

  
}
.cards{
  width: 80%;
  height: 80%;
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: 1fr 1fr;
  gap: 20px;

}
.cards a{
  width: 100%;
  height: 100%;
}
.cards div{
  width: 100%;
  height: 100%;
  background-size: cover;
  background-repeat: no-repeat;
}


</style>
