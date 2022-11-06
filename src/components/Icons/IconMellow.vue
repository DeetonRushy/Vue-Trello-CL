<template>
  <div class="icon-area">
    <img class="icon" src="./images/mellow.png"  alt="Mellow"/>
    <p class="icon-text">
      <slot></slot>
    </p>
  </div>
</template>

<script>
export default {
  name: "IconMellow"
}
</script>

<style scoped>

.icon-area{
  display: flex;
  text-align: center;

  margin-right: 0;
}

.icon {
  display: inline-block;
  width: 15px;
  height: 20px;
  overflow: hidden;

  border-radius: 50%;

  left: 0;
}

.icon-text{
  margin: 0;
  display: inline;
  color: white;

  font-family: fantasy;
}
</style>