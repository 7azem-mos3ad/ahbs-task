<template>
  <div>
    <table id="produuctDetails" style="width: 100%">
      <thead>
        <tr>
          <th>Product</th>
          <th>On Hand</th>
          <th>Type</th>
        </tr>
        <tr>
          <th>
            <div class="input_search">
              <input type="text" name="search" />
              <button type="submit"><i class="fa fa-search"></i></button>
            </div>
          </th>
          <th>
            <div class="input_search">
              <input type="text" name="search" />
              <button type="submit"><i class="fa fa-search"></i></button>
            </div>
          </th>
          <th>
            <div class="input_search">
              <input type="text" name="search" />
              <button type="submit"><i class="fa fa-search"></i></button>
            </div>
          </th>
        </tr>
      </thead>
      <tbody></tbody>
    </table>
    <div class="no_data">
      <img src="../assets/images/noDataFoundGreen.svg" alt="" />
      <br>
      <p>Select warehouse and product</p>
    </div>
  </div>
</template>

<style scoped>
table {
  border: none;
}
th,
td,
tr {
  background-color: #d7e4f1;
  border: none;
}
input {
  background: #fff;
}
.no_data {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>>

</style>
