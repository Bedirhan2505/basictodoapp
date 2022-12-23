<template>
    <div>
      <div class="app">
        <form @submit.prevent="notekle">
          <div class="field">
            <div class="control">
              <input class="input" type="text" v-model="not" placeholder="Lütfen Not Giriniz....">
            </div>
          </div>
          <div class="buton">
            <button class="button is-success">Kayıt Ekle</button>
          </div>
        </form>
      </div>
      <div v-for="n in notlar" :key="n.id" class="box">
        <p  @click="done(n)">{{ n.content }}</p>  <br>
        <span>Yapıldı : {{ n.done }}</span>
      </div>
    </div>
</template>
<script>
import {ref} from 'vue';
export default {
  setup(){
    const not = ref("");
    const notlar = ref([]);

    function notekle(){
      notlar.value.push({
        done: false,
        content: not.value,
        id: Date.now()
      });
      not.value="";
    }
    function done(not){
      not.done = !not.done;
    }
    return {not,notlar,notekle,done};
  }
}
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  width: 600px;
  height: auto;
  margin: 100px 400px;
}
.button{
  margin-bottom:20px;
}
#tamam{
  font-size: 14px;
  text-decoration: overline;
}
</style>
