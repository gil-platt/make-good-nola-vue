<template>
  <div role="navigation" id="header-bar">
    <div class="top-menu" aria-labelledby="Site links and social media links">
      <span class="site-links" aria-labelledby="Site links">
        <a 
          :class="currentPage === item.page ? 'current-link' : 'site-link'" 
          v-for="item in headerItems" 
          :key="item.page"
          @click="setCurrentPage(item.page)"
        >
          {{ item.page }}
        </a>
      </span>
      <div class="donor-social-navigation">
        <span class="social-media-links" aria-labelledby="Social media links">
          <a
            class="social-media-link"
            v-for="item in socialMediaItems"
            :key="item.brand"
          >
            <font-awesome-icon :icon="`fa-brands fa-${item.brand}`" />
          </a>
        </span>
        <a role="button">
          <button
            type="button"
            class="donor-button"
            aria-label="link to the donation page"
          >
            Become a donor
          </button>
        </a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HeaderBar",
  data() {
    return {
      currentPage: "Home",
      headerItems: [
        {
          page: "Home",
          link: ""
        },
        {
          page: "About",
          link: ""
        },
        {
          page: "Links",
          link: ""
        },
        {
          page: "Makers' Fests",
          link: ""
        }
      ],
      socialMediaItems: [
        {
          brand: "facebook",
          link: ""
        },
        {
          brand: "instagram",
          link: ""
        }
      ]
    };
  },
  methods: {
    setCurrentPage(page) {
      this.currentPage = page;
      console.log(this.currentPage)
    }
  }
};
</script>

<style lang="scss" scoped>
@import './header-bar.scss';
</style>

