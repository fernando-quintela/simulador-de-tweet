<template>
  <div class="container">
    <h1 class="text-center"> Lista de Tweets</h1>
    <p v-if="tweets.length === 0">NO hay ningun tweet</p>
    <div class="tweet" v-for="tweet in tweets" :key="tweet.id">
      <p class="tweet__title">{{tweet.username}}</p>
      <p class="tweet__text">{{tweet.tweet}}</p>
      <span>{{formatDate(tweet.createdAt)}}</span>
      <Close @click="deleteTweet(tweet.id)"/>
    </div>

    

  </div>
</template>

<script>
import moment from "moment";
import "moment/locale/es";
import {Close} from "./Icons/index";
import { deleteTweetApi } from "../api/tweet";
export default {
  props: {
    tweets: Array,
    reloadTweets: Function
  },
  components: {
   Close
  },
  setup(props) {
    const formatDate = (date) => {
      return moment(date).fromNow();
    };

    const deleteTweet = (idTweet) => {
     deleteTweetApi(idTweet);
     props.reloadTweets();
    };
    // console.log(props.tweets);

    return {
      formatDate,
      deleteTweet
    }
  }

}
</script>

<style lang="scss">

.tweet {
  position: relative;
  border: 1px solid gray;
  padding: 23px;
  margin-bottom: 23px;
  display: flex;
  justify-content: space-between;
  align-items: center;

  p {
    margin: 0;
  }

  &__title {
    position: absolute;
    top: -12px;
    left: 10px;
    background: white;
    padding: 0 15px;
    font-weight: bold;
  }

  &__text {
    color: blue;
    font-size: 15px;
  }

  span {
    position: absolute;
    right: 10px;
    bottom: -9px;
    font-size: 12px;
    color: rgb(80, 80, 82);
    background: white;
    padding: 0 20px;
    border: 1px solid gray;
    font-size: 16px;
  }

  svg {
    width: 20px;
    height: 20px;

    &:hover {
      cursor: pointer;
      color: red;
    }
  }
}

</style>