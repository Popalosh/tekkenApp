<script>
export default {
  name: 'TekkenApp',
  props: {
    msg: String
  }
}

</script>

<template>
  <div class="navbar">
    <div class="left">
        <p class="roboto-font-white">Бронирование</p>
    </div>
    <div class="right">
        <button class="btn roboto-btn">Регистрация</button>
    </div>
  </div>
</template>

<style scoped>
.navbar {
  background:  #393186;
  padding: 16px;
  padding-top: 5px;
  padding-bottom: 5px;
}

.roboto-font-white {
  font-family: Roboto;
  font-size: 20px;
  font-weight: 400;
  color: white;
}
.roboto-btn {
  font-family: Roboto;
  font-size: 16px;
  border: 1px solid black;
  background-color: white;
  color: black;
  font-weight: 400;
}

.right {
  float: right!important;
}

.left {
  float: left!important;
}

</style>
