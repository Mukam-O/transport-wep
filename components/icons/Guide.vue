<template>
  <svg
    :width="iconWidth"
    :height="iconHeight"
    viewBox="0 0 91 92"
    fill="none"
    xmlns="http://www.w3.org/2000/svg"
  >
    <path
      d="M76.7812 46H14.2188"
      stroke="white"
      stroke-width="8"
      stroke-linecap="round"
      stroke-linejoin="round"
    />
    <path
      d="M39.8125 20.4062L14.2188 46L39.8125 71.5938"
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
