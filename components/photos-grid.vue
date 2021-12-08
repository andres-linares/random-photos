<template>
  <ul>
    <li
      v-for="seed in seeds"
      :key="seed.seed"
      :style="{ 'grid-row-end': `span ${seed.span}` }"
    >
      <img :src="`https://picsum.photos/seed/${seed.seed}/${imageSize}`" />
    </li>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      seeds: [],
      interval: null,
      imageSize: 600,
    };
  },
  created() {
    this.imageSize = window.innerWidth < 720 ? 350 : 600;
  },
  mounted() {
    this.interval = setInterval(
      () => {
        const seed = Math.random() * (this.seeds.length + 1);
        let span = Math.round(Math.random() * 2 + 1);
        const lastSpan = this.seeds[this.seeds.length - 1]?.span;
        if (span === lastSpan) span = Math.round(Math.random() * 2 + 1);

        this.seeds.push({ seed, span });

        this.$nextTick().then(() => {
          window.scrollTo({ top: 999999, behavior: "smooth" });
        });
      },
      window.innerWidth < 720 ? 900 : 750
    );
  },
};
</script>

<style scoped>
ul {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(15rem, 1fr));
  grid-auto-rows: 6rem;
  gap: 1rem;
  margin: 1rem;
  margin-left: 1.125rem;
}

@media screen and (max-width: 720px) {
  ul {
    grid-template-columns: repeat(auto-fill, minmax(8rem, 1fr));
    grid-auto-rows: 4rem;
  }
}

img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  box-sizing: border-box;
  background: linear-gradient(45deg, #ffffff1a, #dddddd1a);
  opacity: 0;
  animation: appear 700ms ease-out 1s forwards;
  transition: transform 250ms ease-out;
}

li {
  position: relative;
  box-shadow: 1px 1px 3px #ffffff36;
  overflow: hidden;
}

li:hover img {
  transform: scale(1.25) rotate(8deg);
}

li::after {
  content: "";
  position: absolute;
  inset: 0;
  border: 4px solid #ffffffdf;
  opacity: 0;
  animation: appear 700ms ease-out forwards;
}

@keyframes appear {
  to {
    opacity: 1;
  }
}
</style>
