<template>
  <div>
    <header class="gloabl-nav container">
      <div class="phone-number">
        <img class="phone-logo" src="/svg/phone.svg" alt="logo" />888.391.2214
      </div>
      <g-link to="/" aria-label="Home">
        <img class="header-logo" src="/svg/cra-logo.svg" alt="down arrow" />
      </g-link>
      <div class="mobile-nav" @click="openHamMenu">
        <img class="mobile-nav-trigger" src="/svg/hamburger.svg" />
      </div>
      <nav class="navbar navbar-dark" :class="{ show: hamMenu }">
        <g-link class="nav-link" to="/">Home</g-link>
        <span class="nav-link-dropdown nav-link">
          <g-link class="dd-parent" to="/about-us/">About Us</g-link>
          <img src="/svg/downarrow.svg" alt="down arrow" />
          <div class="drowdown-menu">
            <g-link to="/about-us/">Overview</g-link>
            <g-link to="/about-us/our-team/">Our Team</g-link>
            <g-link to="/about-us/our-approach/">Our Approach</g-link>
            <g-link to="/about-us/our-clients/">Our Clients</g-link>
          </div>
        </span>
        <g-link class="nav-link" to="/our-services/">Our Services</g-link>
        <g-link class="nav-link" to="/our-stories/">Our Stories</g-link>
        <g-link class="nav-link" to="/training-materials/">Training Materials</g-link>
        <g-link class="nav-link" to="/e-training-programs/">E-Training Programs</g-link>
        <g-link class="nav-link" to="/contact-us/">Contact Us</g-link>
      </nav>
    </header>
  </div>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      hamMenu: false
    };
  },
  methods: {
    openHamMenu() {
      this.hamMenu = !this.hamMenu;
    }
  }
};
</script>

<style lang="scss">
// Header Styles
.gloabl-nav {
  position: relative;
  margin: 2.5rem auto;
}

.header-logo {
  width: 30rem;
  height: 9rem;
  display: inline;
}

.navbar {
  float: right;
  margin-top: 3rem;
  font-size: $base-font-size;
}

.gloabl-nav .phone-number .phone-logo {
  width: 3.7rem;
  height: 2.7rem;
  padding-right: 0.5rem;
}

.gloabl-nav .phone-number {
  font-size: 2.2rem;
  letter-spacing: 0;
  text-align: right;
  line-height: 32px;
  position: absolute;
  top: 0;
  right: 3.4rem;
  color: $shiraz;
}

.navbar a {
  color: $mine-shaft;

  &:visited {
    color: $mine-shaft;
  }

  &:hover,
  &:focus {
    color: lighten($mine-shaft, 20%);
  }
}

.nav-link {
  display: inline;
}

.home .gloabl-nav {
  margin-top: 2.5rem;
  margin-bottom: 0;
}

.home .header-logo {
  width: 45.8rem;
  height: 13.7rem;
  margin: 0 auto;
  display: block;
}

.home .navbar {
  margin: 2rem 0;
  justify-content: center;
  float: none;
}

.nav-link-dropdown {
  position: relative;
}

.drowdown-menu {
  opacity: 0;
  position: absolute;
  // pointer-events: none;
  transition: all 300ms linear;
  background: $white;
  box-shadow: $box-shadow;
  z-index: 1;

  a {
    border-bottom: 1px solid $mine-shaft;
    padding: 1rem 2rem;
    box-sizing: border-box;
    display: block;
    white-space: nowrap;

    &:hover {
      background: $dusty-gray;
      color: $white;
    }
  }
}

.nav-link-dropdown {
  img {
    padding-left: 0.5rem;
  }
  &:hover {
    .drowdown-menu {
      opacity: 1;
      pointer-events: auto;
    }
  }
}

.mobile-nav {
  display: none;
}

// Hamburger menu :(
@media (max-width: em(1330px)) {
  .mobile-nav {
    display: block;
    position: absolute;
    top: 5rem;
    right: 4rem;
    cursor: pointer;

    .mobile-nav-trigger {
      width: 3rem;
    }
  }

  .navbar {
    display: block;
    background: $white;
    padding: 0;
    position: absolute;
    z-index: 3;
    box-shadow: $box-shadow;
    margin: 0;
    right: 3rem;
    // Visability
    opacity: 0;
    transition: all 300ms linear;
    pointer-events: none;

    .nav-link {
      display: block;
      padding: 1.5rem 3rem;
      border-bottom: 1px solid $mine-shaft;

      img {
        display: none;
      }

      .drowdown-menu {
        opacity: 1;
        position: relative;
        box-shadow: none;
        pointer-events: auto;

        a {
          padding: 1.5rem 4rem;
        }
      }
    }

    &.show {
      opacity: 1;
      pointer-events: auto;
    }

    .nav-link-dropdown {
      border-bottom: 0;
      padding: 0;

      .dd-parent {
        border-bottom: 1px solid $mine-shaft;
        width: 100%;
        display: block;
        padding: 1.5rem 2rem;
      }
    }
  }
  .gloabl-nav {
    .header-logo {
      margin: 2rem 0;
    }
  }
}

@media screen and (max-width: em(767px)) {
  .gloabl-nav {
    display: block;

    .phone-number {
      position: relative;
      top: unset;
      right: unset;
      text-align: left;
    }

    .header-logo {
      display: block;
      margin: 2rem 0;
    }
  }
}

@media screen and (max-width: em(440px)) {
  .gloabl-nav {
    margin: 1rem 0 0;

    .header-logo {
      width: 15rem;
      margin: 0;
    }
  }
}
</style>
