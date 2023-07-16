<template>
  <Form @onSubmit="handleSubmit" />
  <List @onRemove="handleRemove" :items="notes" />
</template>

<script>
import Form from "@/components/Notes/Form";
import List from "@/components/Notes/List";

export default {
  components: { Form, List },
  data() {
    return {
      notes: [
        {
          title: "Learn Vue 3",
          tags: ["work"],
        },
        {
          title: "Finish course",
          tags: ["work", "home"],
        },
      ],
    };
  },
  mounted() {
    this.getNotes();
  },
  watch: {
    notes: {
      handler(updatedList) {
        localStorage.setItem("notes", JSON.stringify(updatedList));
      },
      deep: true,
    },
  },
  methods: {
    // * get / set notes
    getNotes() {
      const localNotes = localStorage.getItem("notes");
      if (localNotes) {
        this.notes = JSON.parse(localNotes);
      }
    },
    // * submit note
    handleSubmit(title) {
      const note = {
        title: title,
        tags: [],
      };
      this.notes.push(note);
      console.log(note);
    },
    // * remove note
    handleRemove(index) {
      this.notes.splice(index, 1);
    },
  },
};
</script>