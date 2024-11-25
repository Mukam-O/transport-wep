<script setup lang="ts">
import TheBurgerMenu from "~/components/TheBurgerMenu.vue";

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
const activeBurgerMenu = ref(false);
const showBurgerMenu = () => {
  activeBurgerMenu.value = !activeBurgerMenu.value;
};
</script>

<template>
  <div class="home">
    <video
      autoplay
      muted
      loop
      src="../assets/video/AWTOULAG-SRGI-(MONITOR)karta-duz.mp4"
    ></video>
    <div @click="showBurgerMenu" class="header__burger">
      <button class="home__burger-button">
        <span></span>
        <span></span>
        <span></span>
      </button>
    </div>
    <div class="home__body">
      <div :class="['home__item-wrapper', { active: activeBurgerMenu }]">
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
            @click="router.push('/agrament')"
            :style="{ fontSize: `${fontSize2}px`, padding: `${padding}px` }"
          >
            Aşgabat halkara ylalaşygy <br />
            Ulag geçelgesi
          </button>
          <button
            class="home__item"
            @click="router.push('/nourth')"
            :style="{ fontSize: `${fontSize2}px`, padding: `${padding}px` }"
          >
            Aşgabat halkara ylalaşygy <br />
            Ulag geçelgesi
          </button>
          <button
            class="home__item"
            @click="router.push('/traceca')"
            :style="{ fontSize: `${fontSize2}px`, padding: `${padding}px` }"
          >
            Ýewropa-kawkaz-Aziýa halkara <br />
            (Traceca) Ulag geçelgesi
          </button>
          <button
            class="home__item"
            @click="router.push('/silk-way')"
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
    height: 100vh;
  }

  &__title {
    position: absolute;
    top: 5px;
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
    transform: translateX(150%);
    transition: 0.3s;
    &.active {
      transform: translateX(0%);
      transition: 0.3s;
    }
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

  &__burger {
    &-button {
      top: 20px;
      right: 50px;
      position: absolute;
      background: rgba(0, 0, 0, 0.5);
      border: 1px solid white;
      padding: 7.57px 5.67px;
      border-radius: 4px;
      span {
        display: block;
        width: 40px;
        height: 5px;
        border-radius: 1.27px;
        background: var(--white);
        margin-bottom: 5px;
        user-select: none;
        &:last-child {
          margin-bottom: 0;
        }
      }
    }
  }
}
</style>
