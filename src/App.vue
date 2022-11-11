<template>
  <h1>ToDo List</h1>
  <Container />
</template>

<script>
import Container from './components/Container';
export default {
  name: 'App',
  components: {
    Container,
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Dancing+Script:wght@400;700&family=Lato:ital,wght@0,300;0,400;1,300;1,400&display=swap');
* {
  margin: 0;
  padding: 0;
  outline: 0;
  box-sizing: border-box;
  -webkit-font-smoothing: antialiased;
  user-select: none;
}
html,
body {
  width: 100%;
  height: 100%;
}
body {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  background-color: #f5f5f5;
  font-family: 'Lato', sans-serif;
}
#app {
  width: 90%;
  min-width: 500px;
}
h1 {
  font-family: 'Dancing Script', cursive;
  text-align: center;
  margin-bottom: 50px;
  font-size: 45px;
  color: #335c62;
  font-weight: 700;
}

input,
button {
  font: 400 20px 'Lato', sans-serif;
  padding-left: 5px;
  padding-right: 5px;
}
</style>
