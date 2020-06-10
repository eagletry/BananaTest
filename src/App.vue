<template>
  <v-app class="display">
    <v-app-bar
      class="borderd"
      color="white"
      app
      light
      elevate-on-scroll
      flat
    >
        <v-toolbar-title style="padding:0px" class="title font-weight-bold">หน้าแรก</v-toolbar-title>

        <v-spacer></v-spacer>
        <v-btn text fab>
        <v-icon color="#42A5F5"> mdi-star-four-points-outline</v-icon>
        </v-btn>
    </v-app-bar>

    <v-divider></v-divider>

    <!-- <v-layout >
      <v-flex > -->

    <v-navigation-drawer
      permanent
      light
      app
      width="320"
      v-model="drawer"
      :mini-variant="isMobile"
      mini-variant-width = "80"
    >

    <v-list-tile>

      <v-list v-if="!isMobile" :class="isMobile && 'px-0'">
      <div class="ml-10">

        <v-btn fab light text color="#42A5F5" >
       <v-icon medium>mdi-twitter</v-icon>
       </v-btn>

      </div>
      </v-list>

      <v-list v-else :class="isMobile && 'px-0'">
      <div class="ml-3">

        <v-btn fab light text color="#42A5F5" >
       <v-icon medium>mdi-twitter</v-icon>
       </v-btn>

      </div>
      </v-list>

    </v-list-tile>

    <v-item-group v-if="!isMobile"  mandatory class="ml-10 mr-5">

    <v-list v-for="list in lists" :key="list.text">

      <v-item v-slot:default="{ active, toggle }">
      <!-- <v-col cols="2"> -->
      <v-btn
      rounded
      text
      light
      class="title font-weight-bold hove"
      :color="active ? '#42A5F5' : ''"
      @click="toggle"
      >

            <v-list-icon>
              <v-icon medium>{{ list.icon }}</v-icon>
            </v-list-icon>

            <v-list-content class="ml-5 mr-5">
              <v-list-title >{{ list.text }}</v-list-title>
            </v-list-content>

      </v-btn>
      <!-- </v-col> -->
</v-item>
    </v-list>

    </v-item-group>

    <v-item-group v-else mandatory class="ml-5">

    <v-list v-for="list in lists" :key="list.text">

      <v-item v-slot:default="{ active, toggle }">
      <!-- <v-col cols="2"> -->
      <v-btn
      icon
      rounded
      text
      light
      class="title font-weight-bold hove"
      :color="active ? '#42A5F5' : ''"

      @click="toggle"
      >

            <v-list-icon>
              <v-icon medium>{{ list.icon }}</v-icon>
            </v-list-icon>

      </v-btn>
      <!-- </v-col> -->
</v-item>
    </v-list>

    </v-item-group>

    <v-list  v-if="!isMobile" class="ml-10 mr-5">

    <v-btn
      rounded
      color="#42A5F5"
      dark
      class="font-weight-bold mr-10"
      block
      >
      ทวีต
      </v-btn>
    </v-list>

    <v-list  v-else class="ml-3 ">
     <v-btn
      fab
      rounded
      light
      color="#42A5F5"

      class="title font-weight-bold"
      @click="toggle"
      >
              <v-icon dark color="white" >mdi-pencil-plus-outline</v-icon>

      </v-btn>
    </v-list>

    <v-list v-if="!isMobile" class="ml-10 mr-5">
    <!-- <v-btn  @click="show = !show">USERNAME</v-btn> -->

    <v-menu
              bottom
              top
              offset-y
            >
              <template v-slot:activator="{ on }">
              <!-- New Import -->

  <v-card
    flat
    max-width="500"
    class="mx-0 mt-2"
    style="border-radius: 50px"
  >

  <v-list two-line>
      <template v-for="item in item2" >

        <v-list-item
          :key="item.title"
          @click="doSomething()"
          v-on="on"
        >
          <v-list-item-avatar>
            <v-img :src="item.avatar"></v-img>
          </v-list-item-avatar>

          <v-list-item-content>
            <v-list-item-title class="font-weight-bold" v-html="item.title"></v-list-item-title>
            <v-list-item-subtitle v-html="item.subtitle"></v-list-item-subtitle>
          <v-spacer></v-spacer>
          </v-list-item-content>

          <v-icon rounded class="font-weight-bold" light >mdi-chevron-down</v-icon>
        </v-list-item>

      </template>
    </v-list>

  </v-card>
              <!-- New Import -->
              </template>

      <v-list>

      <template v-for="item in item2" >
        <v-list-item
          :key="item.title"
        >
          <v-list-item-avatar>
            <v-img :src="item.avatar"></v-img>
          </v-list-item-avatar>

          <v-list-item-content>
            <v-list-item-title class="font-weight-bold" v-html="item.title"></v-list-item-title>
            <v-list-item-subtitle v-html="item.subtitle"></v-list-item-subtitle>
          <v-spacer></v-spacer>


          </v-list-item-content>
          <v-icon color="#42A5F5">mdi-check</v-icon>
          <!-- <v-btn rounded text outlined class="font-weight-bold" color="primary" style="border: 1px solid currentColor;"> ติดตาม</v-btn> -->
        </v-list-item>

      </template>
                <v-list-item
                  v-for="(item, i) in Dialog"
                  :key="i"
                  @click="() => {}"
                >

                  <v-list-item-title
                  v-for="(UserAccount,j) in item2"
                  :key="j"
                  >
                    {{ item.title }}
                    <v-text v-if="item.check">
                      {{UserAccount.subtitle}}
                    </v-text>

                    </v-list-item-title>

                </v-list-item>
              </v-list>
            </v-menu>

    </v-list>
    </v-navigation-drawer>

