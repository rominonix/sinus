<template>
  <div class="checkout">
    <div class="form">
      <h1>Checkout</h1>
      <h1 class="tag">Delivery details</h1>
      <form class="checkout-form">
        <label class="name" for="name">Name</label>
        <input class="input-name" type="text" />
        <img class="name-line" src="../assets/line.svg" alt="" />
        <label class="lastname" for="lastname">Lastname</label>
        <input class="input-lastname" type="text" />
        <img class="lastname-line" src="../assets/line.svg" alt="" />
        <label class="address" for="address">Address</label>
        <input class="input-address" type="text" />
        <img class="address-line" src="../assets/address-line.svg" alt="" />
        <label class="zip" for="zip">Zip</label>
        <input class="input-zip" type="text" />
        <img class="zip-line" src="../assets/line.svg" alt="" />
        <label class="city" for="city">City</label>
        <input class="input-city" type="text" />
        <img class="city-line" src="../assets/line.svg" alt="" />
        <label class="email" for="email">Email</label>
        <input class="input-email" type="text" />
        <img class="email-line" src="../assets/line.svg" alt="" />
        <label class="phone" for="phone">Telephone number</label>
        <input class="input-phone" type="text" />
        <img class="phone-line" src="../assets/line.svg" alt="" />
      </form>
      <h1 class="tag">choose delivery options</h1>
      <div class="options">
          <div class="delivery-post">
              <div class="my-checkbox"></div>
              <p>Delivery by post</p>
          </div>

          <div class="pickup-store">
              <div class="my-checkbox"></div>
              <p>Store pickup</p>
          </div>
      </div>

      <div class="buttons-checkout">
        <button>go back</button>
        <button>continue</button>
      </div>
    </div>

    <div class="order">
      <div class="item">
        <div
          class="items-container"
          v-for="item in drawItems"
          v-bind:key="item.id"
        >
          <div class="product-img">
            <img :src="require(`../assets/${item.imgFile}`)" />
          </div>
          <div class="item-desc">
            <h3 class="product-title">{{ item.title }}</h3>
            <p class="item-details">Color: {{ item.color }}</p>
            <p class="item-details">
              Quantity:
              <button class="minus" @click="removeItem(item)">-</button>
              <!-- {{ item.quantity }} -->
              {{ item.quantity }}
              <button class="plus" @click="addItem(item)">+</button>
            </p>
            <!-- <p class="item-details">{{item.size}}</p> -->
            <p class="item-details">Price: {{ item.price }} SEK</p>
            <img
              class="trash"
              src="../assets/trash.svg"
              @click="deleteItem(item)"
            />
          </div>
        </div>

        <!-- <div class="img-product">Img Product</div>
        <div class="item-info">
          <p class="name-product"></p>
          <p>quantity</p>
          <p>size</p>
          <p>PRICE</p>
          <img src="../assets/trash.svg" alt="" />
        </div> -->
      </div>
      <div class="total">TOTAL CART</div>
      <p class="vat">Including VAT</p>
    </div>
  </div>
</template>

<script>

export default {
    name: 'Checkout',

    computed: {
    drawItems() {
      let cart = this.$store.state.cart;
      // let page_size = 3;
      // let page_number = 1;
      // let pages = this.paginate(cart, page_size, page_number);

      let cartArr = [];

      for (var key in cart) {
        cartArr.push(cart[key]);
      }

      // if (this.nextPage(page_number)) {
      //   pages = this.paginate(cartArr, page_size, page_number);
      // } else if (this.prevPage(page_number)) {
      //   pages = this.paginate(cartArr, page_size, page_number);
      // } else {
      //   pages = this.paginate(cartArr, page_size, page_number);
      // }

      return cartArr;
    },
  }

}
</script>

<style scoped>
/* style form */
h1 {
  text-transform: uppercase;
  font-weight: 400;
  font-size: 1.5rem;
  text-align: justify;
}

p {
    text-align: justify;
}


