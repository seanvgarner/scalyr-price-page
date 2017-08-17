<template>
  <div class="slider-container">
    <div class="slide-col">
      <h2>Simple Pricing</h2>
      <div class="slider-wrapper">
        <vue-slider v-model="value"
          :min="0"
          :max="16"
          :dot-size="22"
    		  :bg-style="bgStyle"
    		  :processStyle="processStyle"
          :sliderStyle="sliderStyle"
          :speed="0.2"
          height="14"
    		  width="100%"
          tooltip-dir="bottom"
          v-on:input="updatePrice($event)">
          <template slot="tooltip" scope="tooltip">
            <div class="diy-tooltip">
              <span v-if="value < 12">{{ gigs[value] }}GB</span>
              <span v-else>{{ gigs[value] / 1000 }}TB</span>
            </div>
          </template>
    		</vue-slider>
      </div>
      <div class="labels">
        <div>
          1 GB/Day
        </div>
        <div>
          100 TB/Day
        </div>
      </div>
    </div>

    <div class="slide-col">
      <div v-if="value < 12" class="price-tag">${{ getPrice }}<span class="month">/MO</span></div>
      <div v-else>
        <a id="quote-link" href="#">Get a Quote</a>
      </div>
    </div>
	</div>

</template>

<script>
import VueSlider from 'vue-slider-component';

export default {
  name: 'slider',
  components: {
    VueSlider
  },
  data: function() {
    // In order to display non-linear prices/gigs while sliding, we set the slider to start
    // at 0 and then use its value as an index to find the amount of gigs in the array.
    // This allows for customization of what specific price points to showcase.
		return {
			value: 2,
      price: 50,
      gigs: [ 1, 2, 3, 4, 5, 10, 15, 20, 50, 100, 500, 800, 1000, 5000, 10000, 50000, 100000 ],
      // Styling for the slider component: Needs to be passed in as objects.
      bgStyle: {
        "backgroundColor": "#fff",
        "border": "2px solid #9E9E9E",
        "borderRadius": "0"
      },
      processStyle: {
        "height": "40%",
        "backgroundColor": "#9FD3A7",
        "borderRadius": "0",
        "margin": "4px"
      },
      sliderStyle: {
        "boxSizing": "border-box",
        "border": "1px solid #9E9E9E",
        "backgroundColor": "#fff"
      }
		}
	},
  methods: {
    updatePrice: function(val) {
      this.price = 50 * this.gigs[val];
    }
  },
  computed: {
    getPrice: function() {
      let p = this.price - 1;
      return p.toLocaleString();
    }
  }
}
</script>

<style lang="less">
  @sliderGrey: #9E9E9E;
  @lighterGreen: #5bc3b2;
  @darkerGreen: #567981;
  @fadedGreen: #9FD3A7;

  .slider-container {
    max-width: 500px;
    min-width: 200px;
    width: 100%;
    height: 250px;
    margin: 0 auto;
    display: flex;
    flex-direction: column;
  }

  .slide-col {
    flex: 1;
    text-align: center;
  }

  .slide-col h2 {
    font-size: 30px;
    font-weight: 300;
    padding-bottom: 20px;
  }

  .slider-wrapper {
    max-width: 400px;
    margin: 0px auto;
  }

  .labels {
    font-size: 14px;
    color: @sliderGrey;
    display: flex;
    justify-content: space-between;
  }

  .labels div {
    padding: 3px 30px;
  }

  .diy-tooltip {
    color: @sliderGrey;
    position: relative;
    top: -5px;
    font-size: 10px;
    width: 100px;
  }

  .diy-tooltip::after {
    content: "";
    background-color: @fadedGreen;
    height: 12px;
    width: 12px;
    display: block;
    border-radius: 50%;
    position: absolute;
    top: -20px;
    left: 44px;
  }

  .price-tag {
    display: flex;
    font-size: 50px;
    justify-content: center;
    padding-top: 20px;
  }

  .price-tag span {
    margin-top: 4px;
    font-size: 12px;
  }

  #quote-link {
    transition: all 0.2s ease-in-out;
    color: @darkerGreen;
    line-height: 30px;
    display: flex;
    height: 30px;
    border: 2px solid @darkerGreen;
    width: 95px;
    margin: 25px auto;
    border-radius: 5px;
    justify-content: center;
  }

  #quote-link:hover {
    color: @lighterGreen;
    border: 2px solid @lighterGreen;
  }

  @media (max-width: 500px) {
    .labels div {
      padding: 3px 5px;
      font-size: 12px;
    }

    .diy-tooltip {
      font-size: 8px
    }
  }
</style>
