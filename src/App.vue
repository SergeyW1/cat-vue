<template>
  <div class="app">
    <div class="cat-content">
      <div class="img-cat">
        <img
          v-if="boolText"
          :class="catFilter"
          src="https://scientificrussia.ru/images/b/teb-full.jpg"
          alt="cat"
          :style="[imgStyles, imgRotate]"
        />
        <span v-else>Кот спрятался</span>
      </div>
      <div class="cat-content__nav">
        <h1>Красивый котик</h1>
        <div class="filter">
          <h2>Фильтры</h2>
          <button
            class="btn"
            :class="catFilter.grayscale1 ? 'active' : ''"
            @click="catFilter.grayscale1 = !catFilter.grayscale1"
          >
            Не множко серого
          </button>
          <button
            class="btn"
            :class="catFilter.grayscale ? 'active' : ''"
            @click="catFilter.grayscale = !catFilter.grayscale"
          >
            Бесцветный
          </button>
          <button
            class="btn"
            :class="catFilter['btn-shadow'] ? 'active' : ''"
            @click="catFilter['btn-shadow'] = !catFilter['btn-shadow']"
          >
            Тень
          </button>
        </div>
        <div>
          <h2>Размер</h2>
          <div>
            <div>Ширина: {{ imgSizes.currentWidth }}</div>
            <input
              type="range"
              v-model="imgSizes.currentWidth"
              :max="imgSizes.maxWidth"
            />
          </div>
          <div>
            <div>Высота: {{ imgSizes.currentHeight }}</div>
            <input
              type="range"
              v-model="imgSizes.currentHeight"
              :max="imgSizes.maxHeight"
            />
          </div>
        </div>
        <div>
          <h2>Поворот</h2>
          <div>Угол: {{ imgSizes.currentRotate }}</div>
          <input
            type="range"
            v-model="imgSizes.currentRotate"
            :max="imgSizes.maxRotate"
          />
        </div>
        <button class="btn" @click="boolText = !boolText">
          {{ boolText ? "Спрятать" : "Раскрыть" }}
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      boolText: true,
      catFilter: {
        grayscale: false,
        grayscale1: false,
        "btn-shadow": false,
      },
      imgSizes: {
        maxWidth: 680,
        maxHeight: 420,
        currentWidth: 680,
        currentHeight: 420,
        currentRotate: 0,
        maxRotate: 360,
      },
    };
  },
  computed: {
    imgStyles() {
      return {
        width: `${this.imgSizes.currentWidth}px`,
        height: `${this.imgSizes.currentHeight}px`,
      };
    },
    imgRotate() {
      return {
        transform: `rotate(${this.imgSizes.currentRotate}deg)`,
      };
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Comfortaa:wght@300;400&display=swap");

.app {
  font-family: "Comfortaa", cursive;
  margin: 50px auto;
  width: 1200px;
}

.cat-content {
  display: flex;
}

.cat-content__nav {
  margin-left: 30px;
}

.btn {
  font-size: 12px;
  font-family: "Comfortaa", cursive;
  padding: 5px;
  margin-right: 10px;
}

ul,
li {
  list-style-type: none;
  padding: 0;
}

.grayscale {
  filter: grayscale(100%);
}

.active {
  background: pink;
}

.grayscale1 {
  transform: rotate(-45deg);
  filter: grayscale(0.5);
}

.btn-shadow {
  box-shadow: 4px 4px 8px 0px rgba(34, 60, 80, 0.2);
}

.img-cat {
  background: rgba(0, 0, 0, 0.481);
  width: 680px;
  height: 420px;
}
</style>
