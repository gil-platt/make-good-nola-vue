<template>
  <div
    role="navigation"
    id="navigation-bar"
    aria-labelledby="Accessibility settings, site links, and social media links"
  >
    <div class="top-menu" aria-labelledby="Site links and social media links">
      <div id="accessibility-wrapper" aria-hidden="true">
        <div
          class="button-drop-down"
          aria-labelledby="Dropdown button and dropdown menu content"
        >
          <span
            id="accessibility-filters"
            role="button"
            aria-labelledby="Set fonts and colors for visual assistance"
            ref="menu"
            @click="accessibilityMenuOpen = !accessibilityMenuOpen"
          >
            Accessibility
            <font-awesome-icon
              icon="fa-solid fa-universal-access"
              aria-hidden="true"
            />
            <font-awesome-icon icon="fas fa-caret-down" />
            <div
              class="accessibility-menu"
              aria-labelledby="Dropdown menu"
              v-show="accessibilityMenuOpen"
            >
              <a
                role="button"
                :aria-label="item.ariaLabel"
                class="accessibility-menu-item"
                v-for="item in accessibilityMenu"
                :key="item.label"
              >
                {{ item.label }}
              </a>
            </div>
          </span>
        </div>
      </div>
      <div
        id="mobile-styles"
        aria-labelledby="A container to style the navigation menu for mobile users. Disregard this message if you are a desktop user."
        @click="setMobileMenuOpen()"
      >
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
          <a class="donor-link" role="button">
            <span
              class="donor-button"
              data-alttext="Donate"
              aria-label="link to the donation page"
            >
              <span>Become a donor</span>
            </span>
          </a>
        </div>
      </div>
      <div
        id="mobile-menu"
        v-show="mobileMenuOpen"
        aria-placeholder="Mobile site menu"
      >
        <a
          :class="
            currentPage === item.page
              ? 'current-mobile-link'
              : 'mobile-menu-link'
          "
          v-for="item in headerItems"
          :key="item.page"
          @click="setCurrentPage(item.page)"
        >
          {{ item.page }}
        </a>
        <a
          class="mobile-menu-link"
          v-for="item in socialMediaItems"
          :key="item.brand"
        >
          {{ item.brand }}
        </a>
        <a class="mobile-menu-link"> Become a Donor </a>
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
      accessibilityMenuOpen: false,
      mobileMenuOpen: false,
      accessibilityMenu: [
        {
          label: "Dyslexia",
          ariaLabel: "",
        },
        {
          label: "Deuteranomaly",
          ariaLabel: "",
        },
        {
          ariaLabel: "",
          label: "Protanomaly",
        },
        {
          ariaLabel: "",
          label: "Protanopia",
        },
        {
          ariaLabel: "",
          label: "Deuteranopia",
        },
        {
          ariaLabel: "",
          label: "Tritanomaly",
        },
        {
          ariaLabel: "",
          label: "Tritanopia",
        },
        {
          ariaLabel: "",
          label: "Monochromacy",
        },
      ],
      headerItems: [
        {
          page: "Home",
          link: "",
        },
        {
          page: "About",
          link: "",
        },
        {
          page: "Links",
          link: "",
        },
        {
          page: "Makers' Fests",
          link: "",
        },
      ],
      socialMediaItems: [
        {
          brand: "facebook",
          link: "",
        },
        {
          brand: "instagram",
          link: "",
        },
      ],
    };
  },
  methods: {
    setCurrentPage(page) {
      this.currentPage = page;
    },
    setAccessibilityMenuOpen() {
      this.accessibilityMenuOpen = !this.accessibilityMenuOpen;
    },
    setMobileMenuOpen() {
      window.visualViewport.width >= 375 && window.visualViewport.width <= 677
        ? (this.mobileMenuOpen = !this.mobileMenuOpen)
        : null;
    },
  },
};
</script>

<style lang="scss" scoped>
@import "./header-bar.scss";
</style>

