<script setup lang="ts">
import Guide from "~/components/icons/Guide.vue";
import NextGuide from "~/components/icons/Next-guide.vue";

const fontSize = ref(16);
const padding = ref(20);

const updateFontSize = () => {
  const baseSize = 10;
  const basePadding = 5;
  const scaleFactor = window.innerWidth / 600;
  fontSize.value = Math.max(baseSize * scaleFactor, 12);
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
  <div class="lapiz">
    <video
      autoplay
      muted
      loop
      src="../assets/video/Ludovico Einaudi - Experience (Live from Teatro dal Verme, Milano).mp4"
    ></video>
    <div class="lapiz__body">
      <div class="lapiz__button-out">
        <button
          @click="router.push('/')"
          class="lapiz__button-btn-out"
          :style="{ fontSize: `${fontSize}px`, padding: `${padding}px` }"
        >
          <Guide /> çykmak
        </button>
      </div>
      <div class="lapiz__button-next">
        <button
          @click="router.push('/lapis3')"
          class="lapiz__button-btn-next"
          :style="{ fontSize: `${fontSize}px`, padding: `${padding}px` }"
        >
          <NextGuide /> indiki
        </button>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.lapiz {
  position: relative;
  height: 100vh;
  width: 100%;

  &__body {
  }
  video {
    object-fit: cover;
    width: 100%;
    height: 100%;
  }
  &__button-out {
    position: absolute;
    top: 3%;
    left: 20px;
  }

  &__button-btn-out {
    color: var(--white);
    background: rgba(0, 0, 0, 0.5);
    border-radius: 15px;
    text-transform: uppercase;
    font-size: 20px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 30px;
    transition: 0.3s ease;
    &:hover {
      background: rgba(10, 113, 37, 0.8);
    }
  }
  &__button-next {
    position: absolute;
    bottom: 20px;
    right: 20px;
  }

  &__button-btn-next {
    color: var(--white);
    background: rgba(10, 113, 37, 0.8);
    border-radius: 15px;
    text-transform: uppercase;
    font-size: 20px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 30px;
  }
}
</style>
