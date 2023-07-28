<template>
  <div class="note-form__wrapper">
    <form class="note-form" @submit.prevent="onSubmit">
      <textarea required v-model="value" placeholder="Type ur note" />
      <TagsList @onItemClick="handleTagClick" :items="tags" :tempArr="tempArr" />
      <button class="btn btnPrimary" type="submit">Add new note</button>
    </form>
  </div>
</template>

<script>
import TagsList from "@/components/UI/TagsList";

export default {
  components: { TagsList },
  data() {
    return {
      value: "",
      tags: ["home", "work", "travel"],
      checkedTags: [],
      tempArr: [],
    };
  },
  methods: {
    onSubmit() {
      this.$emit("onSubmit", { title: this.value, arr: this.checkedTags });
      this.value = "";
      this.checkedTags = [];
      this.tempArr = [];
    },

    handleTagClick(tag, i) {

      if (this.checkedTags.length > 0) {
        let isMatch = false;

        this.checkedTags.forEach(el => {
          if (tag === el) {
            isMatch = true;
          }
        });

        if (isMatch) {
          this.checkedTags = this.checkedTags.filter(el => tag !== el);
        } else {
          this.checkedTags.push(tag);
        }

      } else {
        this.checkedTags.push(tag);
      }

    },
  },
};
</script>

<style lang="scss">
.note-form__wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.note-form {
  display: flex;
  flex-direction: column;
  max-width: 600px;
  width: 100%;
  textarea {
    margin-bottom: 0;
  }
}
</style>