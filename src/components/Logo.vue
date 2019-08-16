<template>
  <div class="logo">
    <img src="../assets/logo.svg" alt="Logo" />
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.logo {
  position: fixed;
  top: 30px;
  left: 40px;
  z-index: 999;
  img {
    height: 70px;
    width: auto;

    @media (max-width: 668px) {
      height: 40px;
    }
  }
}
</style>
