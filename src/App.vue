<template>
  <div id="app">
    <header-menu></header-menu>
    <section id="title-hero">
      <div class="container">
        <h1>Pricing &amp; Plans for Everyone</h1>
        <h3>No credit card required to give Scalyr a try, because we know you'll love it.</h3>
      </div>
    </section>
    <slider></slider>
    <footer>
      <div class="sub-footer">
        For lower-volume users, our Kindling Plan offers 0.5GB per day with 7 days retention for $19 per month.
      </div>
      <h4 id="features-title">Standard Features For All Include:</h4>
      <div class="features-container">
        <ul>
          <li>✓ Custom Log Parsing</li>
          <li>✓ Log Graphs</li>
          <li>✓ Server Monitoring</li>
          <li>✓ Custom Dashboards</li>
          <li>✓ Log Search &amp; Analysis</li>
        </ul>
        <ul>
          <li>✓ Custom Alerts</li>
          <li>✓ Custom Metrics</li>
          <li>✓ Multi-User</li>
          <li>✓ User Permissions</li>
          <li>✓ Audit Trails</li>
        </ul>
      </div>
    </footer>
    <demo-form></demo-form>
  </div>
</template>

<script>
import Slider from './components/Slider'
import HeaderMenu from './components/HeaderMenu'
import DemoForm from './components/DemoForm'

export default {
  name: 'app',
  components: {
    Slider,
    HeaderMenu,
    DemoForm
  }
}
</script>

<style lang="less">

  #app {
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    font-family: 'Roboto', sans-serif;
  }

  #title-hero {
    display: block;
  }

  #title-hero .container {
    width: 85%;
    padding-top: 90px;
    padding-bottom: 100px;
    margin: 0 auto;
  }

  #title-hero .container h3 {
    font-size: 17px;
    text-align: center;
    font-weight: 300;
  }

  #title-hero .container h1 {
    font-weight: 500;
    font-size: 36px;
    letter-spacing: -1px;
    text-align: center;
    margin-bottom: 15px;
  }

  footer {
    padding: 0px 10px;
    display: flex;
    flex-direction: column;
  }

  .sub-footer {
    display: block;
    text-align: center;
    padding-top: 20px;
    padding-bottom: 30px;
    font-weight: 300;
    font-size: 15px;
  }

  #features-title {
    display: block;
    font-weight: 500;
    font-size: 28px;
    letter-spacing: -0.5px;
    text-align: center;
    padding-bottom: 15px;
  }

  .features-container {
    margin: 0 auto;
    width: 300px;
    display: flex;
    justify-content: space-between;
    margin-bottom: 60px;
  }

  .features-container li {
    font-size: 12px;
    margin-bottom: 8px;
  }

  @media (max-width: 600px) {
    #title-hero .container {
      padding-top: 65px;
    }
  }

  @media (max-width: 400px) {
    .features-container {
      width: 250px;
    }
  }

</style>
