<template>
  <div class="results">
    <div class="container">
      <div class="results-wrap">
        <span class="results-title">
          Say <span class="results-title_italic">“hello”</span> to the <br />
          realest results
        </span>
        <p class="results-text">
          The top G-Plans success stories are almost always from clients in our
          commitment program.
        </p>
      </div>
    </div>
    <VueSlickCarousel v-bind="settings">
      <div class="results-slide" v-for="slide in results" :key="slide.id">
        <video width="268" height="268" controls preload>
          <!-- <source src="~/assets/images/results/sample.mp4" type="video/mp4" /> -->
        </video>
        <div v-if="slide.showPlay" class="results-slide__info">
          <span class="results-slide__name">{{ slide.name }}</span>
          <span class="results-slide__text">{{ slide.text }}</span>
        </div>
        <div
          v-if="slide.showPlay"
          class="results-slide__play"
          @click="play(slide)"
        ></div>
      </div>
    </VueSlickCarousel>
  </div>
</template>

<script>
import VueSlickCarousel from "vue-slick-carousel";
import "vue-slick-carousel/dist/vue-slick-carousel.css";
import "vue-slick-carousel/dist/vue-slick-carousel-theme.css";

export default {
  data() {
    return {
      settings: {
        dots: true,
        centerMode: true,
        variableWidth: true,
        infinite: false,
        initialSlide: 1,
      },
      results: [
        {
          id: 0,
          name: "Amber",
          text: "Lost 52 lbs and 9% body fat!",
          url: "~/assets/images/results/sample.mp4",
          showPlay: true,
        },
        {
          id: 1,
          name: "Alyssa",
          text: "Lost 37 lbs so far!",
          url: "~/assets/images/results/sample.mp4",
          showPlay: true,
        },
        {
          id: 2,
          name: "Rebecca",
          text: "Lost 67 lbs and 13 inches!",
          url: "~/assets/images/results/sample.mp4",
          showPlay: true,
        },
      ],
    };
  },
  components: {
    VueSlickCarousel,
  },
  methods: {
    startPlay(idx) {
      const video = document.querySelectorAll("video");

      video.forEach((v, i) => {
        if (i === idx) {
          v.play();
        }
      });
    },
    stopPlay(idx) {
      const video = document.querySelectorAll("video");

      video.forEach((v, i) => {
        if (i === idx) {
          v.pause();
        }
      });
    },

    play(slide) {
      this.results.forEach((item, idx) => {
        if (item === slide) {
          item.showPlay = false;
          this.startPlay(idx);
        } else {
          item.showPlay = true;
          this.stopPlay(idx);
        }
      });
    },
  },
};
</script>

<style></style>
