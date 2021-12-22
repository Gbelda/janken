<template>
  <div class="component_container">
    <div class="card_container">
      <div class="header">
        <h3>RULES</h3>
        <div class="img_container">
          <img
            src="../assets/images/icon-close.svg"
            alt=""
            @click="$emit('toggleOff', false)"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss">
.component_container {
  width: 100vw;
  height: 100vh;
  position: fixed;
  background-color: rgba(0, 0, 0, 0.568);
  top: 0%;
  left: 0%;
  z-index: 99;
  display: flex;

  .card_container {
    min-width: 400px;
    margin: auto;
    height: 450px;
    background-image: url(../assets/images/image-rules.svg);
    background-color: white;
    background-repeat: no-repeat;
    background-size: 70%;
    background-position-x: center;
    background-position-y: 70%;
    border-radius: 15px;

    .header {
      padding: 2rem 1rem 0%;
      justify-content: space-between;
      display: flex;
      align-items: center;
    }

    h3 {
      font-size: 2rem;
    }

    .img_container {
      display: flex;

      &:hover {
        cursor: pointer;
      }
    }

    img {
      width: 30px;
      height: 30px;
    }
  }
}
</style>