<script>
import { store } from "../data/store";
export default {
  name: "ContactsCardComponent",
  props: {
    dataFriends: Object,
    searchBarContact: String,
  },
  data() {
    return {
      store,
    };
  },
};
</script>

<template>
  <div
    class="card"
    v-if="
      dataFriends.name
        .toLowerCase()
        .trim()
        .includes(searchBarContact.toLowerCase().trim())
    "
  >
    <div class="image-person-container">
      <div class="cont-card-image">
        <img
          :src="store.getImage('avatar' + dataFriends.avatar + '.jpg')"
          :alt="dataFriends.name"
        />
      </div>
      <div class="cont-text-person">
        <h4 class="name">{{ dataFriends.name }}</h4>
        <p class="last-msg">
          {{
            dataFriends.messages && dataFriends.messages.length > 0
              ? dataFriends.messages[dataFriends.messages.length - 1].message
              : "Nessun messaggio disponibile"
          }}
        </p>
      </div>
    </div>
    <div class="date-message">
      <p class="time">
        {{
          dataFriends.messages && dataFriends.messages.length > 0
            ? dataFriends.messages[dataFriends.messages.length - 1].date
            : ""
        }}
      </p>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.card {
  height: 80px;
  width: 100%;
  padding: 5px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 0.8rem;
  &:hover {
    background-color: gainsboro;
    cursor: pointer;
  }

  .image-person-container {
    display: flex;
    align-items: center;
    gap: 10px;
    .cont-card-image {
      img {
        height: 50px;
        border-radius: 50%;
      }
    }
    .cont-text-person {
      p {
        font-size: 0.7rem;
        color: #a4a3a3;
        max-width: 130px;
      }
    }
  }
  .date-message {
    .time {
      color: #a4a3a3;
      font-size: 0.6rem;
      max-width: 50px;
    }
  }
}
</style>
