<template>
  <v-list-item :to="toConvo" class="py-0 itemConversation" @click="onClick">
    <v-list-item-avatar v-if="avatarUrl">
      <v-img :src="avatarUrl"></v-img>
    </v-list-item-avatar>
    <v-list-item-icon v-else>
      <v-icon color="primary">{{
        iconName || convoObj.type === "single" ? "mdi-account" : "mdi-account-group"
      }}</v-icon>
    </v-list-item-icon>
    <v-list-item-title>{{ convoObj.conversation_name }}</v-list-item-title>
  </v-list-item>
</template>

<script>
export default {
  name: "ConversationItem",
  props: {
    avatarUrl: {
      type: String,
    },
    iconName: {
      type: String,
    },
    convoObj: {
      type: Object,
      required: true,
    },
  },
  methods: {
    onClick() {
      this.$emit("click", this.convoObj.id);
    },
  },
  computed: {
    toConvo() {
      return { name: "Message", params: { convoId: this.convoObj.id } };
    },
  },
};
</script>

<style></style>