.tag {
  font-family: "Schoolbell", cursive;
  letter-spacing: 0.2rem;
  padding: 4% 0 8%;
}

button {
  cursor: pointer;
  font-family: Ropa Sans;
  font-size: 18px;
  width: 144px;
  height: 40px;
  background-color: whitesmoke;
  color: #2b2b2b;
  border-style: none;
  box-shadow: -6px 6px #cbe9ef;
  margin: 0rem;
}

button:hover {
  background-color: #2b2b2b;
  color: whitesmoke;
}

.buttons-checkout {
  padding-top: 10%;
  display: flex;
  justify-content: space-around;
}

label {
  font-family: "Ropa Sans", sans-serif;
  text-align: justify;
}

input {
  border-style: none;
  border-radius: 5px;
  font-family: "Ropa Sans", sans-serif;
  font-size: 1rem;
  outline: none;
  background-color: transparent;
}

input:focus {
  border: none;
}

input:active {
  border: none;
}

.checkout {
  padding: 3%;
  margin: 2%;
  display: flex;
  justify-content: space-around;
  background-image: url("../assets/background-checkout.svg");
  background-repeat: no-repeat;
}

.form,
.order {
  margin-top: 2%;
  padding: 3%;
  width: 50%;
}

.order {
  margin: 2%;
  padding: 5%;
  background-color: #f1f1f1;
}

.checkout-form {
  display: grid;
  grid-template-columns: repeat(2, auto);
  grid-template-rows: repeat(12, 1.5rem);
  text-align: justify;
  gap: 5px;
}

.options {
  display: grid;
  grid-template-columns: repeat(2, auto);
  align-content: center;
  align-items: center;
  padding: 1% 5%;
}

.delivery-post, .pickup-store{
    display: flex;
    justify-content: center;
}
.my-checkbox{
    width: 1rem;
    height: 1rem;
    margin-right: 3%;
    background-color:transparent;
    border: solid 2px #2b2b2b;
    box-shadow: -2px 2px #2b2b2b ;
}

.my-checkbox:hover{
 background-color:#F46D69;
}
.my-checkbox:selection{
 background-color:#F46D69;
}



.name {
  grid-column: 1;
  grid-row: 1;
}

.input-name {
  grid-column: 1;
  grid-row: 2;
}

.name-line {
  grid-column: 1;
  grid-row: 3;
}

.lastname {
  grid-column: 2;
  grid-row: 1;
}

.input-lastname {
  grid-column: 2;
  grid-row: 2;
}

.lastname-line {
  grid-column: 2;
  grid-row: 3;
}

.address {
  grid-column: 1/3;
  grid-row: 4;
}

.input-address {
  grid-column: 1/3;
  grid-row: 5;
}

.address-line {
  grid-column: 1/3;
  grid-row: 6;
}

.zip {
  grid-column: 1;
  grid-row: 7;
}

.input-zip {
  grid-column: 1;
  grid-row: 8;
}

.zip-line {
  grid-column: 1;
  grid-row: 9;
}

.city {
  grid-column: 2;
  grid-row: 7;
}

.input-city {
  grid-column: 2;
  grid-row: 8;
}

.city-line {
  grid-column: 2;
  grid-row: 9;
}

.email {
  grid-column: 1;
  grid-row: 10;
}

.input-email {
  grid-column: 1;
  grid-row: 11;
}

.email-line {
  grid-column: 1;
  grid-row: 12;
}

.phone {
  grid-column: 2;
  grid-row: 10;
}

.input-phone {
  grid-column: 2;
  grid-row: 11;
}

.phone-line {
  grid-column: 2;
  grid-row: 12;
}

/* style order items */

.item {
  display: grid;
  grid-template-columns: repeat(2, auto);
  height: 85%;
  text-align: justify;
  margin-bottom: 5%;
}

.total {
  text-align: justify;
  font-size: 2.5rem;
  margin-bottom: 2%;
}

.vat{
    font-size: 1.2rem;
}
</style>