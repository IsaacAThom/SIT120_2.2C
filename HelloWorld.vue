<script setup>
import { reactive } from 'vue'
import { ref } from 'vue'
// List of products in the system at this time
  // Dress image sourced from https://iconscout.com/icon/womans-52
  // Shirt image sourced from https://iconscout.com/icon/tshirt-90
  // Pants image sourced from https://iconscout.com/icon/womans-54
const productStock = reactive([
        { 
          productName: 'Slim Dress',
          size: ['S', 'M'],
          color: ['blue', 'red'],
          type: 'dress',
          img: "https://cdn.iconscout.com/icon/free/png-512/free-womans-52-455230.png?f=avif&w=256",
          price: 22
        },
        {
          productName: 'Baggy Dress',
          size: ['Xs', 'M', 'L'],
          color: ['red', 'yellow', 'blue'],
          type: 'dress',
          img: "https://cdn.iconscout.com/icon/free/png-512/free-womans-52-455230.png?f=avif&w=256",
          price: 34
        },
        {
          productName: 'Revealing Dress',
          size: ['S', 'L'],
          color: ['yellow','green'],
          type: 'dress',
          img: "https://cdn.iconscout.com/icon/free/png-512/free-womans-52-455230.png?f=avif&w=256",
          price: 15
        },
        {
          productName: 'Fitted Dress',
          size: ['Xs','S'],
          color: ['red'],
          type: 'dress',
          img: "https://cdn.iconscout.com/icon/free/png-512/free-womans-52-455230.png?f=avif&w=256",
          price: 47
        },
        {
          productName: 'Crop Shirt',
          size: ['M','Xl'],
          color: ['yellow','red'],
          type: 'shirt',
          img: "https://cdn.iconscout.com/icon/free/png-512/free-tshirt-90-455210.png?f=avif&w=256",
          price: 15
        },
        {
          productName: 'Loose Shirt',
          size: ['S','M','L'],
          color: ['blue','green'],
          type: 'shirt',
          img: "https://cdn.iconscout.com/icon/free/png-512/free-tshirt-90-455210.png?f=avif&w=256",
          price: 25
        },
        {
          productName: 'Tight Shirt',
          size: ['Xs','M'],
          color: ['red'],
          type: 'shirt',
          img: "https://cdn.iconscout.com/icon/free/png-512/free-tshirt-90-455210.png?f=avif&w=256",
          price: 31
        },
        {
          productName: 'Asymmetrical Shirt',
          size: ['S','L','Xl'],
          color: ['green','yellow','red'],
          type: 'shirt',
          img: "https://cdn.iconscout.com/icon/free/png-512/free-tshirt-90-455210.png?f=avif&w=256",
          price: 48
        },
        {
          productName: 'Skinny Jeans',
          size: ['Xs','S','M'],
          color: ['blue'],
          type: 'pants',
          img: "https://cdn.iconscout.com/icon/free/png-512/free-womans-54-455232.png?f=avif&w=256",
          price: 39
        },
        {
          productName: 'Baggy Pants',
          size: ['L','Xl'],
          color: ['yellow','green','red'],
          type: 'pants',
          img: "https://cdn.iconscout.com/icon/free/png-512/free-womans-54-455232.png?f=avif&w=256",
          price: 16
        },
        {
          productName: 'Culottes',
          size: ['Xs','M','L'],
          color: ['red','blue'],
          type: 'pants',
          img: "https://cdn.iconscout.com/icon/free/png-512/free-womans-54-455232.png?f=avif&w=256",
          price: 24
        }
      ])
// Blank arrays for storing filtered colours, sizes, and styles
const checkedSizes = ref([])
const checkedColors = ref([])
const checkedTypes = ref([])
// Min and Maximum price, set to 0 and 50 by default
const minPrice = ref(0)
const maxPrice = ref(50)
// Visibility toggle, false at launch
const visible1 = ref(false)
const visible2 = ref(false)
</script>

