<script>
import { store } from "../data/store";
export default {
  name: "ChatCardComponent",
  props: {
    chatData: Object,
    indexMessage: Number,
    contactIndex: Number,
  },
  data() {
    return {
      store,
      hideWindowVisible: true,
    };
  },
  methods: {
    deleteMessage(index) {
      const activeMessagese = this.store.contacts[this.contactIndex].messages;
      activeMessagese.splice(index, 1);
    },
  },
};
</script>

<template>
  <div
    :class="{
      ' cloud': true,
      'cloud-sent': chatData.status === 'sent',
      'cloud-received': chatData.status === 'received',
    }"
    @click="hideWindowVisible = !hideWindowVisible"
  >
    <p class="text-message">
      {{ chatData.message }}
    </p>
    <p class="date-message-sent">{{ chatData.date }}</p>
    <div
      :class="{
        ' window-delete': true,
        'd-none': hideWindowVisible,
      }"
    >
      <p @click="deleteMessage(indexMessage)">Delete Message</p>
    </div>
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
  position: relative;
  cursor: pointer;
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
  .window-delete {
    background-color: white;
    height: 60px;
    border-radius: 10px;
    padding: 5px;
    position: absolute;
    top: 110%;
    left: 80%;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    z-index: 10;
    p {
      color: red;
      cursor: pointer;
    }
    &.d-none {
      display: none;
    }
  }
}
</style>
