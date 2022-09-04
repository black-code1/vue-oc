<template>
  <div id="app" class="app">
    <h1>{{ restaurantName }}</h1>
    <p className="description">
      Bienvenue dans notre café {{ restaurantName }} ! Nous sommes réputés pour notre
      pain et nos merveilleuses pâtisseries. Faites vous plaisir dès le matin
      ou avec un goûter réconfortant. Mais attention, vous verrez qu'il est
      difficile de s'arrêter.
    </p>

    <section class="menu">
      <h2>Menu</h2>
      <MenuItem
          v-for="menuItem in simpleMenu"
          @add-items-to-cart="addToShoppingCart"
          :name="menuItem.name"
          :image="menuItem.image"
          :price="menuItem.price"
          :quantity="menuItem.quantity"
          :inStock="menuItem.inStock"
          :key="menuItem.name"
      />
    </section>

    <aside class="shopping-cart">
      <h2>Panier d'achat: {{ shoppingCart }} articles</h2>
    </aside>

    <footer class="footer">
      <p>{{ copyright }}</p>
    </footer>
  </div>
</template>

<script>

import MenuItem from "@/components/MenuItem.vue";
import {mapGetters, mapState} from "vuex";

export default {
  name: 'HomeView',
  components: {MenuItem},
  computed: {
    ...mapGetters({
      copyright: "copyright"
    }),
    ...mapState({
      restaurantName: "restaurantName",
      shoppingCart: "shoppingCart",
      simpleMenu: "simpleMenu"
    })
  },
  methods: {
    addToShoppingCart(amount) {
      this.shoppingCart += amount
    }
  }
}
</script>


<style lang="scss">
.description {
  max-width: 960px;
  font-size: 1.2rem;
  margin: 0 auto;
}
.footer {
  font-style: italic;
  text-align: center;
}
.menu {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.shopping-cart {
  position: absolute;
  right: 30px;
  top: 0;
}
</style>
