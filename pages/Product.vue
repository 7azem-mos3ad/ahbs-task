<template>
<div id="product">
    <Navbar/>
    <Navigation/>
    <ProductContent/>
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
}
#product {
  display: grid;
  background-color: #eff7ff;
  grid-template-columns: repeat(12, 1fr);
  grid-template-rows: 40px 25px auto 30px 15px;
  row-gap: 5px;
min-height:100vh
}
</style>