<template>
  <header>
    <h1>Fashion Central</h1>
  </header>
  
  <!-- Navigates nowhere at this time, and stores cart -->
  <nav>
    <a href="#home">Home</a>
    <a href="#sale">Shop Now</a>
    <a href="#contact">Contact</a>
    <button @click="visible2 = !visible2">Cart</button>
  </nav>

  <main>
    <!-- Button for toggling the filtering menu -->
    <button @click="visible1 = !visible1">Refine</button>
    <div class="slideout" v-if="visible1">
      <button @click="visible1 = !visible1" id="exit">X</button><h3>Filter</h3>
      <!-- Checkboxes which filter by item type -->
      <div class="item">
        <h4>Style</h4>
        <input type="checkbox" id="dress" value="dress" v-model="checkedTypes">
        <label for="dress">Dress</label>
        <input type="checkbox" id="shirt" value="shirt" v-model="checkedTypes">
        <label for="shirt">Shirt</label>
        <input type="checkbox" id="pants" value="pants" v-model="checkedTypes">
        <label for="pants">Pants</label>
      </div>
      <!-- Checkboxes which filter items by size-->
      <div class="item">
        <h4>Size</h4>
        <input type="checkbox" id="x-small" value="Xs" v-model="checkedSizes">
        <label for="x-small">XS</label>
        <input type="checkbox" id="small" value="S" v-model="checkedSizes">
        <label for="small">S</label>
        <input type="checkbox" id="medium" value="M" v-model="checkedSizes">
        <label for="medium">M</label>
        <input type="checkbox" id="large" value="L" v-model="checkedSizes">
        <label for="large">L</label>
        <input type="checkbox" id="x-large" value="Xl" v-model="checkedSizes">
        <label for="x-large">XL</label>
      </div>
      <!-- Checkboxes which filter items by colour -->
      <div class="item">
        <h4>Colour</h4>
        <input type="checkbox" id="red" value="red" v-model="checkedColors">
        <label for="red">Red</label>
        <input type="checkbox" id="blue" value="blue" v-model="checkedColors">
        <label for="blue">Blue</label>
        <input type="checkbox" id="yellow" value="yellow" v-model="checkedColors">
        <label for="yellow">Yellow</label>
        <input type="checkbox" id="green" value="green" v-model="checkedColors">
        <label for="green">Green</label>
      </div>
      <!-- Text boxes to give price range -->
      <div class="item">
        <h4>Price</h4>
        <label for="minprice">Minimum Price</label><br>
        <input type="text" id="minprice" v-model="minPrice"><br>
        <label for="maxprice">Maximum Price</label><br>
        <input type="text" id="maxprice" v-model="maxPrice">
      </div>
      <!-- Clear all filters + reset prices -->
      <button @click="clearArray(checkedColors);clearArray(checkedSizes);clearArray(checkedTypes);minPrice='0';maxPrice='50'">Reset Filter</button>
    </div>
    
    <!-- All/Filtered stock -->
    <div class="stock">
      <div v-for="(value, index) in productStock" :key="index" class="storage">
        <div v-if="compareArrays(value.size,checkedSizes) && compareArrays(value.color,checkedColors) && compareArrays(value.type,checkedTypes)">
          <!-- Price range filter -->
          <div class="stock-item" v-if="value.price >= minPrice && value.price <= maxPrice">
            <img v-bind:src="`${value.img}`">
            <div class="properties">
              <!-- Displays a box for each size an item has -->
              <section v-for="innerValue in value.size" :key="innerValue" class="property">
                <p>{{ innerValue.toUpperCase() }}</p>
              </section>
            </div>
            <div class="properties">
              <!-- Displays a box for each colour an item has -->
              <section v-for="innerValue in value.color" :key="innerValue" class="property" :class="colorClass(innerValue)">
                <p>{{ innerValue.charAt(0).toUpperCase() }}</p>
              </section>
            </div>
            <h3>{{ value.productName }}</h3>
            <h4>${{ value.price }}</h4>
            <button @click="addToCart(value)">Add to Cart</button>
        </div>
        </div>
      </div>
    </div>

    <div class="slideout cart" v-if="visible2">
      <button @click="visible2 = !visible2" id="exit">X</button><h3>Cart</h3>
      <div v-for="(value, index) in addedCart" :key="index" class="item">
        <button @click="removeFromCart(index)" id="remove">X</button>
        <h4>{{ value.productName }} ${{ value.price }}</h4>
      </div>
      <div v-if="tallyCartPrice(addedCart) !== 0">
        <p><b>Subtotal:</b> ${{ tallyCartPrice(addedCart) }}</p>
      </div>
      <div v-else>
        <p>Your cart is empty!</p>
      </div>
    </div>
    
  </main>

  <footer>
    &copy; 2023 Fashion Central. All rights reserved.
  </footer>

</template>

