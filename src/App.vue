<template>
<div class="menu">
  <a v-for="(a,i) in Menus" :key="i">{{a}}</a>
  <div class="black-bg" v-if="ModalUi==true"><!--조건식이 참일 때만 표시-->
    <div class="white-bg">
      <h4>상세페이지</h4>
      <p>상세페이지 내용</p>
      <button v-on:click="ModalUi=false" style="border-radius: 8px;">닫기</button>
    </div>
  </div>
</div>
  <div v-for="(a,k) in products" :key="k">
    <img v-bind:src= imglist[k] class = "room-img"><!-- 태그 속성데이터바인딩 할때는 v-bind사용. -->
    <h4 @click="ModalUi=true">{{a}}</h4>
    <p>{{price[k]}}</p>
    <button v-on:click="신고수[k]++">허위매물신고</button> <span>신고수 : {{신고수[k]}}</span>
  </div>
</template>
<script>
//함수 모음.


//Vue 반복문은 변수 작명을 두개 할수있다.
//왼쪽 변수는 array내의 데이터, 오른쪽 변수는 1씩 증가하는 정수이다.
export default {
  name: 'App',
  //데이터 보관함,html 속성도 바인딩 가능
  data(){
    return{
      Menus : ['Home','Shop','About'],
      
      products : ['역삼동원룸','천호동원룸','마포구원룸'],
      price : [70,50,40],
      신고수 : [0,0,0],
      imglist : [require("./assets/room0.jpg"),require("./assets/room1.jpg"),require("./assets/room2.jpg")],
      ModalUi : false,
    }
  },
//동적인ui만드는법.1 ui현재 상태를 데이터로 저장. 2 데이터에 따라 ui가 어떻게 보일지 작성.
  methods: {
  increase(){
    this.신고수[this.k]+=1//변수범위 지정
  }
},

  components: {

  }
}
</script>

<style>
body{
  margin : 0
}
div {
  box-sizing: border-box;
}
.black-bg{
  width:100%;height: 100%;
  background: rgba(0, 0, 0, 5);
  position: fixied; padding: 20px;
}
.white-bg{
  width:100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu{
  background: #2c3e50;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
}
.room-img{
  width:100%;
  margin-top: 40px;

}
</style>
