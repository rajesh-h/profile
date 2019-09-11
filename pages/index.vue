<template>
  <v-container class="page grey lighten-4">
    <div class="left-col black">
      <div class="personal" style="padding-top:20px;">
        <p class="title text-uppercase condensed light mb-0">
          {{ resume.name.first }} {{ resume.name.middle }}
          {{ resume.name.last }}
        </p>
        <p class="text-uppercase subtitle-2 font-weight-black">
          {{ resume.position }}
        </p>
        <p class="pl-2 grey--text caption">
          <v-icon class="grey--text">mdi-phone</v-icon>
          {{ resume.contact.phone }}
        </p>
        <p class="pl-2 grey--text caption">
          <v-icon class="grey--text">mdi-email</v-icon>
          {{ resume.contact.email }}
        </p>
        <p class="pl-2 grey--text caption">
          <v-icon class="grey--text">mdi-github-circle</v-icon>
          <a
            :href="'https://github.com/' + resume.contact.github"
            target="_blank"
            >github.com/{{ resume.contact.github }}</a
          >
        </p>
        <p class="pl-2 grey--text caption">
          <v-icon class="grey--text">mdi-city</v-icon>
          {{ resume.contact.city }}
        </p>
      </div>
      <div class="skills">
        <p class="grey--text text-uppercase subtitle-2 font-weight-black pt-3">
          SKILLS / CONCEPTS
        </p>
        <div v-for="skill in resume.skills" :key="skill.name" class="pl-2">
          <p class="grey--text text-uppercase caption mb-0">
            {{ skill.name }}
          </p>
          <progress
            class="grey--text mlr-2"
            style="width:96%; height:3px; vertical-align: top;"
            max="100"
            :value="skill.level"
          ></progress>
        </div>
      </div>

      <div class="accomplishments">
        <p class="grey--text text-uppercase subtitle-2 font-weight-black pt-3">
          ACCOMPLISHMENTS
        </p>
        <div
          v-for="(accmp, index) in resume.accomplishments"
          :key="index"
          class="pl-2"
        >
          <p class="grey--text body-2 mb-2">&#9679; {{ accmp }}</p>
        </div>
      </div>

      <div class="about-me">
        <p class="grey--text text-uppercase subtitle-2 font-weight-black pt-3">
          ABOUT ME
        </p>
        <div v-for="(abt, index) in resume.about" :key="index" class="pl-2">
          <p class="grey--text body-2 mb-2">&#9679; {{ abt }}</p>
        </div>
      </div>
    </div>
    <div class="right-col">
      <div class="career-objective" style="padding-top:20px;">
        <p class="black--text text-uppercase subtitle-2 font-weight-black pt-3">
          CAREER OBJECTIVE
        </p>
        <div class="white">
          <p class="body-2 black--text pa-2 font-weight-light text-justify">
            {{ resume.objective }}
          </p>
        </div>
      </div>
      <div class="languages">
        <p class="black--text text-uppercase subtitle-2 font-weight-black pt-3">
          LANGUAGES / TOOLS / SOFTWARES WORKED ON
        </p>
        <div class="white">
          <div class="pa-2">
            <v-chip
              v-for="tool in resume.toolsLanguages"
              :key="tool.name"
              class="overlay font-weight-regular mr-1 mb-1"
              style="height:22px; border-radius:11px"
              :color="tool.color"
              text-color="black"
            >
              {{ tool.name }}
            </v-chip>
          </div>
          <div class="pa-2">
            <p class="body-2 black--text px-2 font-weight-light">
              LEGENDS:
              <v-chip
                class="overlay font-weight-regular mr-1 mb-1"
                style="height:22px; border-radius:11px"
                color="green"
                text-color="black"
              >
                Advanced
              </v-chip>
              <v-chip
                class="overlay font-weight-regular mr-1 mb-1"
                style="height:22px; border-radius:11px"
                color="orange"
                text-color="black"
              >
                Medium
              </v-chip>
              <v-chip
                class="overlay font-weight-regular mr-1 mb-1"
                style="height:22px; border-radius:11px"
                color="grey"
                text-color="black"
              >
                Basic
              </v-chip>
            </p>
          </div>
        </div>
      </div>
      <div class="work-experience">
        <p class="black--text text-uppercase subtitle-2 font-weight-black pt-3">
          WORK EXPERIENCE
        </p>
        <div v-for="comp in resume.experience" :key="comp.timeperiod">
          <div class="white pa-2 mb-3">
            <p class="black--text body-2 font-weight-regular mb-0">
              {{ comp.company }} - {{ comp.position }}
            </p>
            <p class="grey--text body-2 font-weight-regular">
              Domain: {{ comp.domain }} - {{ comp.timeperiod }}
            </p>
            <p
              v-for="(desc, index) in comp.description"
              :key="index"
              class="body-2 black--text mb-1 pl-2 font-weight-light text-justify"
            >
              &#9679; {{ desc }}
            </p>
          </div>
        </div>
      </div>
      <div class="education">
        <p class="black--text text-uppercase subtitle-2 font-weight-black pt-3">
          EDUCATION
        </p>
        <div class="white pa-2">
          <p
            class="body-2 black--text pa-2 font-weight-light text-justify mb-0"
          >
            {{ resume.education[0].degree }}
          </p>
        </div>
      </div>

      <!-- <div v-if="1 == 2" class="demo">
        <p class="black--text text-uppercase subtitle-2 font-weight-black pt-3">
          DEMO
        </p>
        <div class="white">
          <v-row class="pa-2">
            <v-col
              v-for="video in resume.videoDemo"
              :key="video.name"
              class="d-flex child-flex"
              cols="4"
            >
              <v-card flat tile class="d-flex">
                <v-img
                  :src="video.demoImage"
                  :lazy-src="video.demoImage"
                  aspect-ratio="1"
                  class="grey lighten-2"
                  border="5"
                >
                  <v-card-title
                    class="blue--text align-end text-center fill-height font-weight-black"
                    style="font-size: 14px !important;"
                    >{{ video.name }}</v-card-title
                  >
           
                  <template v-slot:placeholder>
                    <v-row
                      class="fill-height ma-0"
                      align="center"
                      justify="center"
                    >
                      <v-progress-circular
                        indeterminate
                        color="grey lighten-5"
                      ></v-progress-circular>
                    </v-row>
                  </template>
                </v-img>
              </v-card>
            </v-col>
          </v-row>
        </div>
      </div> -->
      <div class="furtherLinks">
        <p class="black--text text-uppercase subtitle-2 font-weight-black pt-3">
          FURTHER LINKS / DEMOS/ SOURCE CODES
        </p>
        <div class="white pa-2 mb-3">
          <p class="body-2 black--text pa-2 font-weight-light text-justify">
            For detailed Profile please refer this link.<br />

            <a
              href="https://github.com/rajesh-h/profile/tree/master/detailed"
              target="_blank"
              >https://github.com/rajesh-h/profile/tree/master/detailed</a
            >
          </p>
          <p class="pl-2 body-2 black--text ">Demo/Source</p>
          <p
            v-for="link in resume.gitHubLinks"
            :key="link.name"
            class="body-2 black--text pl-10  font-weight-light text-justify mb-0"
          >
            <a :href="link.link" target="_blank">{{ link.name }}</a>
            <span class="caption black--text">--{{ link.type }}</span>
          </p>
        </div>
      </div>
      <div class="lookingForward">
        <p class="black--text text-uppercase subtitle-2 font-weight-black pt-3">
          LOOKING FORWARD
        </p>
        <div class="white pa-2 mb-1">
          <p class="black--text pa-2 body-2 font-weight-regular ">
            {{ resume.lookingForward.text }}
          </p>

          <v-chip
            v-for="(prof, index) in resume.lookingForward.profiles"
            :key="index"
            class="overlay font-weight-regular mr-1 mb-1"
            style="height:22px; border-radius:11px"
            color="grey lighten-2"
            text-color="black"
          >
            {{ prof }}
          </v-chip>
        </div>
      </div>
      <div class="d-none d-print-block" style="position:absolute; bottom: 0;">
        <p class="black--text text--right caption font-weight-thin ">
          This Profile can be accessed online at
          <a href="https://rajesh-h.github.io/profile/"
            >https://rajesh-h.github.io/profile/</a
          >
        </p>
      </div>
    </div>
  </v-container>
</template>

<script>
const getResume = () => import('~/data/resume.json').then((m) => m.default || m)

export default {
  async asyncData({ req }) {
    const resume = await getResume()

    return { resume }
  },
  head: {
    title: 'Rajesh Profile',
    meta: [
      {
        hid: 'resume',
        name: 'resume',
        content: 'Rajesh Resume'
      }
    ]
    // ...
  }
}
</script>
<style scoped>
.page {
  /* background: white; */
  position: relative;
  width: 21cm;
  height: 55cm;
  display: block;
  page-break-after: auto;
  overflow: hidden;
  /* margin-top: 10px; */
}
.left-col {
  width: 35%;
  float: left;
  padding-left: 16px;
  height: 100%;
}
.right-col {
  width: 64%;
  float: right;
}
@media print {
  .skills {
    page-break-after: always;
  }
}
</style>
