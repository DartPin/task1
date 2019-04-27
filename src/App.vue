<template>
  <div id="app">
    <div class="window">
      <p class="header-text">первое число</p>
      <input type="text" class="form-control" v-model="first">
      <p class="header-text">второе число</p>
      <input type="text" class="form-control" v-model="second">
      <div class="err" v-show="showErr">
        {{err}}
      </div>
      <div class="btn btn-primary" @click="summ()">сумма</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      err: "Здесь будет текст ошибки",
      first: 0.1 ,
      second: 0.2,
      showErr: false
    }
  },
  methods:{
    summ(){
      this.showErr = false;
      if(this.first === "" & this.second === ""){
        this.showErr = true;
        this.err = "Мне кажется вы что то забыли";
      } else if(this.first === "" || this.second === ""){
        if (isNaN(this.first) || isNaN(this.second)){
          this.showErr = true;
          this.err = "вы ввели некоректные значения";
        } else {
          this.showErr = true;
          this.err = "Вы не указали одно из чисел, поэтому я решил что это будет 0";
          alert ("Результат: " + (Number(this.first)*10 + Number(this.second)*10)/10)
        }       
      } else if (isNaN(this.first) || isNaN(this.second)){
        this.showErr = true;
        this.err = "вы ввели некоректные значения";
      } else {
        alert ("Результат: " + (Number(this.first)*10 + Number(this.second)*10)/10)
      }
      
    }
  }
}
</script>

<style>
  html,body{
    width: 100%;
    height: 100%;
  }
  #app{
    position: absolute;
    width: 100%;
    height: 100%;
    background: #AD66D5;
  }
  .window{
    position: absolute;
    width: 300px;
    margin: 20px 0 0 -150px;
    left: 50%; 
    border: 1px solid black;
    border-radius: 10px;
    padding: 10px;
    background: #876ED7;
  }
  .header-text{
    text-transform: uppercase;
    font-weight: bold;

  }
  .btn{
    position: relative;
    width: 100px;
    margin: 20px 0 10px -50px;
    left: 50%;

  }
  .err{
    position: relative;
    margin: 10px 0 10px 0 ;
    background-color:#E667AF;
    border-radius: 5px;
    color: red
  }
</style>
 