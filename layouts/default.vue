<template>
  <div id="app">
    <div class="wrapper">
      <nav id="sidenav-main" class="navbar navbar-sidebar" background-color="vue" short-title="Argon" title="Argon">
        <div class="container-fluid" style="padding-left:0px;">
          <ul class="navbar-nav">
            <li class="nav-item" v-for="(item, i) in listUrl" :key="i" :to="item.to" router exact>
              <nuxt-link class="nav-link" :to="item.to">{{ item.title }}</nuxt-link>
            </li>
            <!-- <li class="nav-item">
              <a href="/icons" class="nav-link"><i class="ni ni-planet text-blue"></i><span class="nav-link-text">Icons</span></a>
            </li>
            <li class="nav-item">
              <a href="/maps" class="nav-link"><i class="ni ni-pin-3 text-orange"></i><span class="nav-link-text">Maps</span></a>
            </li>
            <li class="nav-item">
              <a href="/profile" class="nav-link"><i class="ni ni-single-02 text-yellow"></i><span class="nav-link-text">User Profile</span></a>
            </li>
            <li class="nav-item">
              <a href="/tables" class="nav-link"><i class="ni ni-bullet-list-67 text-red"></i><span class="nav-link-text">Tables</span></a>
            </li>
            <li class="nav-item">
              <a href="/login" class="nav-link"><i class="ni ni-key-25 text-info"></i><span class="nav-link-text">Login</span></a>
            </li>
            <li class="nav-item">
              <a href="/register" class="nav-link"><i class="ni ni-circle-08 text-pink"></i><span class="nav-link-text">Register</span></a>
            </li> -->
          </ul>
          <!-- <hr class="my-3">
          <h6 class="navbar-heading text-muted">Documentation</h6>
          <ul class="navbar-nav mb-md-3">
            <li class="nav-item">
              <a href="https://demos.creative-tim.com/vue-argon-dashboard/documentation" class="nav-link"><i class="ni ni-spaceship"></i> Getting started </a>
            </li>
            <li class="nav-item">
              <a href="https://demos.creative-tim.com/vue-argon-dashboard/documentation/foundation/colors.html" class="nav-link"><i class="ni ni-palette"></i> Foundation </a>
            </li>
            <li class="nav-item">
              <a href="https://demos.creative-tim.com/vue-argon-dashboard/documentation/components/alerts.html" class="nav-link"><i class="ni ni-ui-04"></i> Components </a>
              </li>
          </ul> -->
        </div>
      </nav>
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
    background-color: #fff !important;
  }

  .navbar-nav {
    width: 100%;
  }
  
  .navbar-nav .nav-link {
    padding-left: 1rem;
    padding-right: 1rem;
    font-size: 0.9rem;
  }

  .nuxt-link-exact-active {
    top: 0.25rem;
    bottom: 0.25rem;
    left: 0;
    right: auto;
    border-left: 3px solid #5e72e4;
    background: rgba(0,0,0,0.04);
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
