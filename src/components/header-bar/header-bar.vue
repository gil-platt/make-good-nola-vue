<template>
  <div role="navigation" id="navigation-bar" aria-labelledby="Accessibility settings, site links, and social media links">
    <div class="top-menu" aria-labelledby="Site links and social media links">
      <div id="accessibility-wrapper" aria-hidden="true">
        <div class="button-drop-down" aria-labelledby="Dropdown button and dropdown menu content">
          <span id="accessibility-filters" role="button" aria-labelledby="Set fonts and colors for visual assistance">
            Accessibility <font-awesome-icon icon="fa-solid fa-universal-access" aria-hidden="true" />
            <!-- <div class="accessibility-menu" aria-labelledby="Dropdown menu">
              <a role="button">

              </a>
            </div> -->
          </span>
        </div>
      </div>
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
          <span
            class="donor-button"
            aria-label="link to the donation page"
          >
            Become a donor
          </span>
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
      accessibilityMenu: [
        {
          label: "Dyslexia"
        },
        {
          label: "Deuteranomaly"
        },
        {
          label: "Protanomaly"
        },
        {
          label: "Protanopia or Deuteranopia"
        },
        {
          label: "Tritanomaly"
        },
        {
          label: "Tritanopia"
        },
        {
          label: "Monochromacy"
        }
      ],
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
    }
  }
};
</script>

<style lang="scss" scoped>
@import './header-bar.scss';
</style>

