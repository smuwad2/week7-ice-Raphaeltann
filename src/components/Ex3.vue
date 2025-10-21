<script>
import axios from 'axios';

export default {
  data() {
    return {
      moods: ["Happy", "Sad", "Angry"],
      posts: [],
      entry: "",
      mood: "",
      subject: "",
      showEditPost: false,
      editPostId: "",
      outputmessage: "",
    }
  },
  computed: {
    baseUrl() {
      if (window.location.hostname == 'localhost')
        return 'http://localhost:3000'
      else {
        const codespace_host = window.location.hostname.replace('5173', '3000')
        return `https://${codespace_host}`;
      }
    }
  },
  methods: {
    addpost() {
      axios.get(`${this.baseUrl}/addPost`, {
        params: {
          'entry': this.entry,
          'mood': this.mood,
          'subject': this.subject
        }
      }).then(response => {
        this.outputmessage = response.data.message;
      }).catch(error => {
        console.log(error)
      })
    }
  }
}
</script>

<template>
  <div class="table m-2">
    <h3>Add a New Blog Post</h3>

    Subject: <input type='text' size='30' v-model='subject' required>
    <br>

    Entry: <br>
    <textarea name='entry' cols='80' rows='5' v-model='entry' required></textarea>
    <br>

    Mood:
    <!-- TODO: Build a dropdown list here for selecting the mood -->
    <select v-model="mood">
      <option v-for="mood in moods">{{ mood }}</option>
    </select>
    <br>

    <br>
    <button @click="addpost">Submit New Post</button>
    <br>
    {{ outputmessage }}
    <hr> Click  <a><router-link to="/ViewPosts/">here</router-link></a>  to return to Main Page
  </div>
</template>
