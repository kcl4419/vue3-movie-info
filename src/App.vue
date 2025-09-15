<template> 
<!-- html을 작성하는 공간 -->
  <h1>
    영화정보
  </h1>
  <div v-for="(movie,i) in data" :key="i" class="item">
    <figure>
      <img :src="`${movie.imgUrl}`" :alt="movie.title">
         <!-- 동적(변수)인 값은 무조건 :을 사용 -->
    </figure>

    <div class="info">
      <h3 class="bg-yellow" :style="movie.textRed">{{movie.title}}</h3>
      <p>개봉: {{movie.year}}</p>
      <p>장르: {{movie.category}}</p>
          <!-- 데이터바인딩 html에 데이터넣는것  
      - 일반 : {{ 변수명 }}
      - 속성 : 속성명="변수명"
      -->
      <button v-on:click="increseLike(i)">좋아요</button> <span>{{ movie.like }}</span>
      <!-- v-on 축약형 : @ -->

    </div>
    <!-- <p>{{ foods[0] }}</p>
    <p>{{ foods[1] }}</p>
    <p>{{ foods[2] }}</p> -->
    <p v-for="(item, i) in foods" :key="i">
      {{ item }}
    </p>
  </div>

</template>

<script>
// 자바스크립트
  export default{
    nmae:'App', //컨포넌트명 기재
    data(){ //문서에 표시될 변수, return필수
      return{
        data:[
          {
            title:"노량",
            year : 2023,
            category : "액션, 드라마",
            textRed:"color:red",
            like:0,
            imgUrl : "/assets/노량.jpg"
          },
          {
            title:"아쿠아맨과 로스트 킹덤",
            year : 2023,
            category : "액션, 판타지, 어드벤처",
            textRed:"color:blue",
            like:0,
            imgUrl : "/assets/아쿠아맨.jpg"
          },
          {
            title:"3일의 휴가",
            year : 2023,
            category : "판타지 드라마",
            like:0,
            imgUrl : "/assets/3일의휴가.jpg"
          }
          

        ]

      }

    },
    methods:{
      increseLike(i){
          this.data[i].like +=1;
      }
    }
  }
</script>

<style>
/* css코드 */
* {
  box-sizing: border-box;
  margin: 0;
}
body {
  max-width: 768px;
  margin: 0 auto;
  padding: 20px;
}
h1, h2, h3 {
  margin-bottom: 1rem;
}
p {
  margin-bottom: 0.5rem;
}
button {
  margin-right: 10px;
}
.item {
  width: 100%;
  border: 1px solid #ccc;
  display: flex;
  margin-bottom: 20px;
  padding: 1rem;
}
.item figure {
  width: 30%;
  margin-right: 1rem;
}
.item img {
  width: 100%;
}
.item .info {
  width: 100%;
}
</style>
