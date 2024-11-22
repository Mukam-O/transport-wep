<template>
  <svg
    :width="iconWidth"
    :height="iconHeight"
    viewBox="0 0 91 92"
    fill="none"
    xmlns="http://www.w3.org/2000/svg"
  >
    <path
      d="M14.2188 46L76.7812 46"
      stroke="white"
      stroke-width="8"
      stroke-linecap="round"
      stroke-linejoin="round"
    />
    <path
      d="M51.1875 71.5938L76.7812 46L51.1875 20.4062"
      stroke="white"
      stroke-width="8"
      stroke-linecap="round"
      stroke-linejoin="round"
    />
  </svg>
</template>
<script setup lang="ts">
const iconWidth = ref(48);
const iconHeight = ref(48);

const resizeIcon = () => {
  const width = window.innerWidth;

  if (width < 600) {
    iconWidth.value = 12;
    iconHeight.value = 12;
  } else if (width >= 600 && width < 1200) {
    iconWidth.value = 24;
    iconHeight.value = 24;
  } else {
    iconWidth.value = 48;
    iconHeight.value = 48;
  }
};

onMounted(() => {
  resizeIcon();
  window.addEventListener("resize", resizeIcon);
});

onBeforeUnmount(() => {
  window.removeEventListener("resize", resizeIcon);
});
</script>