<!-- start Right -->

<v-navigation-drawer

      class="scroll"
      light
      app
      right
      width="430"
    >

<v-app-bar flat light shrink-on-scroll color="white">
     <v-text-field
            class="mx-1 mt-2 mr-6"
            solo
            label="ค้นหาทวิตเตอร์"
            light
            rounded
            flat
            dense
            background-color="#f5f8fa"
            prepend-inner-icon="mdi-magnify"
      >
      </v-text-field>
</v-app-bar>

<v-list>
<v-card
    max-width="500"
    class="mx-5 mt-2 mr-10"
    style="border-radius: 20px"
    color="#f5f8fa"
    flat
  >
    <v-toolbar
      light
      flat
      color="#f5f8fa"
    >

      <v-toolbar-title class="title font-weight-bold">ความนิยมสำหรับคุณ</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon color="#42A5F5">mdi-cog-outline</v-icon>
      </v-btn>

    </v-toolbar>
    <v-divider></v-divider>
  <v-list three-line>
      <template v-for="right in rightnav" >

        <v-divider
          v-if="right.divider"
          :key="right.text"
        ></v-divider>

        <v-list-item
          v-else
          :key="right.tag"
          @click="doSomething()"
        >

          <v-list-item-content>
            <!-- <v-list-item-subtitle v-html="right.tag"></v-list-item-subtitle>
            <v-list-item-title class="font-weight-bold" v-html="right.text"></v-list-item-title>
            <v-list-item-subtitle v-html="right.Tweet"></v-list-item-subtitle> -->
            <v-list-item-subtitle class="caption font-weight-thin">{{right.tag}}</v-list-item-subtitle>
            <v-list-item-title class="font-weight-bold">{{right.text}}</v-list-item-title>
            <v-list-item-subtitle>{{right.Tweet}}</v-list-item-subtitle>

          <v-spacer></v-spacer>

          </v-list-item-content>
 <!-- <v-icon rounded class="font-weight-bold" light >mdi-chevron-down</v-icon> -->
        <!-- Dropdown ความนิยมสำหรับคุณ -->
  <v-menu
      bottom
      left
  >
  <template v-slot:activator="{ on }">

  <v-btn fab light small text top right class="hove">
        <!-- <v-icon small> mdi-chevron-down</v-icon> -->

      <template v-for="item in item2">
        <v-list-item
          :key="item.title"
          @click="doSomething()"
          v-on="on"
        >
          <v-icon rounded light class="title font-weight-thin">mdi-chevron-down</v-icon>
        </v-list-item>

      </template>


  </v-btn>
              <!-- New Import -->
      </template>

      <v-list>
                <v-list-item
                  v-for="(item, i) in Report"
                  :key="i"
                  @click="() => {}"
                >
                <v-list-icon>
                  <v-icon>
                  {{item.icon}}
                  </v-icon>
                </v-list-icon>

                <v-list-item-title class="body-2 ml-2">
                  {{ item.reports }}
                  </v-list-item-title>
                </v-list-item>
              </v-list>
            </v-menu>

        <!-- Dropdown ความนิยมสำหรับคุณ -->

        </v-list-item>

      </template>
    </v-list>

    <v-btn
      text
      rounded
      light
      color="#42A5F5"
      class="font-weight-bold"
      >
      <v-text>
        แสดงเพิ่มเติม
      </v-text>
      </v-btn>

  </v-card>
</v-list>

<!-- Accout -->

