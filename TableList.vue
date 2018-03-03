<template>
    <div class="row">
      <div class="col-md-12">
        <div class="card">
          <paper-table :title="table1.title" :sub-title="table1.subTitle" :data="table1.data" :columns="table1.columns">

          </paper-table>
        </div>
      </div>

    <div>
      <form role="form" class="" @submit.prevent="createProduct()">

             <p> Product Name </p>
             <input type= "text"
             v-model= 'name'
             placeholder = "Enter product name here">

             <p> Price </p>
             <input type= "text"
             v-model= 'price'
             placeholder = "Enter price name here">

             <p> Created At </p>
             <input type= "text"
              v-model= 'createdAt'
             placeholder = "Enter creation date here">

             <p> UpdatedAt </p>
             <input type= "text"
              v-model= 'updatedAt'
             placeholder = "Enter update date here">

           <div>
                 <div style="max-width:400px">
                     <button class="btn btn-primary btn-sm" style="height:50px">Create Product</button>
                 </div>
             </div>
         </form>
         </div>


      <h1>Shopping Cart</h1>
 <div class="shopping-cart">
   <div class="product">
     <div class="product-image">
       <img src="https://images-na.ssl-images-amazon.com/images/I/714v5CiuL9L._UX395_.jpg">
     </div>
     <div class="product-details">
       <div class="product-title">AirForce</div>
       <p class="product-description">A classic.</p>
     </div>
     <div class="product-price">$80</div>
     <div class="product-quantity">
       <input type="number" value="2" min="1">
     </div>
     <div class="product-removal">
       <button class="remove-product">
         Remove
       </button>
     </div>

   </div>

   <div class="product">
     <div class="product-image">
       <img src="https://images3.nike.com/is/image/DotCom/PDP_HERO_M/M7650_102_C_PREM/converse-chuck-taylor-all-star-high-top-unisex-shoe.jpg">
     </div>
     <div class="product-details">
       <div class="product-title">Converse</div>
       <p class="product-description">Comfy, casual and cool.</p>
     </div>
     <div class="product-price">$50</div>
     <div class="product-quantity">
       <input type="number" value="1" min="1">
     </div>
     <div class="product-removal">
       <button class="remove-product">
         Remove
       </button>
     </div>

   </div>

   <div class="totals">
     <div class="totals-item">
       <label>Subtotal</label>
       <div class="totals-value" id="cart-subtotal">$130</div>
     </div>
     <div class="totals-item">
       <label>Tax (5%)</label>
       <div class="totals-value" id="cart-tax">$4.50</div>
     </div>
     <div class="totals-item">
       <label>Shipping</label>
       <div class="totals-value" id="cart-shipping">$15.50</div>
     </div>
     <div class="totals-item totals-item-total">
       <label>Grand Total</label>
       <div class="totals-value" id="cart-total">$150</div>
     </div>
   </div>

       <button class="checkout">Checkout</button>
 </div>
    </div>
</template>
<script>
  import axios from 'axios'
  import PaperTable from 'components/UIComponents/PaperTable.vue'
  const tableColumns = ['Id', 'Name', 'Price', 'CreatedAt', 'UpdatedAt', 'SellerName']
  const tableData = [{
    id: 1,
    name: 'AirForce',
    price: '$80',
    createdat: '15/2/2018',
    updatedat: '16/2/2018',
    sellername: 'Sh'
  },
  {
    id: 2,
    name: 'Converse',
    price: '$50',
    createdat: '15/2/2018',
    updatedat: '16/2/2018',
    sellername: 'Sh'
  }]

  export default {
    components: {
      PaperTable
    },
    data () {
      return {
        table1: {
          title: 'Kool Kicks',
          subTitle: 'Product list created by Shorouk',
          columns: [...tableColumns],
          data: [...tableData]
        },
        name: '',
        price: '',
        createdAt: '',
        updatedAt: ''
      }
    },
    methods: {

      createProduct: function () {
        console.log(this.name)
        console.log(this.price)
        console.log(this.createdAt)
        console.log(this.updatedAt)
        axios.post('http://localhost:3000/api/product/createProduct',
          {
            'name': this.name,
            'price': this.price,
            'createdAt': this.createdAt,
            'updatedAt': this.updatedAt
          })
  .then(response => {})
  .catch(e => {

  })
      }
    }
}
</script>
<style>

</style>
