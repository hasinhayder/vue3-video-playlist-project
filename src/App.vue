<template>
  <div class="container-fluid">
    <div class="row no-gutters">
      <div
        v-show="sidebar.active"
        class="col-lg-3 col-md-4 sidebar col-md-push-4"
      >
        <div class="wrapper">
          <div v-for="chapter in course.data.chapters" :key="chapter.title">
            <h2 class="ctitle">{{chapter.title}}</h2>
            <ul class="episodes">
              <li @click="playVid(episode.vid)" v-for="episode in chapter.episodes" :key="episode.vid">
                <h3 class="etitle">{{episode.title}}</h3>
                <span class="eduration"> {{episode.length}} </span>
              </li>
            </ul>
          </div>
        </div>
      </div>
      <div
        :class="
          sidebar.active
            ? 'col-lg-9 col-md-8 player col-md-pull-8'
            : 'col-lg-10 col-md-10 player offset-md-1'
        "
      >
        <div class="wrapper">
          <div class="container-fluid">
            <div class="row">
              <div class="col-md-12 col-lg-4">
                <ul class="plactions">
                  <li @click="toggleSidebar">
                    <span v-if="sidebar.active">Close Sidebar</span>
                    <span v-else>Open Sidebar</span>
                  </li>
                  <li>Course Info</li>
                  <li>Notes</li>
                </ul>
              </div>
              <div class="col-md-12 col-lg-4">
                <h1 class="coursetitle">{{course.data.title}}</h1>
              </div>
              <div class="col-md-12 col-lg-4">
                <ul class="practions">
                  <li>Home</li>
                  <li>Facebook Group</li>
                  <li class="emphasize">Support</li>
                </ul>
              </div>
            </div>
          </div>
          <div class="course-player">
            <iframe
              :src="'https://www.youtube.com/embed/'+vid"
              frameborder="0"
              allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
              allowfullscreen
            ></iframe>
          </div>
          <div class="course-nav">
            <div class="container-fluid">
              <div class="row">
                <div class="col-md-6 left">
                  <button>Previous Episode</button>
                </div>
                <div class="col-md-6 right">
                  <button>Next Episode</button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import course from "./data/course.json"

export default {
  name: "App",
  data() {
    return {
      vid:"MggIZaWXpo8",
      sidebar: { active: true },
      course,
    }
  },
  methods: {
    toggleSidebar() {
      this.sidebar.active = !this.sidebar.active
    },
    playVid(videoId){
      this.vid = videoId
    }
  },
}
</script>
