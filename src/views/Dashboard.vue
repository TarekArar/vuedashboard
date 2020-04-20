<template>
  <div class="ma-4">
    <h1 class="subheading grey--text">Dashboard</h1>
    <v-container class="my-5">
      <v-row row class="mb-3">

        <v-tooltip bottom>
          <template v-slot:activator="{ on }">
            <v-btn small text color="grey" v-on="on" class="mx-3" @click="sortBy('title')">
              <v-icon left small>folder</v-icon>
              <span class="caption text-lowercase">By project name</span>
            </v-btn>
          </template>
          <span>Oder by project name</span>
        </v-tooltip>

        <v-tooltip bottom>
          <template v-slot:activator="{ on }">
            <v-btn small text color="grey" v-on="on" @click="sortBy('person')">
              <v-icon left small>person</v-icon>
              <span class="caption text-lowercase">By person</span>
            </v-btn>
          </template>
          <span>Oder by person name</span>
        </v-tooltip>
      </v-row>

      <v-card flat class="px-3" v-for="(project, index) in projects" :key="index">
        <v-row row wrap :class="`pa-3 project ${project.status}`">
          <v-col cols="12" md="6">
            <div class="caption grey--text">Project Title</div>
            <div>{{project.title}}</div>
          </v-col>
          <v-col xs="2">
            <div class="caption grey--text">Person</div>
            <div>{{project.person}}</div>
          </v-col>
          <v-col xs="2">
            <div class="caption grey--text">Due Date</div>
            <div>{{project.due}}</div>
          </v-col>
          <v-col xs="2">
            <v-chip :class="`${project.status} caption white--text my-2 `" small>{{project.status}}</v-chip>
          </v-col>
        </v-row>
        <v-divider></v-divider>
      </v-card>
    </v-container>
  </div>
</template>

<script>
export default {
  name: "Home",
  data() {
    return {
      projects: [
        {
          title: "Design a new website",
          person: "The Net Ninja",
          due: "1st Jan 2019",
          status: "ongoing",
          content:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!"
        },
        {
          title: "Code up the homepage",
          person: "Chun Li",
          due: "10th Jan 2019",
          status: "complete",
          content:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!"
        },
        {
          title: "Design video thumbnails",
          person: "Ryu",
          due: "20th Dec 2018",
          status: "complete",
          content:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!"
        },
        {
          title: "Create a community forum",
          person: "Gouken",
          due: "20th Oct 2018",
          status: "overdue",
          content:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!"
        }
      ]
    };
  },
  mounted() {
    this.sortBy("title");
  },
  methods: {
    sortBy(prop) {
      this.projects.sort((a, b) => (a[prop] <= b[prop] ? -1 : 1));
    }
  }
};
</script>

<style>
.project.ongoing {
  border-left: 4px solid orange;
}

.project.complete {
  border-left: 4px solid #3dc1c2;
}

.project.overdue {
  border-left: 4px solid tomato;
}

.v-chip.ongoing {
  background: orange !important;
}
.v-chip.complete {
  background: #3dc1c2 !important;
}
.v-chip.overdue {
  background: tomato !important;
}
</style>