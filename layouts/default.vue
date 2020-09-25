<template>
  <div id="app">
    <div class="wrapper">
      <nav id="sidenav-main" class="navbar navbar-sidebar" background-color="vue" short-title="Argon" title="Argon">
        <div class="container-fluid" style="padding-left:0px;">
          <ul class="navbar-nav">
            <li class="nav-item" v-for="(item, i) in listUrl" :key="i" :to="item.to" router exact>
              <nuxt-link class="nav-link" :to="item.to">{{ item.title }}</nuxt-link>
            </li>
          </ul>
        </div>
      </nav>
    </div>
    <div class="header">

    </div>
    <div class="content-page">
      <Nuxt />
    </div>
  </div>
</template>
<script>
export default {
  data () {
    console.log(this.$router.currentRoute.path);
    return {
      clipped: true,
      drawer: true,
      fixed: false,
      listUrl: [
        {
          icon: 'mdi-apps',
          title: 'Dashboard',
          to: '/'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Pos',
          to: '/pos'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Goods',
          to: '/ListGoods'
        }
      ],
      miniVariant: true,
      right: true,
      rightDrawer: false,
      title: ''
    }
  },
  computed: {
    header () {
      return this.$t('header')
    },
    availableLocales () {
      return this.$i18n.locales.filter(i => i.code !== this.$i18n.locale)
    }
  }
}
</script>
<style>
.bg-white {
  background-color: #fff !important;
}

@media (min-width: 768px) {
  .navbar-sidebar {
    left: 0;
    border-width: 0 1px 0 0;
    display: block;
    position: fixed;
    top: 0;
    bottom: 0;
    width: 100%;
    max-width: 250px;
    padding-left: 0rem;
    padding-right: 1.5rem;
    overflow-y: auto;
    box-shadow: 0 0 2rem 0 rgba(136, 152, 170, 0.15) !important;
    background-color:#4e73df !important;
  }

  .navbar-nav {
    width: 100%;
  }
  
  .navbar-nav .nav-link {
    padding-left: 1rem;
    padding-right: 1rem;
    font-size: 0.9rem;
        color: #fff;
  }

  .nuxt-link-exact-active {
    top: 0.25rem;
    bottom: 0.25rem;
    left: 0;
    right: auto;
    /* border-left: 3px solid #5e72e4;
       background: rgba(0,0,0,0.04); */
    border-left: 3px solid #fff;
    background: rgba(0, 0, 0, 0.8);
    border-bottom: 0;
    width: 100%;
    color: rgba(0, 0, 0, 0.9);
  }
  /* .page-enter-active, .page-leave-active {
    transition: all 0.5s;
  }
  .page-enter, .page-leave {
    opacity: 0;
    transform: scale();
  } */
}
</style>
