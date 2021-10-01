<template>
  <section>
    <h3>Product</h3>
    <div class="form_content">
      <div class="basic_information">
        <div class="header">
          <h4><i class="fas fa-qrcode"></i> Basic Information</h4>
          <hr />
        </div>
        <div class="warehouse">
          <label for="warehouse">warehouse</label>
          <select
            name="warehouse"
            id="warehouse"
            required
            v-model="selectedWarehouse"
          >
            <option selected disabled hidden>select warehouse</option>
            <option
              v-for="warehouse in warehouses"
              v-bind:value="warehouse.id"
              :key="warehouse.id"
              >{{ warehouse.name }}</option
            >
          </select>
        </div>
        <div class="type">
          <label for="type">type</label>
          <select
            name="type"
            id="type"
            required
            v-model="selectedType"
            :disabled="!selectedWarehouse"
          >
            <option selected disabled hidden>select UOM type</option>
            <option
              v-for="type in filteredTypes"
              v-bind:value="type.id"
              :key="type.id"
              >{{ type.name }}</option
            >
          </select>
        </div>
        <div class="show_balance">
          <br>
          <input type="checkbox" id="show" name="show" value="show" />
          <label for="show"> show zero balance</label><br />
        </div>
        <div class="product_classification">
          <p>product Classification</p>
          <input
            type="radio"
            id="allProduct"
            name="product_classification"
            value="All_Product"
            v-model="picked"
            :disabled="!selectedWarehouse || !selectedType"
          />
          <label for="allProduct">All Product</label>
          <input
            type="radio"
            id="specificProduct"
            name="product_classification"
            value="Specific_Product"
            v-model="picked"
            :disabled="!selectedWarehouse || !selectedType"
          />
          <label for="specificProduct">Specific Product</label>
        </div>
        <div class="specifi_product" v-show="picked === 'Specific_Product'">
          <label for="specifiProduct">product</label>
          <input
            type="text"
            id="specifiProduct"
            name="specifiProduct"
            required
          />
        </div>
        <div class="search_button">
          <button>search</button>
        </div>
      </div>
      <div class="product_details">
        <div class="header">
          <h4><i class="fas fa-qrcode"></i> Product Details</h4>
          <hr />
        </div>
        <div class="table">
          <Table/>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data: () => ({
    warehouses: [
      { id: 1, name: "warehouse1" },
      { id: 2, name: "warehouse2" }
    ],
    types: [
      { id: 1, warehouse_id: 1, name: "type1" },
      { id: 2, warehouse_id: 1, name: "type2" },
      { id: 3, warehouse_id: 1, name: "type3" },
      { id: 4, warehouse_id: 2, name: "type4" },
      { id: 5, warehouse_id: 2, name: "type5" },
      { id: 6, warehouse_id: 2, name: "type6" }
    ],
    selectedWarehouse: "",
    selectedType: "",
    picked: ""
  }),
  // mounted: function() {
  //   this.selectedWarehouse = 0;
  // },
  computed: {
    filteredTypes: function() {
      return this.types.filter(function(el) {
        return el.warehouse_id === this.selectedWarehouse;
      }, this);
    }
    // showProductInput: function () {
    //   let isShow = (!this.selectedWarehouse != '') ? true : false
    //   return isShow;
    // }
  }
};
</script>

<style>
section {
  grid-row: 3 / span 1;
  grid-column: span 12;
  margin: 0 10px;
  border-radius: 3px;
  display: grid;
  grid-template-rows: 45px 1fr;
  row-gap: 5px;
  color: #0357a8;
}
h3 {
  grid-row: 1 / span 1;
}
.form_content {
  background-color: #fff;
  grid-row: 2 / span 1;
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  grid-template-rows: repeat(2, 1fr);
}
.basic_information {
  color: #0c3c6b;
  grid-row: 1 / span 1;
  grid-column: 2 / span 10;
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  grid-template-rows: auto auto;
  gap: 0 20px;
}
.basic_information .header {
  grid-column: 1 / span 12;
  grid-row: 1 / span 1;
}
.basic_information .warehouse {
  grid-column: 1 / span 3;
}
.basic_information .warehouse select {
  width: 100%;
  border: 0;
  background-color: #f5f7f9;
  padding: 5px;
}
.basic_information .type {
  grid-column: 4 / span 3;
}
.basic_information .type select {
  width: 100%;
  border: 0;
  background-color: #f5f7f9;
  padding: 5px;
}
.basic_information .show_balance {
  grid-column: 7 / span 6;
  align-items: center;
}
.basic_information .product_classification {
  grid-column: 1 / span 4;
}
.basic_information .specifi_product {
  grid-column: 5 / span 5;
}
.basic_information .specifi_product input {
  width: 100%;
  border: 0;
  background-color: #f5f7f9;
  padding: 5px;
}
.basic_information .search_button {
  grid-column: 10 / span 3;
  justify-self: end;
  align-self: end;

}
.basic_information .search_button button {
  background-color: #0c3c6b; /* Green */
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
}
.product_details {
  color: #0c3c6b;
  grid-row: 2 / span 1;
  grid-column: 2 / span 10;
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  grid-template-rows: auto auto;
  gap: 0 20px;
}
.product_details .header {
  grid-column: 1 / span 12;
  grid-row: 1 / span 1;
}
.product_details .table {
    grid-column: 1 / span 12;
  grid-row: 2 / span 1;
}
</style>
