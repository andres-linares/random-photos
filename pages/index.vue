<template>
  <div>
    <photos-grid />

    <span>Made with love by Andrés</span>
  </div>
</template>

<script>
export default {
  head() {
    return {
      title: 'Random Photos',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'A museum of random photos in a masonry style'
        },
        {
          hid: 'og:image',
          name: 'og:image',
          content: '/screenshot.PNG'
        }
      ]
    }
  }
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Nunito:wght@400&display=swap');

* {
  margin: 0;
  padding: 0;
}

body {
  background: #18191a;
  overflow-y: scroll;
}

span {
  position: fixed;
  top: 0.5rem;
  left: 0.125rem;
  font-family: 'Nunito';
  color: #fff;
  writing-mode: vertical-lr;
  font-size: 0.6rem;
  letter-spacing: 0.07em;
}

ul,
ol {
  list-style: none;
}

img {
  display: block;
  max-width: 100%;
}
</style>
