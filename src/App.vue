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
            "I am Khwachanok Saeneewong Na Ayutthaya, also known as Pearwa, a Third-year Computer Science student at Maejo University. I have some basic experience in programming and served as a Teacher Assistant in the 20th and 21st Youth Computer Camp Project.",
            "I have a strong proficiency in time management, being able to work efficiently and meet deadlines consistently. I am a quick learner and am confident in my ability to communicate effectively and collaborate with others. My special expertise lies in system design and structural development. I aspire to further advance my skills and hope that your esteemed company will consider my application. Thank you very much for your kind consideration.",
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
                "<b>Languages:</b> Python, Java(strong), HTML, Assembly, CSS.",
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
            `<b>GonnaGo</b> Designing a website system for travel in Chiang Mai. <a target="_blank" href="//travel-go-eight.vercel.app/?fbclid=IwAR05RtJ-bT6BGVTFEYyf7i60iJdiRTKOtWzRaoYztgey-pn6maY0s5vo3aw">GonnaGo</a>`,
            `<b>MUJLibrary</b>  Designing a book borrowing system <a target="_blank" href="//drive.google.com/drive/folders/1ndD7-Aab7eE8jG7P05I7phSrxE1KHvG0?usp=drive_link">MUJLibrary</a>`,
            `<b>QuickNote</b> A website for leaving some notes <a target="_blank" href="//note-app-8b269.web.app/login?classId=bafbc167-d49c-4902-89cd-70ce9466fc32&assignmentId=cb60278f-4c4a-47b2-bfab-e958534d505b&submissionId=2a0cc702-547b-53f8-de05-5acb58f9cb18">QuickNote</a>`,
            `<b>Dashboard</b> A self-introduction website created with Bootstrap. <a target="_blank" href="//khwanchanok123.github.io/Booststrap-Profile/index.html">Dashboard</a>`,
          ],
          interests_title: "INTERESTS",
          interests: [
            "Areas : Movie, Make-up",
            "Talent : Piano",
            "Beverage : Matcha tea, Lemon tea",
            "Games : FPS, MOBA"
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
            `ดิฉัน นางสาวขวัญชนก เสนีย์วงศ์ ณ อยุธยา หรือที่รู้จักในชื่อว่า แพรวา นักศึกษาสาขาวิทยาการคอมพิวเตอร์ มหาวิทยาลัยแม่โจ้ ชั้นปีที่ 3 ดิฉันมีประสบการณ์พื้นฐานในการเขียนโปรแกรมและเป็นผู้ช่วยสอนหรือ TA ในโครงการค่ายคอมพิวเตอร์รุ่นที่ 20 และ 21 ของสาขาวิทยาการคอมพิวเตอร์ มหาวิทยาลัยแม่โจ้`,
            `ดิฉันค่อนข้างเชี่ยวชาญในการจัดการเวลา มีความสามารถในการทำงานตามกำหนดเวลาได้และดิฉันเป็นคนที่เรียนรู้ได้อย่างรวดเร็ว ดิฉันมั่นใจว่าดิฉันสามารถสื่อสารและทำงานร่วมกับผู้อื่นได้เป็นอย่างดี 
            ดิฉันมีความถนัดด้านการออกแบบระบบและโครงสร้างระบบเป็นพิเศษ ดิฉันอยากที่จะพัฒนาตนเองให้ได้มากกว่านี้ และหวังว่าทางบริษัทของท่านจะรับดิฉันพิจารณา ขอบพระคุณเป็นอย่างสูง`,
    
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
                "<b>Languages:</b> Python, Java(strong), HTML, Assembly, CSS.",
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
            `<b>GonnaGo</b> ออกแบบระบบเว็ปไซต์ท่องเที่ยวทั่วเชียงใหม่ <a target="_blank" href="//travel-go-eight.vercel.app/?fbclid=IwAR05RtJ-bT6BGVTFEYyf7i60iJdiRTKOtWzRaoYztgey-pn6maY0s5vo3aw">GonnaGo</a>`,
            `<b>MUJLibrary</b> ออกแบบระบบเว็ปไซต์จองหนังสือออนไลน์ <a target="_blank" href="//drive.google.com/drive/folders/1ndD7-Aab7eE8jG7P05I7phSrxE1KHvG0?usp=drive_link">MUJLibrary</a>`,
            `<b>QuickNote</b> เว็ปไซต์สำหรับการเขียนโน็ตฝากไว้ <a target="_blank" href="//note-app-8b269.web.app/login?classId=bafbc167-d49c-4902-89cd-70ce9466fc32&assignmentId=cb60278f-4c4a-47b2-bfab-e958534d505b&submissionId=2a0cc702-547b-53f8-de05-5acb58f9cb18">QuickNote</a>`,
            `<b>Dashboard</b> เว็ปไซต์แนะนำตนเองสร้างจาก Bootstrap <a target="_blank" href="//khwanchanok123.github.io/Booststrap-Profile/index.html">Dashboard</a>`,
          ],
          interests_title: "ความสนใจ",
          interests: [
            "สนใจเป็นพิเศษ : ภาพยนต์, การแต่งหน้า",
            "ความสามารถพิเศษ : เล่นเปียโน",
            "เครื่องดื่ม : ชาเขียวมัจฉะ, ชามะนาว",
            "แนวเกม : FPS, MOBA"
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