<script type="module">
export default {
  data() {
    return {
      addedCart: []
    }
  },
  methods: {
    // Comparing the information in productStock to the information from the filter
    compareArrays(array1, array2) {
      let source = array1.toString();
      let check = 0;
      let match = '';
      if (array2.length > 0) {
        for (let i = 0; i < array2.length; i++) {
          // defines match as whatever value is at i index in the filter
          match = array2[i].toString();
          // if match is found in the stock array, check = 1
          if (source.includes(match)) {
            check = 1;
          }
        }
        // if, after searching, the filter was not found in the stock array, it will return as false
        if (check > 0) return true;
        else return false;
      }
      // if filter is empty, return true
      return true;
    },
    // Adds a class to an element based on the value of it, used to change the colours of the colour boxes
    colorClass(value) {
      if (value == "red") {
        return 'red';
      } else if (value == "blue") {
        return 'blue';
      } else if (value == "yellow") {
        return 'yellow';
      } else if (value == "green") {
        return 'green';
      }
    },
    // Add item to cart
    addToCart(array) {
      this.addedCart.push(array);
    },
    // Remove item from cart
    removeFromCart(array) {
      this.addedCart.splice(array, 1);
    },
    // Add up the prices of all cart items
    tallyCartPrice(array) {
      return array.reduce((acc, item) => acc + item.price, 0);
    },
    // Delete data from erray
    clearArray(array) {
      while (array.length > 0) {
        array.pop();
      }
    }
  }
}
</script>

<style>
  * {
    box-sizing: border-box;
  }

  /* Base Blocks */
  body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    background-color: #f4f4f4;
  }

  header {
    background-color: #333;
    color: white;
    text-align: center;
    padding: 1rem;
  }

  nav {
    background-color: #444;
    color: white;
    padding: 0.5rem;
    text-align: center;
  }

  nav a {
    color: white;
    text-decoration: none;
    margin-right: 1rem;
  }

  main {
    padding: 2rem;
    background-color: #e8e8e8;
  }

  footer {
    background-color: #333;
    color: white;
    text-align: center;
    padding: 1rem;
  }

  /* CSS for the filter search and cart */
  .slideout {
    background: white;
    color: #333;
    position: fixed;
    top: 0;
    width: 30vw;
    left: 0;
    height: 100%;
    text-align: center;
    padding-top: 25px;
    padding-bottom: 35px;
    box-shadow: 3px 3px 15px 0px #444;
  }

  .slideout .item {
    overflow: hidden;
    border-top: 2px solid #444;
    border-bottom: 2px solid #444;
    margin-bottom: 20px;
    padding-bottom: 20px;
    text-align: center;
  }

  /* Exit buttons */
  .slideout button#exit {
    position: absolute;
    top: 44px;
    right: 15px;
  }
  /* Specific to the cart */
  .cart {
    left: inherit;
    right: 0;
  }

  /* Remove item button */
  .slideout button#remove {
    float: right;
    margin-right: 15px;
    margin-top: 15px;
  }

  /* CSS for the overall items */
  /* Box containing all items */
  .stock {
    padding: 2px;
    overflow: hidden;
  }
  /* Box for column purposes */
  .storage {
    width: 25%;
    float: left;
  }
  /* Box with the actual content */
  .stock-item {
    border: 1px solid #333;
    border-radius: 25px;
    padding: 10px;
    margin: 15px;
    text-align: center;
    background-color: white;
    box-shadow: 3px 3px 6px 0px #444;
  }
  /* Container for all size/colour boxes */
  .properties {
    overflow: hidden;
    text-align: center;
    margin-left: auto;
    margin-right: auto;
    width: fit-content;
  }
  /* Size/Colour boxes */
  .property {
    padding: 5px;
    width: 30px;
    height: 30px;
    border: 1px solid black;
    border-radius: 5px;
    float: left;
    display: table;
    margin: 5px;
  }

  .property p {
    display: table-cell;
    vertical-align: middle;
    text-align: center;
    font-size: 12px;
    color: #111;
  }

  /* Colour Boxes */
  .red {
    background: #f97171;
  }

  .yellow {
    background: #fae875;
  }

  .blue {
    background: #90b7fe;
  }

  .green {
    background: #97e497;
  }

/* On screens smaller than 1400px */
@media screen and (max-width: 1400px) {
  .storage {
    width: 33.3333%;
  }
}
/* On screens smaller than 800px */
@media screen and (max-width: 800px) {
  .storage {
    width: 50%;
  }
  .slideout {
    width: 100%;
  }
}
</style>
