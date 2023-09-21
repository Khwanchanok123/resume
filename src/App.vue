<template>
  <div class="resume-header text-light mb-4">
    <div class="container py-5">
      <div class="row gap-3">
        <div class="col-sm-auto col-lg-auto col-12 col-md-12 text-center" v-if="toggleImage">
          <img :src="resumeImage" alt="Resume image" class="resume-image" />
        </div>
        <div class="col-sm col-lg my-auto col-12 col-md-12">
          <div class="row">
            <div class="col-6 col-md-3 text-start main-content">
              <p class="m-0">
                <a class="text-white" :href="'mailto:' + currentTranslations.email[0]">{{
                  currentTranslations.email[0]
                }}</a>
              </p>
              <p class="m-0">
                <a class="text-white" :href="'mailto:' + currentTranslations.email[1]">{{
                  currentTranslations.email[1]
                }}</a>
              </p>
              <p class="m-0">{{ currentTranslations.email[2] }}</p>
            </div>
            <div class="col-12 col-md-6 text-center order-md-0 order-first">
              <h2><a style="color: rgb(183, 159, 254)">{{ currentTranslations.nickname }}</a> {{ currentTranslations.name }}</h2>
              <h2>{{ currentTranslations.surname }}</h2>
            </div>
            <div class="col-6 col-md-3 text-end text-white main-content">
              <a class="no-print" target="_blank" :href="'//' + currentTranslations.github" ><img :src="github_icon" style="width: 50px;height:50px;" > </a>
              <a class="no-print" target="_blank" :href="'//' + currentTranslations.github" >My GitHub</a>
            <a class="print-only">{{currentTranslations.github}}</a>
