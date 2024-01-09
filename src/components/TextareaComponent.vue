<script>
export default {
  name: "TextareaComponent",
};
</script>
<template>
  <div>
    <i class="fa-regular fa-face-smile"></i>
    <input type="text" placeholder="Scrivi un messaggio" />
    <i class="fa-solid fa-microphone"></i>
  </div>
</template>

<style lang="scss" scoped>
div {
  height: 100%;
  width: 100%;
  padding: 5px 9px;
  background-color: #ede9e5;
  display: flex;
  justify-content: space-between;
  align-items: center;
  i {
    font-size: 1.5rem;
    color: #b4b3b3;
    cursor: pointer;
  }
  input {
    height: 90%;
    width: 75%;
    border-radius: 8px;
    border: 1px solid #b4b3b3;
    padding-left: 10px;
  }
}
</style>
