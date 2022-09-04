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
          :addToShoppingCart="addToShoppingCart"
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

export default {
  name: 'HomeView',
  components: {MenuItem},
  data() {
    return {
      address: '18 avenuequantity du Beurre, Paris, France',
      email: 'hello@cafewithavue.bakery',
      phone: '01 88 88 88 88',
      restaurantName: 'La belle vue',
      shoppingCart: 0,
      simpleMenu: [
        {
          name: "Croissant",
          image: {
            source: "/images/croissant.jpg",
            alt: "Un croissant"
          },
          inStock: true,
          quantity: 1,
          price: 2.99
        },
        {
          name: "Baguette de pain",
          image: {
            source: "/images/french-baguette.jpeg",
            alt: "Quatre baguettes de pain"
          },
          inStock: true,
          quantity: 1,
          price: 3.99
        },
        {
          name: "Éclair",
          image: {
            source: "/images/eclair.jpg",
            alt: "Éclair au chocolat"
          },
          inStock: false,
          quantity: 1,
          price: 4.99
        }
      ]
    }
  },
  computed: {
    copyright() {
      const currentYear = new Date().getFullYear()

      return `Copyright ${this.restaurantName} ${currentYear}`
    }
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