<v-list>
<v-card
    max-width="500"
    class="mx-5 mt-2 mr-10"
    style="border-radius: 20px"
    color="#f5f8fa"
    flat
  >
    <v-toolbar
      light
      flat
      color="#f5f8fa"
    >

      <v-toolbar-title class="title font-weight-bold">ติดตามใครดี</v-toolbar-title>

      <!-- <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn> -->

    </v-toolbar>
    <v-divider></v-divider>

  <v-list two-line>
      <template v-for="(item, index) in items" >

        <v-divider
          v-if="item.divider"
          :key="index"
        ></v-divider>

        <v-list-item
          v-else
          :key="item.title"
          @click="doSomething()"
        >
          <v-list-item-avatar>
            <v-img :src="item.avatar"></v-img>
          </v-list-item-avatar>

          <v-list-item-content>
            <v-list-item-title class="font-weight-bold" v-html="item.title"></v-list-item-title>
            <v-list-item-subtitle v-html="item.subtitle"></v-list-item-subtitle>
          <v-spacer></v-spacer>
          </v-list-item-content>

          <v-btn rounded text outlined class="font-weight-bold" color="#42A5F5" style="border: 1px solid currentColor;"> ติดตาม</v-btn>
        </v-list-item>

      </template>
    </v-list>

    <v-btn
      text
      rounded
      light
      color="#42A5F5"
      class="font-weight-bold"
      >
        แสดงเพิ่มเติม
      </v-btn>

  </v-card>
</v-list>
    </v-navigation-drawer>

    <v-content>
      <HelloWorld/>
    </v-content>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld';

export default {
  name: 'App',

  components: {
    HelloWorld,
  },

  data:() => ({
    show: false,
    drawer:true,
    lists: [
      {icon: "mdi-home",text: "หน้าแรก"},
      {icon: "mdi-pound",text: "สำรวจ"},
      {icon: "mdi-bell-outline",text: "แจ้งเตือน"},
      {icon: "mdi-email-outline",text: "ข้อความ"},
      {icon: "mdi-bookmark-outline",text: "บุ๊กมาร์ก"},
      {icon: "mdi-text-box-outline",text: "รายชื่อ"},
      {icon: "mdi-account-outline",text: "ข้อมูลส่วนตัว"},
      {icon: "mdi-dots-horizontal-circle-outline",text: "เพิ่มเติม"}
    ],
    miniVariant: false,
    rightnav: [
      {tag:"ได้รับความนิยมในไทย",text:"#ยกเลิก112",Tweet:"100K ทวีต"},
      { divider: true},
      {tag:"ได้รับความนิยมในไทย",text:"#WhoAreYouEP12",Tweet:"50K ทวีต"},
      { divider: true},
      {tag:"ได้รับความนิยมในไทย",text:"#โบ๊ะบ๊ะแฟมิลี่",Tweet:"30K ทวีต"},
      { divider: true},
    ],
   items: [
        {
          avatar: require('./assets/Lisa.jpg'),
          title: 'BLACKPINK LISA 리사',
          subtitle: "@lalaIalisaa_m",
        },
        { divider: true},
        {
          avatar: require('./assets/HRK.jpg'),
          title: 'พี่เป็นนักยูทูป',
          subtitle: "@MisterHeartz",
        },
        { divider: true},
        {
          avatar: require('./assets/Artgerm.jpg'),
          title: 'Stanley Artgerm Lau',
          subtitle: "@Artgerm",
        },
        { divider: true},
      ],
      item2: [
         {
          avatar: require('./assets/UserTwitter.png'),
          title: 'Username',
          subtitle: "@User_Login",
        },
      ],
      Dialog: [
        { title: "เพิ่มบัญชีที่มีอยู่แล้ว" },
        { title: "ออกจากระบบ" ,check: true},
      ],
      Report: [
        { icon: "mdi-emoticon-sad-outline" ,reports: "ความนิยมนี้เป็นแสปม"},
        { icon: "mdi-emoticon-sad-outline" ,reports: "ความนิยมนี้ไม่เหมาะสมหรือเป็นอันตราย"},
        { icon: "mdi-emoticon-sad-outline" ,reports: "ความนิยมนี้มีความเหมือนกัน"},
        { icon: "mdi-emoticon-sad-outline" ,reports: "ความนิยมนี้มีคุณภาพต่ำ"},
      ],
      windowWidth: window.innerWidth,
    //New Data
    //
  }),

  mounted() {
    window.addEventListener("resize", () => {
      this.windowWidth = window.innerWidth;
    });
  },
  computed: {
    isMobile() {
      return this.windowWidth <= 800;
    },
  },
};
</script>

<style scoped>
  .hove:hover{
    color: #42A5F5
  }
</style>

<style>
.scroll .v-navigation-drawer__content::-webkit-scrollbar {
  display: none;
}
.borderd .v-toolbar__content{
  border-bottom: 1px solid #E0E0E0;
}
</style>