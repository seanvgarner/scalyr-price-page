<template lang="html">
  <div class="header-container">
    <nav>
      <a href="#">
        <img src="../assets/images/scalyr-logo.png">
      </a>
      <ul :class="navClass">
        <li><a href="#">FEATURES</a></li>
        <li><a href="#">PRICING</a></li>
        <li><a href="#">RESOURCES</a></li>
        <li><a href="#">CAREERS</a></li>
        <li><a href="#">LOGIN</a></li>
      </ul>
      <button class="burger" v-on:click="toggleMenu">
        <span class="bun"></span>
        <span class="bun"></span>
        <span class="bun"></span>
      </button>
    </nav>
  </div>
</template>

<script>
export default {
  name: 'header-menu',
  data: function() {
    return {
      navClass: "nav-menu"
    }
  },
  methods: {
    toggleMenu: function() {
      this.navClass = this.navClass === "nav-menu" ? "show-menu" : "nav-menu";
    }
  }
}
</script>

<style lang="less">
  @lighterGreen: #5bc3b2;
  @darkerGreen: #547687;

  .header-container {
    padding-top: 25px;
    padding-bottom: 20px;
    width: 90%;
    margin: 0 auto;
  }

  .header-container nav {
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
  }

  .header-container img {
    display: block;
    width: 140px;
  }

  .header-container li {
    font-weight: 700;
    margin: 0 35px;
    font-size: 10px;
  }

  .header-container ul a {
    color: #000;
    padding-bottom: 2px;
    transition: all 0.2s ease-in-out;
  }

  .header-container ul a:hover {
    color: @lighterGreen;
    border-bottom: 1px solid @lighterGreen;
  }

  .burger {
    margin: 0;
    padding: 0;
    border: none;
    background-color: #fff;
  }

  .burger:hover {
    cursor: pointer;
  }

  .burger:hover .bun {
    background-color: @lighterGreen;
  }

  .burger:focus {
    outline: none;
  }

  .bun {
    transition: all 0.2s ease-in-out;
    display: block;
    background: #000;
    width: 25px;
    height: 2px;
    border-radius: 3px;
    margin-bottom: 4px;
  }

  .nav-menu {
    display: flex;
    align-items: center;
    margin-bottom: 0;
    list-style-type: none;
  }

  .show-menu {
    flex-direction: row;
    display: flex;
    align-items: center;
    margin-bottom: 0;
    list-style-type: none;
  }

  @media (min-width: 800px) {
    .burger {
      display: none;
    }
  }

  @media (max-width: 800px) {
    .nav-menu {
      display: none;
    }

    .show-menu {
      width: 100%;
      display: flex;
      flex-direction: column;
      align-items: center;
      order: 4;
    }

    .show-menu li {
      margin: 15px auto;
    }
  }
</style>
