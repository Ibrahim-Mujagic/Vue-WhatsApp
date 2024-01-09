<script>
export default {
  name: "ChatCardComponent",
  props: {},
  data() {
    return {};
  },
};
</script>

<template>
  <div class="cloud cloud-sent">
    <p class="text-message">
      Lorem ipsum dolor sit amet consectetur adipisicing elit.
    </p>
    <p class="date-message-sent">10/12/2023 15:00:00</p>
  </div>
  <div class="cloud cloud-received">
    <p class="text-message">
      Lorem ipsum dolor sit amet consectetur adipisicing elit.
    </p>
    <p class="date-message-sent">10/12/2023 15:00:00</p>
  </div>
</template>

<style lang="scss" scoped>
.cloud {
  min-height: 40px;
  border-radius: 10px;
  min-width: 50%;
  max-width: 330px;
  margin-bottom: 15px;
  padding: 7px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  &.cloud-sent {
    background-color: #d5f9ba;
    margin-left: auto;
  }
  &.cloud-received {
    margin-right: auto;
    background-color: #fff;
  }
  p {
    font-size: 0.8rem;
    &.text-message {
      max-width: 250px;
    }
    &.date-message-sent {
      font-size: 0.6rem;
      max-width: 70px;
      text-align: right;
    }
  }
}
</style>
