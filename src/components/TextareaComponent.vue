<script>
import { store } from "../data/store";
import { DateTime } from "luxon";
export default {
  name: "TextareaComponent",
  props: {
    indexToSendMsg: Number,
    sendNotification: Boolean,
  },
  data() {
    return {
      store,
      now: DateTime.now(),
      chatText: "",
    };
  },
  methods: {
    sendMessage() {
      const msgData = {
        date: this.now
          .setLocale("it")
          .toLocaleString(DateTime.DATETIME_SHORT_WITH_SECONDS),
        message: this.chatText,
        status: "sent",
      };
      if (this.chatText !== "") {
        store.contacts[this.indexToSendMsg].messages.push(msgData);
      }
      this.chatText = "";
      this.reciveMessage();
    },
    reciveMessage() {
      setTimeout(() => {
        const msgFromContact = {
          date: this.now
            .setLocale("it")
            .toLocaleString(DateTime.DATETIME_SHORT_WITH_SECONDS),
          message: "OK!!",
          status: "received",
        };
        store.contacts[this.indexToSendMsg].messages.push(msgFromContact);
        if (this.sendNotification) {
          alert("Hai ricevuto un messaggio");
        }
      }, 1000);
    },
  },
};
</script>
<template>
  <div>
    <i class="fa-regular fa-face-smile"></i>
    <input
      v-model="chatText"
      @keyup.enter="sendMessage()"
      type="text"
      placeholder="Scrivi un messaggio"
    />
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
