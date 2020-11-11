<template>
  <div>
    <div>
      <p>現在位置：{{latitude}},{{longtitude}}</p>
      <button @click="getLocation">現在位置取得</button>
    </div>
  </div>
</template>

<script>
import { Options, Vue } from 'vue-class-component';

const gpsComponent = {
  data() {
    return {
      latitude:0,
      longtitude:0
    }
  },
  methods:{
    getLocation () {

      console.log("process");
      console.log(process);
      console.log("navigator");
      console.log(navigator);

     if (process.client) {
       if (!navigator.geolocation) {
         alert('現在地情報を取得できませんでした。お使いのブラウザでは現在地情報を利用できない可能性があります。エリアを入力してください。')
         return
       }

       const options = {
         enableHighAccuracy: false,
         timeout: 5000,
         maximumAge: 0
       }

        console.log(options);

       navigator.geolocation.getCurrentPosition(this.success, this.error, options)
     } else {
       alert('現在地情報を取得できませんでした。お使いのブラウザでは現在地情報を利用できない可能性があります。エリアを入力してください。')
     }
   },
   success (position) {
     console.log("position");
     this.latitude = position.coords.latitude
     this.longitude = position.coords.longitude
     console.log(`緯度：${this.latitude}`);
     console.log(`緯度：${this.longtitude}`);
   },
   error (error) {
     console.log("error");
     switch (error.code) {
       case 1: //PERMISSION_DENIED
         alert('位置情報の利用が許可されていません')
         break
       case 2: //POSITION_UNAVAILABLE
         alert('現在位置が取得できませんでした')
         break
       case 3: //TIMEOUT
         alert('タイムアウトになりました')
         break
       default:
         alert('現在位置が取得できませんでした')
         break
     }
   }
  }
}

export default gpsComponent;

</script>