<script>
import { store } from "../data/store";
import ContactsCardComponent from "./ContactsCardComponent.vue";
import ChatCardComponent from "./ChatCardComponent.vue";
import TextareaComponent from "./TextareaComponent.vue";
export default {
  name: "WhatsAppCard",
  components: {
    ContactsCardComponent,
    ChatCardComponent,
    TextareaComponent,
  },
  data() {
    return {
      store,
    };
  },
  methods: {
    getBackgroundImage(image) {
      return { backgroundImage: `url('${image}')` };
    },
  },
};
</script>

<template>
  <div class="whatsApp-card">
    <div class="header-card">
      <div class="user-data">
        <div class="user-pic">
          <img :src="store.getImage('avatar_io.jpg')" alt="" />
        </div>
        <div class="user-name">
          <h4>Sofia</h4>
        </div>
      </div>
      <div class="friend-active-data">
        <div class="friend-pic-name">
          <img :src="store.getImage('avatar_1.jpg')" alt="" />
          <div class="cont-text">
            <h4>Michele</h4>
            <p>Online •</p>
          </div>
        </div>
      </div>
    </div>
    <div class="card-main">
      <div class="friends-list">
        <div class="container-alerts">
          <div class="icon">
            <i class="fa-solid fa-bell"></i>
          </div>
          <div class="text-alert">
            <strong>Ricevi notifiche di nuovi messaggi!</strong>
            <p>Attiva notifiche desktop</p>
          </div>
        </div>
        <div class="container-chats">
          <ContactsCardComponent
            v-for="(item, index) in store.contacts"
            :dataFriends="item"
          />
        </div>
      </div>
      <div
        :style="getBackgroundImage(store.getImage('mine.jpg'))"
        class="active-chat"
      >
        <div class="chat-container">
          <ChatCardComponent />
        </div>
        <div class="textarea-container">
          <TextareaComponent />
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@use "../styles/variables" as *;
.whatsApp-card {
  height: 700px;
  width: 70%;
  border: 1px solid #000;

  .header-card {
    height: 70px;
    background-color: $card-header-bg;
    display: flex;

    & > div {
      height: 100%;
    }

    .user-data,
    .friend-active-data {
      display: flex;
      align-items: center;
      gap: 0px 10px;
      padding: 8px;
      img {
        max-width: 40px;
        border-radius: 50%;
      }
    }
    .user-data {
      width: $left-size-card-width;
      border: 1px solid #a4a3a3;
    }
    .friend-active-data {
      width: $chat-active-width;
      flex-direction: column;
      align-items: flex-start;
      border-width: 1px 1px 1px 0px;
      border-style: solid;
      border-color: #a4a3a3;
      justify-content: center;
      .friend-pic-name {
        display: flex;
        align-items: center;
        gap: 0px 10px;
        margin-bottom: 3px;
        p {
          font-size: 0.7rem;
          color: #a4a3a3;
          cursor: default;
        }
      }
    }
  }
  .card-main {
    height: calc(100% - 70px);
    display: flex;
    .friends-list,
    .active-chat {
      height: 100%;
    }

    .friends-list {
      width: $left-size-card-width;
      background-color: #fff;
      .container-alerts {
        height: 60px;
        background-color: $main-blue;
        display: flex;
        align-items: center;
        gap: 0px 7px;
        font-size: 0.8rem;
        padding: 4px 15px;
        .icon {
          height: 40px;
          width: 40px;
          background-color: #fff;
          border-radius: 50%;
          display: flex;
          justify-content: center;
          align-items: center;
          i {
            font-size: 1.5rem;
            color: $main-blue;
          }
        }
        .text-alert {
          strong {
            color: rgba(21, 21, 21, 0.85);
          }
          p {
            text-decoration: underline;
            color: #a4a3a3;
          }
        }
      }
      .container-chats {
        width: 100%;
        max-height: calc(100% - 60px);
        overflow-y: auto;
      }
    }
    .active-chat {
      width: $chat-active-width;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      .chat-container {
        height: calc(100% - 45px);
        padding: 12px;
      }
      .textarea-container {
        height: 45px;
        width: 100%;
        background-color: red;
      }
    }
  }
}
</style>
