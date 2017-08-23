<template lang="html">
  <div class="demo-form-container">
    <button type="button" class="request-btn">Request a Demo</button>
    <div class="wrapper">
      <div class="description">We just need a few bits of data and you'll be able to jump in and start exploring Scalyr immediately</div>
      <form class="request-form">
        <label>Email address:</label>
        <input type="email" class="email-inp">
        <label for="">Company name:</label>
        <input type="text" class="company-name-inp">
        <label for="">Comments (optional):</label>
        <textarea name="comments" rows="8" cols="80" class="comments-inp"></textarea>
        <p>Preferred plan size: {{ gigs }}GB/day, 30 days retention</p>
        <button type="button" name="submit">Submit</button>
      </form>
    </div>
  </div>
</template>

<script>
import { bus } from '../main.js';

export default {
  name: 'demo-form',
  data: function() {
    return {
      gigs: '',
    }
  },
  created() {
    bus.$on('updateGigs', (data) => {
      this.gigs = data;
    })
  },
  methods: {

  }
}
</script>

<style lang="less">
  .demo-form-container {
    display: block;
    background: #efefef;
    padding: 45px;
  }

  .request-btn {
    display: block;
    margin: 0 auto;
    border: 1px solid #000;
    padding: 10px;
    background-color: #9FD3A7;
    color: #fff;
    font-size: 14px;
  }

  .wrapper {
    margin-top: 50px;
  }

  .description {
    text-align: center;
  }

  .request-form {
    display: flex;
    flex-direction: column;
    width: 430px;
    margin: 50px auto;
  }

</style>
