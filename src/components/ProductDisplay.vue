<template>
  <div class="container">
    <div v-if="isLoading" class="card">
      <div class="product-container load">
        <div class="load-thumbnail"></div>
        <div class="load-details">
          <div class="load-text-details"></div>
          <div class="load-details-action"></div>
        </div>
      </div>
    </div>
    <div
      v-else
      :class="{
        container: true,
        'bg-unavailable': !isProductAvailable,
        'bg-men-color':
          products.data && products.data.category === 'men\'s clothing',
        'bg-women-color':
          products.data && products.data.category === 'women\'s clothing',
      }"
    >
      <div class="overlay">
        <img src="../assets/images/bg-shape.svg" alt="bg-image" />
      </div>
      <div class="card">
        <div v-if="!isProductAvailable" class="product-unavailable-container">
          <div class="overlay">
            <img
              src="../assets/images/bg-unavailable-product.svg"
              alt="bg-unvailable-product"
            />
          </div>
          <div class="product-text">
            <p>This product is Unvailable to show</p>
            <div class="cta">
              <button class="cta-next" type="button" @click="getProductbyId()">
                Next Product
              </button>
            </div>
          </div>
        </div>
        <div v-else class="product-container">
          <div class="product-image">
            <img :src="products.data.image" alt="image-product" />
          </div>
          <div class="product-text">
            <div class="details">
              <h4
                :class="{
                  title: true,
                  'font-men': products.data.category === 'men\'s clothing',
                  'font-women': products.data.category === 'women\'s clothing',
                }"
              >
                {{ products.data.title }}
              </h4>
              <div class="sub-title">
                <span>{{ products.data.category }}</span>
                <div class="rating">
                  <span>{{ products.data.rating.rate }}/5 </span>
                  <div class="rating">
                    <span
                      :class="{
                        circle: true,
                        'bg-navy': products.data.category === 'men\'s clothing',
                        'bg-magenta':
                          products.data.category === 'women\'s clothing',
                      }"
                    ></span>
                    <span
                      :class="{
                        circle: true,
                        'bg-navy': products.data.category === 'men\'s clothing',
                        'bg-magenta':
                          products.data.category === 'women\'s clothing',
                      }"
                    ></span>
                    <span
                      :class="{
                        circle: true,
                        'bg-navy': products.data.category === 'men\'s clothing',
                        'bg-magenta':
                          products.data.category === 'women\'s clothing',
                      }"
                    ></span>
                    <span
                      :class="{
                        circle: true,
                        'bg-navy': products.data.category === 'men\'s clothing',
                        'bg-magenta':
                          products.data.category === 'women\'s clothing',
                      }"
                    ></span>
                    <span
                      :class="{
                        circle: true,
                        'bg-navy': products.data.category === 'men\'s clothing',
                        'bg-magenta':
                          products.data.category === 'women\'s clothing',
                      }"
                    ></span>
                  </div>
                </div>
              </div>
              <div class="description">
                <p>
                  {{ products.data.description }}
                </p>
              </div>
            </div>
            <div class="action">
              <span
                :class="{
                  price: true,
                  'font-men': products.data.category === 'men\'s clothing',
                  'font-women': products.data.category === 'women\'s clothing',
                }"
                >$ {{ products.data.price }}</span
              >
              <div class="cta">
                <button
                  :class="{
                    'cta-buy': true,
                    'bg-navy': products.data.category === 'men\'s clothing',
                    'bg-magenta':
                      products.data.category === 'women\'s clothing',
                  }"
                  type="button"
                >
                  Buy Now
                </button>
                <button
                  :class="{
                    'cta-next': true,
                    'font-men border-men':
                      products.data.category === 'men\'s clothing',
                    'font-women border-women':
                      products.data.category === 'women\'s clothing',
                  }"
                  type="button"
                  @click="getProductbyId()"
                >
                  Next Product
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProductDisplay",
  data() {
    return {
      isLoading: false,
      products: {},
      index: 0,
      isProductAvailable: false,
    };
  },
  methods: {
    async getData() {
      const res = await fetch(
        `https://fakestoreapi.com/products/${this.index}`
      );
      const result = await res.json();
      return result;
    },

    async getProductbyId() {
      this.isLoading = true;

      if (this.index !== 20) {
        this.index++;
      } else {
        this.index = 1;
      }

      let data = await this.getData();
      if (
        data.category === "men's clothing" ||
        data.category === "women's clothing"
      ) {
        this.products = { data };
        // console.log(data);
        this.isProductAvailable = true;
      } else {
        // console.log(data);
        this.isProductAvailable = false;
      }
      this.isLoading = false;
    },
  },
  mounted() {
    this.getProductbyId();
    // this.getData();
  },
};
</script>

<style>
@import "../assets/style/page.css";
</style>
