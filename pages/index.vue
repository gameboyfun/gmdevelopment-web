<template>
  <div>
    <div :class="bgNav">
      <Navbar />
    </div>

    <div class="fulldiv">
      <video ref="videoPlayer" muted loop autoplay playsinline>
        <source
          :src="
            require('~/assets/video/190828_07_MarinaBayatNightDrone_UHD_22.mp4')
          "
          type="video/mp4"
        />
        <p>Your browser does not support the video tag.</p>
      </video>
      <ul class="text-rotation" style="font-family: 'Mali', cursive">
        <li>we are developer</li>
        <li>we are god</li>
        <li>we are inwza</li>
        <li>we are shit</li>
      </ul>
    </div>
    <div class="body">
      <h2 class="py-5 d-flex justify-content-center">Service</h2>
      <div class="row px-3 rownomr">
        <div
          v-for="(service, id) in services"
          :key="id"
          class="col-sm-6 col-md-4 col-lg-4 indiv"
        >
          <div class="d-flex justify-content-center pb-3">
            <fa :icon="service.icon" id="service.header" class="fa-3x" />
          </div>
          <h5 class="d-flex justify-content-center">{{ service.header }}</h5>
          <div class="pt-2 pb-5">{{ service.detail }}</div>
        </div>
      </div>
      <div class="py-5" style="background: white">
        <h2 class="pb-3 d-flex justify-content-center">ต้องการใบเสนอราคา?</h2>
        <div class="pb-3 d-flex justify-content-center">
          <b-button v-scroll-to="'#contact'" size="lg" variant="secondary"
            >ติดต่อเรา</b-button
          >
        </div>
        <div class="d-flex justify-content-center">
          <img
            class="image"
            :src="
              require('~/assets/image/favpng_responsive-web-design-web-development-website.png')
            "
            alt=""
          />
        </div>
      </div>
      <div class="row py-5 rownomr px-5">
        <div class="col-sm-3 pb-3">
          <div class="pb-3">
            <h4>WORK PROCESS</h4>
          </div>
          <div>
            เพียง 3 ขั้นตอนง่ายๆ ที่จะทำให้คุณชนะคู่แข่งทุกการแข่งขันบนโลก
            Digital
          </div>
        </div>
        <div v-for="(workflow, id) in workflow" :key="id" class="col-sm-3">
          <div class="d-flex justify-content-center align-items-center pb-3">
            <fa :icon="workflow.icon" id="workflow.icon" class="fa-5x" />
          </div>
          <div class="d-flex justify-content-center align-items-center pb-3">
            {{ workflow.header }}
          </div>
        </div>
      </div>
      <div class="py-5 px-5" style="background: #596475">
        <h4 class="text-white">OUR CLIENTS</h4>
        <div class="row mt-3">
          <div
            v-for="(image, id) in images"
            :key="id"
            class="col-sm-6 col-md-4 col-lg-4 mb-2 py-4 d-flex justify-content-center"
          >
            <img
              class="image2 hover15"
              :src="require(`~/assets/image/${image.name}`)"
              alt=""
            />
          </div>
        </div>
      </div>
      <div id="contact" class="py-5 px-5" style="background: white">
        <h2 class="pb-5 d-flex justify-content-center">CONTACT</h2>
        <div class="row d-flex justify-content-center">
          <div class="col-md-8 col-md-offset-2">
            <div class="row">
              <div
                v-for="(contact, id) in contacts"
                :key="id"
                class="col-sm-6 col-md-6 col-lg-6"
              >
                <div class="row mb-3">
                  <div
                    id="contact-icon"
                    class="col-sm-3 col-lg-3 d-flex justify-content-end align-items-center pb-3"
                  >
                    <fa :icon="contact.icon" id="contact.icon" class="fa-2x" />
                  </div>
                  <div class="col-sm-9 col-lg-9">
                    <h4>
                      {{ contact.header }}
                    </h4>
                    <div v-if="contact.header === 'Call us'">
                      <div>
                        <a class="link" href="tel:+66850839976">
                          {{ contact.detail }}
                        </a>
                      </div>
                    </div>
                    <div v-if="contact.header === 'Address'">
                      {{ contact.detail }}
                    </div>
                    <div v-if="contact.header === 'Email'">
                      <div>
                        <a class="link" href="mailto:gameboyfun@hotmail.com">
                          {{ contact.detail }}
                        </a>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="row d-flex justify-content-center">
          <div class="col-md-8 col-md-offset-2">
            <b-form @submit="onSubmit">
              <div class="row mb-2">
                <div class="col-lg-6">
                  <b-form-input
                    class="mb-2"
                    id="name"
                    v-model="form.name"
                    type="text"
                    placeholder="Name"
                    required
                  />
                  <b-form-input
                    class="mb-2"
                    id="email"
                    v-model="form.email"
                    type="email"
                    placeholder="Email"
                    required
                  />
                  <b-form-input
                    class="mb-2"
                    id="telephone"
                    v-model="form.telephone"
                    type="tel"
                    placeholder="Tel"
                    required
                  />
                </div>
                <div class="col-lg-6">
                  <b-form-textarea
                    id="message"
                    v-model="form.message"
                    type="text"
                    placeholder="Message"
                    required
                    rows="5"
                  />
                </div>
              </div>
              <div class="row mb-2">
                <div class="col-lg-12">
                  <b-form-file
                    v-model="form.img"
                    accept="image/*"
                    placeholder="Choose an example file"
                    drop-placeholder="Drop file here..."
                    multiple
                  >
                    <template slot="file-name" slot-scope="{ names }">
                      <b-badge variant="dark">{{ names[0] }}</b-badge>
                      <b-badge
                        v-if="names.length > 1"
                        variant="dark"
                        class="ml-1"
                      >
                        + {{ names.length - 1 }} More files
                      </b-badge>
                    </template>
                  </b-form-file>
                </div>
              </div>
              <div class="d-flex justify-content-between">
                <div>
                  <fa :icon="['fas', 'info-circle']" id="information" /> All the
                  fields are required
                </div>
                <b-button type="submit" variant="primary">Submit</b-button>
              </div>
            </b-form>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar";
