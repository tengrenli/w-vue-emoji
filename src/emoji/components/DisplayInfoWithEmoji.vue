<template>
  <span>
    <template v-for="oMsg in msgWithEmoji">
      <span v-if="oMsg.t === 0">{{oMsg.m}}</span>
      <span v-else>
        <emoji-item :emojiObj="oMsg.m"></emoji-item>
      </span>
    </template>
  </span>
</template>

<script>
  import {convertStr2Emoji} from "../index"
  import EmojiItem from "./EmojiItem"

  export default {
    name: "DisplayInfoWithEmoji",
    components: {
      EmojiItem
    },
    props: {
      msg: String
    },
    created() {
      this.msgWithEmoji = convertStr2Emoji(this.msg);
    },
    data() {
      return {
        msgWithEmoji: []
      };
    },
    watch: {
      msg(oNewVal, oOldVal) {
        this.msgWithEmoji = convertStr2Emoji(this.msg);
      }
    }
  }

</script>

<style scoped lang="less" type="text/less">

</style>
