<template>
  <nav>
    <div class="logo">
      <img src="../assets/images/logo.png" alt="" />
    </div>
    <!-- <div class="input_search">
      <input type="search" />
    </div> -->
    <div class="input_search">
      <input
        type="text"
        placeholder="Search For Patient (Name, Code, Phone Number)"
        name="search"
      />
      <button type="submit"><i class="fa fa-search"></i></button>
    </div>
    <div class="select_language">
      <select name="language" id="language">
        <option value="english">English</option>
        <option value="arabic">عربي</option>
      </select>
    </div>
    <div class="profile">
      <img src="@/assets/images/user.png" alt="">
      <span>hazem mosaad mosbah</span>
    </div>
  </nav>
</template>

<script>
export default {
  name: "Navbar"
};
</script>

<style>
nav {
  grid-area: navbar;
  grid-column: span 12;
  background-color: #fff;
  grid-row: 1 / span 1;
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  align-content: center;
  padding: 5px;
}
.logo {
  grid-column: span 2;
}
.logo img {
  width: 100%;
  height: 100%;
}
.input_search {
  grid-column: 3 / span 3;
  display: flex;
  align-items: center;
}
.input_search input {
  border: 0;
  padding: 6px 0;
  border-radius: 2px;
  background-color: #e8f0f7;

  width: 90%;
}

.input_search button {
  border: 0;
  width: 10%;
  background-color: #e8f0f7;
  padding: 6px 2px;
  border-radius: 2px;
  position: relative;
}
.input_search button:before {
  content: "";
  width: 0;
  height: 100%;
  position: absolute;
  border-left: 1px solid #114e9d;
  top: 0;
  left: 0;
}
.input_search button svg {
  color: #114e9d;
}
.select_language {
  grid-column: 10 / span 1;
  display: flex;
  align-items: center;
  position: relative;
}
.select_language select {
  border: 0;
  color: #114e9d;
}
.select_language:after {
  content: "";
  position: absolute;
  border-right: 1px solid #114e9d;
  width: 0;
  height: 100%;
  top: 0;
  right: 0;
}
.profile {
  grid-column: 11 / span 2;
  display: flex;
  align-items: center;
  position: relative;
}
.profile img {
    margin: 0 3px;

}
</style>