export default {
  data() {
    return {
      show: true,
      form: {
        name: "",
        email: "",
        telephone: "",
        message: "",
        img: null,
      },
      bgNav: "bgNavtrans",
      services: [
        {
          icon: ["fas", "globe-americas"],
          header: "SOCIAL MEDIA MARKETING",
          detail:
            "โฆษณาแบรนด์ของคุณผ่านช่องทาง Social ต่างๆ ตามที่คุณต้องการ อาธิ เช่น Facebook Instagram Line หรือ Youtube",
        },
        {
          icon: ["fas", "search"],
          header: "SEARCH ENGINE MARKETING",
          detail:
            "ทำให้ธุรกิจของคุณขึ้นสู่อันดับหนึ่งในการค้นหาทั้งรูปแบบ Adwords และ SEO ทำให้ผู้ใช้รู้จักคุณมากขึ้น ได้เปรียบคู่แข่งในโลกของธุรกิจ",
        },
        {
          icon: ["fas", "pencil-alt"],
          header: "CONTENT MARKETING",
          detail:
            "เขียน Content และตกแต่งรูปภาพให้เหมาะสมกับความต้องการ และรองรับ SEO ช่วยให้การตลาดของคุณน่าสนใจ ดึงดูดลูกค้ามากยิ่งขึ้น",
        },
        {
          icon: ["fas", "palette"],
          header: "WEB DESIGN",
          detail:
            "รับทำเว็บไซต์ด้วย Wordpress หรือออกแบบและพัฒนาใหม่ทั้งหมด พร้อมให้คำปรึกษา เพื่อให้เหมาะสมกับลักษณะธุรกิจของคุณ",
        },
        {
          icon: ["fas", "cogs"],
          header: "DEVELOPMENT",
          detail:
            "รับทำระบบตามความต้องการของคุณทั้งแอพพลิเคชัน และระบบภายในองค์กรตามความต้องการของคุณ ด้วยเทคโลโยีที่คุณต้องการ",
        },
        {
          icon: ["fas", "layer-group"],
          header: "PROGRAM",
          detail:
            "โปรแกรมสำเร็จรูปที่พร้อมติดตั้งให้คุณใช้งานภายใน 7 วันที่เหมาะกับทุกคนไม่ว่าคุณจะเริ่มต้นค้าขาย หรือเป็นแม่ค้ามือาชีพ",
        },
      ],
      workflow: [
        {
          icon: ["far", "comments"],
          header: "1. พูดคุย",
        },
        {
          icon: ["fas", "tools"],
          header: "2. ลงมือทำ",
        },
        {
          icon: ["fas", "trophy"],
          header: "3. ชนะคู่แข่ง",
        },
      ],
      images: [
        { name: "maxresdefault-1.jpg" },
        { name: "applelogo2.jpg" },
        { name: "google.jpg" },
        { name: "maxresdefault-1.jpg" },
        { name: "applelogo2.jpg" },
        { name: "google.jpg" },
      ],
      contacts: [
        {
          icon: ["fas", "phone-square"],
          header: "Call us",
          detail: "0850839976",
        },
        {
          icon: ["fas", "map-pin"],
          header: "Address",
          detail: "103/103 ม.2 ต.เสม็ด อ.เมืองชลบุรี จ.ชลบุรี 20000",
        },
        {
          icon: ["far", "envelope"],
          header: "Email",
          detail: "gameboyfun@homail.com",
        },
      ],
    };
  },
  methods: {
    handleScroll() {
      if (window.scrollY > 85) {
        this.bgNav = "bgNav";
      } else {
        this.bgNav = "bgNavtrans";
      }
    },
    async onSubmit(event) {
      event.preventDefault();
      let formData = new FormData();
      formData.append('name',this.form.name);
      formData.append('email',this.form.email);
      formData.append('telephone',this.form.telephone);
      formData.append('message',this.form.message);
      if (this.form.img) {
        for( var i = 0; i < this.form.img.length; i++ ){
          let file = this.form.img[i];
          formData.append('img', file);
        }
      }
      
      //log formdata
      // for (var pair of formData.entries()) {
      //   console.log(pair[0] + " - " + pair[1]);
      // }
      try {
        await this.$axios.post('/contact', formData,{ headers: {'Content-Type': 'multipart/form-data' }}).then(response => {
          if(response.status == 201) {
            this.$swal("Success", `${response.data}`, "success").then(result => {
              if (result.isConfirmed) {
                this.form.name = ''
                this.form.email = ''
                this.form.telephone = ''
                this.form.message = ''
                this.form.img = null
              }
            }) 
          }
        })
      } catch (error) {
        this.$swal(`${error.response.statusText}`, `${error.response.data}`, "error")
      }
    }
  },
  beforeMount() {
    window.addEventListener("scroll", this.handleScroll);
  },
  beforeDestroy() {
    window.removeEventListener("scroll", this.handleScroll);
  },
};
</script>

<style>
</style>
