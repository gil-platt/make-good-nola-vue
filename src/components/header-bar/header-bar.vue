<template>
  <nav
    role="navigation"
    id="navigation-bar"
    aria-labelledby="Accessibility settings, site links, and social media links"
  >
    <div class="top-menu" aria-labelledby="Site links and social media links">
      <button
        class="rnd-btn accessibility-drop-down"
        aria-labelledby="Dropdown button and dropdown menu content"
        ref="dropdown"
        role="button"
        @click="setAccessibilityMenuOpen()"
      >
        <span
          id="accessibility-filters"
          role="button"
          aria-labelledby="Set fonts and colors for visual assistance"
        >
          Accessibility
          <font-awesome-icon
            icon="fa-solid fa-universal-access"
            aria-hidden="true"
          />
          <font-awesome-icon icon="fas fa-caret-down" />
          <span
            class="accessibility-menu dropdown-menu"
            aria-labelledby="Dropdown menu"
            v-show="accessibilityMenuOpen"
          >
            <a
              role="button"
              :aria-label="item.ariaLabel"
              class="accessibility-menu-item bord-btm-drop-down-child"
              v-for="item in accessibilityMenu"
              :key="item.label"
            >
              {{ item.label }}
            </a>
          </span>
        </span>
      </button>

      <span class="site-links" aria-labelledby="Site links">
        <a
          href="#"
          :class="
            currentPage === item.page
              ? 'current-link-wrapper'
              : 'site-link-wrapper'
          "
          v-for="item in headerItems"
          :key="item.page"
          @click="setCurrentPage(item.page)"
        >
          <span
            :class="currentPage === item.page ? 'current-link' : 'site-link'"
          >
            {{ item.page }}
          </span>
        </a>
      </span>
      <a
        class="social-media-link"
        v-for="item in socialMediaItems"
        :key="item.brand"
      >
        <span :data-alttext="item.brand" class="fa-container"
          ><span
            ><font-awesome-icon :icon="`fa-brands fa-${item.brand}`" /> </span
        ></span>
      </a>
      <a class="donor-link">
        <button
          class="rnd-btn donor-button"
          data-alttext="Donate"
          aria-label="link to the donor page"
        >
          <span>Become a donor</span>
        </button>
      </a>
    </div>
  </nav>
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
      this.$refs.dropdown.focus();
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
