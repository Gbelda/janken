<template>
  <footer>
    <div class="rules">
      <h3>RULES</h3>
    </div>
  </footer>
</template>

<script>
export default {};
</script>

<style lang="scss">
footer {
  position: fixed;
  right: 0%;

  .rules {
    line-height: 35px;
    width: 120px;
    height: 40px;
    margin-right: 5rem;
    border: 2px solid hsl(217, 16%, 45%);
    text-align: center;
    border-radius: 10px;

    &:hover {
      cursor: pointer;
    }

    h3 {
      color: rgb(216, 216, 216);
    }
  }
}
</style>