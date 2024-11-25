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

const closeBurger = () => {
  let burgerOverlay = document.querySelector(".burger__overlay");
  burgerOverlay?.classList.toggle("active");
};
</script>

<template>
  <div class="home">
    <div class="burger__overlay">
      <button @click="closeBurger" class="burger__burger-button">
        <span></span>
        <span></span>
        <span></span>
      </button>
    </div>
    <div class="home__body">
      <!-- <h2 class="home__title" :style="{ fontSize: `${fontSize}px` }">
        Türkmenawtoulaglary Agentligi <br />
        Halkara Transport geçelgeleri
      </h2> -->
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
.burger__overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  overflow: hidden;
  background: #0000009b;
  transform: translateX(-100%);
  transition: 0.3s ease;
  &-button {
    top: 20px;
    right: 50px;
    position: absolute;
    background: transparent;
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
  &.active {
    transition: 0.3s ease;
    transform: translateX(0%);
  }
}
</style>
