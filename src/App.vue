<template>
  <Menu :openCloseForm="openCloseForm"  :showForm="showForm" />
  <Form  :showForm="showForm" :reloadTweets="reloadTweets" :openCloseForm="openCloseForm"/>
  <TweetList :tweets="tweets" :reloadTweets="reloadTweets"/>
</template>

<script>
import { ref } from "vue";
import Menu from './components/Menu.vue';
import Form from './components/TweetForm.vue';
import useForm from './hooks/useFormTweet';
import TweetList from './components/TweetList.vue';
import { getTweetsApi } from "./api/tweet";
export default {
  name: 'App',
  components: {
    Menu,
    Form,
    TweetList,
    
  },
  setup() {
    let tweets = ref(getTweetsApi().reverse());

    const reloadTweets = () => {
      tweets.value = getTweetsApi().reverse();
    };
    return {
      ...useForm(),
      tweets,
      reloadTweets
    }
  }
}
</script>

<style lang="scss">


</style>
