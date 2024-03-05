<template>
  <div>
    <nav>
    <button @click="changePage(1)">
      Заполнить данными
    </button>
    <button @click="changePage(2)">
      Отображение данных
    </button>
  </nav>
  <FirstPage @formatToJSON="takeData" v-if="page==1"></FirstPage>
  <SecondPage :json="jsonData" v-if="page==2"></SecondPage>
  </div>
</template>

<script>
import FirstPage from './components/FirstPage.vue'
import SecondPage from './components/SecondPage.vue'
  export default {
    components: {
      FirstPage, SecondPage
    },
    data() {
      return {
        jsonData: '',
        page: 1,
      }
    },
    methods: {
      takeData(data) {
        this.jsonData = data.result;
      },
      changePage(pageNumber) {
        this.page = pageNumber;
      },
    },
  }
</script>

<style>
body {
    height: 100vh;
    margin: 0;
    background-color: rgba(0, 0, 0, 0.750);
}
.start {
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
}

.start_button {
    color: white;
    background-color: rgb(43, 112, 158);
    width: 150px;
    height: 100px;
    border: none;
    border-radius: 15%;
    font-size: 28px;
}
.start_button:hover {
    transition: 100ms;
    background-color: rgb(0, 98, 163);
}
.popup {
    margin: 0 auto;
    margin-top: 10px;
    padding-bottom: 10px;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    max-width: 500px;
    border: 5px solid black;
}

.popup_content {
    color: white;
    text-align: center;
}

input {
    margin-top: 10px;
    margin-right: 5px;
}

.popup_button {
    color: white;
    background-color: rgb(43, 112, 158);
    border: none;
    border-radius: 5%;
    height: 35px;
    margin-top: 10px;
}

.popup_button:hover {
    transition: 100ms;
    background-color: rgb(0, 98, 163);
}

.result {
    height: 100vh;
    color: white;
    background-color: black;
}

nav {
    padding-top: 10px;
    padding-bottom: 10px;
    background-color: black;
    display: flex;
    justify-content: space-around;
}

nav > button {
    color: white;
    background-color: rgb(43, 112, 158);
    border: none;
    border-radius: 5%;
    height: 35px;
}
</style>