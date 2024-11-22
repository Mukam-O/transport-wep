<script setup lang="ts">
const fontSize = ref(16);
const fontSize2 = ref(14);
const padding = ref(20);

const updateFontSize = () => {
  const baseSize = 16;
  const baseSecondarySize = 8;
  const basePadding = 8;
  const scaleFactor = window.innerWidth / 600;
  fontSize.value = Math.max(baseSize * scaleFactor, 12);
  fontSize2.value = Math.max(baseSecondarySize * scaleFactor, 10);
  padding.value = Math.max(basePadding * scaleFactor, 10);
};

onMounted(() => {
  updateFontSize();
  window.addEventListener("resize", updateFontSize);
});

onUnmounted(() => {
  window.removeEventListener("resize", updateFontSize);
});
const router = useRouter();
const goTime = (path: string) => {
  router.push(path);
};
</script>

<template>
  <div class="home">
    <video
      autoplay
      muted
      loop
      src="../assets/video/Ludovico Einaudi - Experience (Live from Teatro dal Verme, Milano).mp4"
    ></video>
    <div class="home__body">
      <h2 class="home__title" :style="{ fontSize: `${fontSize}px` }">
        Türkmenawtoulaglary Agentligi <br />
        Halkara Transport geçelgeleri
      </h2>
      <div class="home__item-wrapper">
        <div class="home__items">
          <button
            @click="router.push('/lapis')"
            class="home__item"
            :style="{ fontSize: `${fontSize2}px`, padding: `${padding}px` }"
          >
            Lapis lazuli halkara <br />
            Ulag geçelgesi
          </button>
          <button
            class="home__item"
            @click="router.push('/lapis2')"
            :style="{ fontSize: `${fontSize2}px`, padding: `${padding}px` }"
          >
            Aşgabat halkara ylalaşygy <br />
            Ulag geçelgesi
          </button>
          <button
            class="home__item"
            @click="router.push('/lapis3')"
            :style="{ fontSize: `${fontSize2}px`, padding: `${padding}px` }"
          >
            Aşgabat halkara ylalaşygy <br />
            Ulag geçelgesi
          </button>
          <button
            class="home__item"
            @click="router.push('/lapis4')"
            :style="{ fontSize: `${fontSize2}px`, padding: `${padding}px` }"
          >
            Ýewropa-kawkaz-Aziýa halkara <br />
            (Traceca) Ulag geçelgesi
          </button>
          <button
            class="home__item"
            @click="router.push('/lapis5')"
            :style="{ fontSize: `${fontSize2}px`, padding: `${padding}px` }"
          >
            ýüpek ýoly halkara <br />
            Ulag geçelgesi
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.home {
  position: relative;
  height: 100%;
  width: 100%;

  &__body {
  }
  video {
    object-fit: cover;
    width: 100%;
    height: 100%;
  }

  &__title {
    position: absolute;
    top: 10px;
    left: 30%;
    font-size: 40px;
    font-weight: 900;
    letter-spacing: 0.06em;
    text-align: center;
    color: var(--white);
    margin-bottom: 30px;
  }

  &__item-wrapper {
    position: absolute;
    top: 15%;
    right: 20px;
    display: flex;
    justify-content: flex-end;
  }

  &__items {
    display: flex;
    gap: 20px;
    flex-direction: column;
  }

  &__item {
    text-transform: uppercase;
    border-radius: 30px;
    padding: 20px 40px;
    font-size: 25px;
    font-weight: 700;
    line-height: 130%;
    text-align: center;
    background: rgba(0, 0, 0, 0.5);
    color: var(--white);
    transition: 0.3s ease;
    &:hover {
      background: rgba(10, 113, 37, 0.8);
    }
  }
}
</style>
