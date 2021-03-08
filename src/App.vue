<template>
  <div id="app">
    <h1>BÀI KIỂM TRA EGANY</h1><img src="https://ci5.googleusercontent.com/proxy/Rn3UJ4AoovTEQTtgH2aW0mhkwQzxO9efSODhw2PH6h9U2K1ep55EByQrcaNsSAn6UagGS9GrWa3qd8kVhMAsyaPsOM41rEoj9dsmwW14vOf0IBGxrXBJHD9r5jcmzyjs=s0-d-e1-ft#https://theme.hstatic.net/1000181505/1000641895/14/egany_logo_light.png?v=126" alt="" srcset="">
    <div>
      <md-field>
        <label>Tìm Kiếm Sản Phẩm</label>
        <md-input md-autogrow v-model="filterProducts"></md-input>
      </md-field>
    </div>
    <md-card v-for="product in findProducts" v-bind:key="product.id">
      <md-card-area>
        <md-card-media>
          <img :src="product.image.src" alt="Products" />
        </md-card-media>

        <md-card-header>
          <div class="md-title">{{ product.title }}</div>
          <div class="md-subhead">{{ product.vendor }}</div>
        </md-card-header>

        <md-card-content>
          {{ product.tags }}
        </md-card-content>

        <md-card-content
          v-for="variant in product.variants"
          v-bind:key="variant.id"
        >
          <div>Giá : {{ variant.price }}</div>
          <div v-if="variant.inventory_quantity > 0">
            Tình Trạng thái kho hàng : {{ variant.inventory_quantity }}
          </div>
          <div v-else>Hết Hàng</div>
        </md-card-content>
      </md-card-area>

      <md-card-actions md-alignment="left">
        <md-button class="md-accent">Yêu Thích</md-button>
        <md-button class="md-primary">Mua Sản Phẩm</md-button>
      </md-card-actions>
    </md-card>
  </div>
</template>

<script>
export default {
  name: "App",
  computed: {
    findProducts() {
      return this.products.filter((product) => {
        return product.title
          .toLowerCase()
          .includes(this.filterProducts.toLowerCase());
      });
    },
  },
  data() {
    return {
      filterProducts: "",
      products: [
        {
          handle: "ega-botconn",
          id: 1,
          title: "egaBotConn",
          vendor: "EGANY",
          tags:
            "platform__cross-platform, type__apps, doc__ega-botconn, demo__https://egany.com",
          image: {
            id: 11,
            src: "https://picsum.photos/id/14/600",
          },
          variants: [
            {
              id: 111,
              sku: "egabotconn",
              price: "0",
              compare_at_price: "0",
              inventory_management: null,
              inventory_policy: "deny",
              inventory_quantity: 1,
            },
          ],
        },
        {
          handle: "ega-shop",
          id: 2,
          title: "egaShop",
          vendor: "EGANY",
          tags:
            "platform__haravan_sapo_cross-platform, type__apps, doc__ega-shop, demo__https://egany.com",
          image: {
            id: 22,
            src: "https://picsum.photos/id/15/600",
          },
          variants: [
            {
              id: 222,
              sku: "egashop",
              price: "149000",
              compare_at_price: "199000",
              inventory_management: null,
              inventory_policy: "deny",
              inventory_quantity: 1,
            },
          ],
        },
        {
          handle: "ega-countdown",
          id: 3,
          title: "egaCountdown",
          vendor: "EGANY",
          tags:
            "platform__haravan_cross-platform, type__apps, doc__ega-countdown, demo__https://egany.com",
          image: {
            id: 33,
            src: "https://picsum.photos/id/16/600",
          },
          variants: [
            {
              id: 333,
              sku: "egabotconn",
              price: "99000",
              compare_at_price: "149000",
              inventory_management: "manual",
              inventory_policy: "allow",
              inventory_quantity: 0,
            },
          ],
        },
        {
          handle: "ega-salebox",
          id: 4,
          title: "egaSaleBox",
          vendor: "EGANY",
          tags:
            "platform__haravan_cross-platform, type__apps, doc__ega-salebox, demo__https://egany.com",
          image: {
            id: 44,
            src: "https://picsum.photos/id/14/600",
          },
          variants: [
            {
              id: 444,
              sku: "egasalebox",
              price: "99000",
              compare_at_price: "149000",
              inventory_management: "manual",
              inventory_policy: "allow",
              inventory_quantity: -1,
            },
          ],
        },
        {
          handle: "ega-cro",
          id: 5,
          title: "egaCRO",
          vendor: "EGANY",
          tags:
            "platform__haravan_cross-platform_sapo, type__apps, doc__ega-salebox, demo__https://egany.com",
          image: {
            id: 55,
            src: "https://picsum.photos/id/14/600",
          },
          variants: [
            {
              id: 555,
              sku: "egasalebox",
              price: "99000",
              compare_at_price: "149000",
              inventory_management: null,
              inventory_policy: "deny",
              inventory_quantity: 10,
            },
          ],
        },
      ],
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.md-card {
  width: 320px;
  margin: 4px;
  display: inline-block;
  vertical-align: top;
}


 

</style>
