<template>
  <div class="breadcrumbs">
    <div class="navigation_menu" v-on:click="canShow = !canShow">
      <button id="navigationMenu"><i class="fas fa-bars"></i></button>
    </div>
      <ol
    vocab="http://schema.org/"
    typeof="BreadcrumbList"
  >
  <li><i class="fas fa-home"></i>
</li>
    <li property="itemListElement" typeof="ListItem">
      <NLink property="item" typeof="WebPage" to="/">
        <span property="name">home</span>
      </NLink>
      <meta property="position" content="1" />
    </li>
    <li
      v-for="(crumb, index) in crumbs"
      :key="index"
      property="itemListElement"
      typeof="ListItem"
    >
      <NLink property="item" typeof="WebPage" :to="crumb.path">
        <span property="name">{{
          $route.fullPath === crumb.path && title !== null ? title : crumb.title
        }}</span>
      </NLink>
      <meta property="position" :content="index + 2" />
    </li>
  </ol>
  <div class="absolute_menu" v-show="canShow">
    <div class="product" @click="$router.push({path: '/Product'})">
      <img src="../assets/images/admin.svg" alt="">
      <p>Product</p>
    </div>
  </div>
  </div>
</template>

<script>
const titleCase = require('ap-style-title-case')
export default {
  data: () => ({
    canShow: false
  }),
  props: {
    title: {
      type: String,
      default: null,
    },
  },
  methods: {
    showMenu: () => {

    },
  },
  computed: {
    crumbs() {
      const fullPath = this.$route.fullPath
      const params = fullPath.startsWith('/')
        ? fullPath.substring(1).split('/')
        : fullPath.split('/')
      const crumbs = []
      let path = ''
      params.forEach((param, index) => {
        path = `${path}/${param}`
        const match = this.$router.match(path)
        if (match.name !== null) {
          crumbs.push({
            title: titleCase(param.replace(/-/g, ' ')),
            ...match,
          })
        }
      })
      return crumbs
    },
  },
}
</script>

<style scoped>
.breadcrumbs {
  background-color: #0357a8;
  grid-row: 2 / span 1;
  grid-column: span 12;
    display: flex;
  align-items: center;
  position: relative;
  margin: 0 10px;
  border-radius: 3px;
}
.navigation_menu {
  position: relative;
  height: 100%;
  display: flex;
  align-items: center;
}
.navigation_menu:after {
  content: '';
  position: absolute;
  border-right: 1px solid #FFF;
  width: 0;
  height: 100%;
  top: 0;
  right: 0;
}
.navigation_menu button {
  background-color: inherit;
  border: 0;
  color: #fff;
}
ol {
  list-style: none;
}
li {
  display: inline;
  text-decoration: none;
}
li .fa-home {
  color: #fff;
}
li:after {
  content: ' > ';
  display: inline;
  font-size: 0.9em;
  color: #aaa;
  padding: 0 0.0725em 0 0.15em;
}
li:last-child:after {
  content: '';
}
li a {
  color: #bbb;
  text-decoration: none;

}
li a.nuxt-link-exact-active.nuxt-link-active {
  color: #fff;
}
.absolute_menu {
  height: 45px;
  width: 100%;
  bottom: -50px;
  background-color: #ecfbff;
  border: 1px solid #CCC;
  border-radius: 5px;
  position: absolute;
  display: grid;
  grid-template-columns: repeat(10, 8%);
  /* justify-content: space-around; */
  column-gap: 3px;
}
.absolute_menu .product {
  box-sizing: border-box;
  padding: 4px;
  cursor: pointer;
}
.absolute_menu .product img {
  height: 40%;
  width: 40%;
  text-align: center;

}
.absolute_menu .product p {
  font-size: 10px;
  margin: -2px 0 0 5px ;
}
</style>