</div>
            <div class="col-12 no-print text-center pt-4">
              [
              <a href="javascript:window.print()" class="no-print text-white">{{
                currentTranslations.printableVersion
              }}</a>
              ] [
              <a @click="toggleLanguage" href="javascript:void(0)" class="no-print text-white"
                >{{ currentTranslations.switchTo }}
                {{ "en" === currentLanguage ? "Thai" : "English" }}</a
              >
              ] [
              <a
                href="javascript: void(0)"
                @click="toggleImage = !toggleImage"
                class="no-print text-white"
                >{{ currentTranslations.toggleImage }}</a
              >
              ] [
              <a target="_blank"
                :href="'//' + currentTranslations.github + '/resume'"
                class="no-print text-white"
                >{{ currentTranslations.source }}</a
              >
              ]
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="container py-0 main-content">
    <div class="row">
      <div class="col-12">
        <p>
          {{ currentTranslations.introduction[0] }}
        </p>

        <p>
          {{ currentTranslations.introduction[1] }}
        </p>
      </div>
      <div class="col-12 no-print">
        <div class="row">
          <div class="col-12 col-md-7 mt-3">
            <div class="col-12">
              <h4>{{ currentTranslations.education[0].title }}</h4>
              <hr />
              <ul>
                <li
                  v-html="education"
                  v-for="(education, index) in currentTranslations.education[0].items"
                  :key="index"
                ></li>
              </ul>
            </div>
            <div class="col-12">
              <h4>{{ currentTranslations.technologies[0].title }}</h4>
              <hr />
              <ul>
                <li
                  v-html="technologies"
                  v-for="(technologies, index) in currentTranslations.technologies[0].items"
                  :key="index"
                ></li>
              </ul>
            </div>
          </div>
          <div class="col-12 col-md-5 mt-3">
            <h4>CERTIFICATIONS</h4>
            <hr />

            <div class="mt-1">
              <ul>
                <li
                  v-for="(item, index) in currentTranslations.certificates"
                  :key="index"
                  v-html="item"
                ></li>
              </ul>
            </div>
          </div>
        </div>
      </div>
      <div class="col-12 print-only">
        <div class="row">
          <div class="col-7 mt-3">
            <div class="col-12">
              <h4>{{ currentTranslations.education[0].title }}</h4>
              <hr />
              <ul>
                <li
                  v-html="education"
                  v-for="(education, index) in currentTranslations.education[0].items"
                  :key="index"
                ></li>
              </ul>
            </div>
            <div class="col-12">
              <h4>{{ currentTranslations.technologies[0].title }}</h4>
              <hr />
              <ul>
                <li
                  v-html="technologies"
                  v-for="(technologies, index) in currentTranslations.technologies[0].items"
                  :key="index"
                ></li>
              </ul>
            </div>
          </div>
          <div class="col-5 mt-3">
            <h4>CERTIFICATES</h4>
            <hr />

            <div class="mt-1">
              <ul>
                <li
                  v-for="(item, index) in currentTranslations.certificates"
                  :key="index"
                  v-html="item"
                ></li>
              </ul>
            </div>
          </div>
        </div>
      </div>
      <div class="col-12 mt-3">
        <h4>{{ currentTranslations.projects_title }}</h4>
        <hr />
        <ul>
          <li v-html="item" v-for="(item, index) in currentTranslations.projects" :key="index"></li>
        </ul>
      </div>
      <div class="col-12 mt-3">
        <h4>{{ currentTranslations.interests_title }}</h4>
        <hr />
        <ul>
          <li
            v-html="item"
            v-for="(item, index) in currentTranslations.interests"
            :key="index"
          ></li>
        </ul>
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import resumeImage from "@/assets/resume-image.png";
import unity_cert from "@/assets/unity_cert.png";
import github_icon from "@/assets/github_101792.png";
export default {
  data() {
    return {
      unity_cert,
      resumeImage,
      github_icon,
      toggleImage: true,
      translations: {
        en: {
          email: ["mju6404101306@mju.ac.th", "pearper2546@gmail.com", "Chaing Mai, Thailand"],
          name: "Khawnchanok",
          surname:" Saeneewong Na Ayutthaya",
          nickname: "Pearwa",
          github: "github.com/Khwanchanok123",
          printableVersion: "Printable version",
          switchTo: "Switch to",
          toggleImage: "Toggle image",
          source: "Source",
          introduction: [
            "I am Khwachanok Saeneewong Na Ayutthaya, also known as Pearwa, a Computer Science student at Maejo University. I have some basic experience in programming and served as a Teacher Assistant in the 20th and 21st Youth Computer Camp Project.",
            "I excel at time management, consistently completing work within specified deadlines, and I have a knack for quick learning.I am confident in my ability to communicate effectively and work well in a team."
          ],
          education: [
            {
              title: "EDUCATION",
              items: [
                "<b>HSC. Science-Mathematics,</b> Setthabutbumphen School, TH 2016 - 2021 [ GPAX 3.81 ]",
                "<b>B. Computer Science,</b> Maejo University, TH 2021 - present [ GPAX 4.00 ]"
              ]
            }
          ],
          technologies: [
            {
              title: "TECHNOLOGIES AND LANGUAGES",
              items: [
                "<b>Languages:</b> Python, Java(strong), C, Assembly, CSS.",
                "<b>Frameworks:</b> VueJS, Vuetify, Bootstrap.",
                "<b>Databases:</b> Docker(basic).",
              ]
            }
          ],
          certificates: [
            `<img src="${unity_cert}" alt="Unity Certified Programmer" style="width: 44px" class="mt-1 no-print" /> </a ><b>Unity Certified User: Programmer</b> (9/3/2022)`,
          ],
          projects_title: "PROJECTS",
          projects: [
            `<b>Coming Soon...</b> <a target="_blank" href="//--">--</a>`,
          ],
          interests_title: "INTERESTS",
          interests: [
            "Areas : Coding, Productivity & Life-hacks",
            "Beverage : Americano, Iced Espresso, Matcha tea",
            "Games : Arcade, Indie, FPS",
            "Pet : I have a cat name Khaijeaw"
          ]
        },
        th: {
          email: ["mju6404101306@mju.ac.th", "pearper2546@gmail.com", "เชียงใหม่, ประเทศไทย"],
          name: "ขวัญชนก",
          surname:"เสนีย์วงศ์ ณ อยุธยา",
          nickname: "แพรวา",
          github: "github.com/Khwanchanok123",
          printableVersion: "พิมพ์หน้านี้",
          switchTo: "เปลี่ยนภาษาเป็น",
          toggleImage: "แสดงรูปภาพ",
          source: "Source",
          introduction: [
            `ดิฉัน นางสาวขวัญชนก เสนีย์วงศ์ ณ อยุธยา หรือที่รู้จักในชื่อว่า แพรวา นักศึกษาสาขาวิทยาการคอมพิวเตอร์ มหาวิทยาลัยแม่โจ้ ดิฉันมีประสบการณ์พื้นฐานในการเขียนโปรแกรมและเป็นผู้ช่วยสอนหรือ TA ในโครงการค่ายคอมพิวเตอร์รุ่นที่ 20 และ 21 ของสาขาวิทยาการคอมพิวเตอร์ มหาวิทยาลัยแม่โจ้`,
            `ดิฉันค่อนข้างเชี่ยวชาญในการจัดการเวลา มีความสามารถในการทำงานตามกำหนดเวลาได้และดิฉันเป็นคนที่เรียนรู้ได้อย่างรวดเร็ว ดิฉันมั่นใจว่าดิฉันสามารถสื่อสารและทำงานร่วมกับผู้อื่นได้เป็นอย่างดี`
          ],
          education: [
            {
              title: "การศึกษา",
              items: [
                "<b>ประกาศนียบัตรมัธยมศึกษาตอนปลาย วิทยาศาสตร์และคณิตศาสตร์,</b> โรงเรียนเศรษฐบุตรบำเพ็ญ, 2015 - 2021 [ GPAX 3.81 ]",
                "<b>ปริญญาตรี. วิทยาการคอมพิวเตอร์,</b> มหาวิทยาลัยแม่โจ้, 2021 - ปัจจุบัน [ GPAX 4.00 ]"
              ]
            }
          ],
          technologies: [
            {
              title: "เทคโนโลยีและภาษาที่ใช้",
              items: [
                "<b>Languages:</b> Python, Java(strong), C, Assembly, CSS.",
                "<b>Frameworks:</b> VueJS, Vuetify, Bootstrap.",
                "<b>Databases:</b> Docker(basic).",
              ]
            }
          ],
          certificates: [
            `<img src="${unity_cert}" alt="Unity Certified Programmer" style="width: 44px" class="mt-1 no-print" /> </a ><b>Unity Certified User: Programmer</b> (9/3/2022)`,
          ],
          projects_title: "ผลงาน",
          projects: [
            `<b>Coming Soon...</b> <a target="_blank" href="//--">--</a>`,
          ],
          interests_title: "ความสนใจ",
          interests: [
            "สนใจเป็นพิเศษ : การเขียนโปรแกรม, การสร้างผลงาน & เทคนิคการใช้ชีวิต",
            "เครื่องดื่ม : อเมริกาโน่, เอสเปรสโซ่, ชาเขียวมัจฉะ",
            "แนวเกม : อาเขต, อินดี้, FPS",
            "สัตว์เลี้ยง : ผมมีแมวชื่อไข่เจียว"
          ]
        }
      },
      currentLanguage: "en" // Default language is English
    };
  },
  computed: {
    // Get the translations for the current language
    currentTranslations() {
      // @ts-ignore
      return this.translations[this.currentLanguage];
    }
  },
  methods: {
    // Function to toggle the language
    toggleLanguage() {
      this.currentLanguage = this.currentLanguage === "en" ? "th" : "en";
    }
  }
};
</script>
<style>
.resume-header {
  background-color: #140126;
}
.resume-image {
  height: 240px;
  border-radius: 5px;
}
hr {
  margin-top: 4px;
  margin-bottom: 4px;
}
.print-only {
  display: none;
}

@media print {
  .no-print {
    display: none !important;
  }

  .print-only {
    display: block !important;
  }

  .text-white {
    color: black !important;
  }

  /* fitting font size to A4 paper */
  .main-content {
    font-size: 12px !important;
  }
  hr {
    margin-top: -2px !important;
    margin-bottom: 4px !important;
    color: rgb(206, 162, 225) !important;
  }

  a {
    color: rgb(60, 2, 84) !important;
  }

  /* decrase all header tags size */
  h1,
  h2,
  h3,
  h4,
  h5,
  h6 {
    font-size: 18px !important;
    margin: 0 !important;
  }

  /* fiting heading size */
  .resume-header {
    margin-top: -2em !important;
    margin-bottom: -2em !important;
    color: black !important;
  }

  div.col-12.mt-3 {
    margin-top: 0.2em !important;
  }

  .resume-image {
    height: 140px !important;
  }
}
</style>
