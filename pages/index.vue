<template>
<div id="home">
    <Navbar/>
    <Navigation/>
    <Hello/>
    <Footer/>
</div>
</template>

<script>
export default {
}
</script>

<style>
body {
  margin: 0;
  padding: 0;
  /* min-height:100vh */
}
#home {
  display: grid;
  row-gap: 10px;
  background-color: #eff7ff;
  grid-template-columns: repeat(12, 1fr);
  grid-template-rows: 40px 25px 1fr 30px 15px;
  min-height:100vh
}
</style>
