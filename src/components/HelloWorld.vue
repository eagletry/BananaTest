<template>

  <v-container style="padding:0px">
    <!-- Post -->
  <v-form
    ref="form"
    v-model="valid"
  >
  <v-list dense style="padding:0px;">
    <v-list-item two-line>

      <v-list-item-avatar dense style="padding:0px ;margin-top:1px">
       <v-img
          :src="require('../assets/UserTwitter.png')"
       />
      </v-list-item-avatar>

    <v-list-item-content dense style="padding:0px; margin:0px">
    <v-text-field
    class="title font-weight-thin "
      light
      solo
      flat
      dense
      :rules="nameRules"
      placeholder="มีอะไรเกิดขึ้นบ้าง"
    ></v-text-field>
    </v-list-item-content>
  </v-list-item>



  <v-list-item dense>
     <v-layout-row class="ml-12">
     <v-list-item-action
        style="margin-right:0px ;margin-left:0px"
        v-for="item in icons"
        :key="item.text"
      >

      <v-btn icon fab dark small color="#42A5F5" >
      <v-icon >{{item.icon}}</v-icon>
      </v-btn>

    </v-list-item-action>

    </v-layout-row>
    <v-spacer></v-spacer>
    <v-btn dark color="#42A5F5" class="mr-5" rounded >
        ทวีต
    </v-btn>
  </v-list-item>
  </v-list>

  <v-divider></v-divider>

  <div style="height:10px; background-color:#f5f8fa">

  </div>

  </v-form>
  <v-divider></v-divider>

    <!-- Pose -->

    <!-- Status -->
  <v-form
    ref="form"
    v-model="valid"

  >
  <v-list v-for="(list,index) in content" :key="index" style="padding:0px">
    <div  @click="doSomething()">
    <v-list-item v-if="index != 4">

      <v-list-item-avatar style="padding:0px ">
       <v-img
          :src="list.avatar"
       />
      </v-list-item-avatar>

    <v-list-item-content three-line>

            <v-list-item-subtitle class="caption font-weight-thin">
              <v-icon v-if="list.tweetby != ''" small>mdi-twitter-retweet</v-icon>
              {{list.tweetby}}
              </v-list-item-subtitle>



            <v-list-item-title class="subtitle font-weight-bold">{{list.Account}}

            <v-text class="ml-2 subtitle font-weight-light">{{list.link}}</v-text>
              •
             <v-text class=" subtitle font-weight-light">{{list.time}}</v-text>

                <v-btn icon rounded class="font-weight-bold " light >
                  <v-icon>mdi-chevron-down</v-icon>
                  </v-btn>

              </v-list-item-title>


            <v-list-item-title class="text-wrap">
               {{list.text}}

            </v-list-item-title>



    </v-list-item-content>

  </v-list-item>
    </div>

  <v-list-item v-if="list.image != '' && index != 4" class="ml-12 mr-5">
    <v-card  flat>
    <v-img :src="list.image"/>
    </v-card>
  </v-list-item>


  <v-list-item v-if="index != 4" class="ml-10" >
    <v-col v-for="list in posticon"
        :key="list.text">
     <v-list-item-action>
       <v-row >
         <div>
          <v-btn rounded text :class="list.text">
        <v-btn
                icon
                light small
                >
          <v-icon>{{list.icon}}</v-icon>
        </v-btn>

        <v-text class="caption">{{list.tweet}}</v-text>
           </v-btn>
        </div>

       </v-row>
    </v-list-item-action>
    </v-col>
  </v-list-item>
  <v-divider></v-divider>

<!-- ติดตาม -->


  <v-list v-if="list.follow == true" style="padding-top:0 ;padding-bottom:0" >

    <div style="height:10px; background-color:#f5f8fa">

  </div>

  <v-list two-line>
     <v-toolbar-title class="ml-5 my-2 title font-weight-bold">ติดตามใครดี
        <v-btn icon>
        <v-icon>mdi-chevron-down</v-icon>
      </v-btn>
     </v-toolbar-title>



      <v-divider></v-divider>

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
      block
      light
      color="#42A5F5"
      class="font-weight-bold"
      >
        แสดงมากขึ้น
      </v-btn>
      <v-divider></v-divider>
      <div style="height:10px; background-color:#f5f8fa">

  </div>

  </v-list>

<!-- ติดตาม -->


  </v-list>

  </v-form>

    <!-- Status -->
  </v-container>
</template>


<script>
  export default {
  name: 'HelloWorld',
    data: () => ({
      icons: [
        {icon: "mdi-image", text: "Image"},
        {icon: "mdi-gif", text: "GIF"},
        {icon: "mdi-poll-box-outline", text: "Poll"},
        {icon: "mdi-emoticon-happy-outline", text: "Happy"},
        {icon: "mdi-calendar-refresh-outline", text: "Calender"},
      ],
      content: [
        {
        avatar: require('../assets/Lisa.jpg'),
        tweetby: "ไอคอนกำลังเข้าเมือง ได้รีทวีต",
        Account:"BLACKPINK LISA 리사",
        link: "@lalaIalisaa_m",
        time:'1 ชม.',
        text:"Guys don't forget to follow blackpink and also the members on Mubeat app, and collect heart beats! Download now guys..",
        image: require('../assets/lisapose.jpg'),
        },

        {
        avatar: require('../assets/HRK.jpg'),
        tweetby: "ไอคอนกำลังเข้าเมือง ได้รีทวีต",
        Account:"พี่เป็นนักยูทูป",
        link: "@MisterHeartz",
        time:'2 ชม.',
        text:"เอางี้ก่อนนะ ผมไม่ได้ว่าคนที่เรียกร้องให้ผมออกมาแสดงอะไรบางอย่างนะ เพราะผมเข้าใจเจตนาจริง ๆ อันนี้อย่าเข้าใจผมผิดน้า ผมแค่ว่าคนที่ด่าเปิดหัวผมก่อนเลยเฉย ๆ แบบน้อยใจอะไรงี้ เอาแบบนี้มั้ย ผมเปิดโอกาสให้ถามใต้ทวีตนี้ดีกว่าผมจะลองตอบดู  อยากปรับความเข้าใจกันมากเลย TT",
        image:"",
        },
        {
        avatar: require('../assets/Artgerm.jpg'),
        tweetby: "",
        Account:"Stanley Artgerm Lau",
        link: "@Stanley Artgerm Lau",
        time:'5 ชม.',
        text:"Alright. Took a moment to add some colors to this. :) #sailormoon #sailormoonredraw",
        image: require('../assets/Artgermpose.jpg'),
        },
        {
        avatar: require('../assets/six.jpg'),
        tweetby: "ไอคอนกำลังเข้าเมือง ได้รีทวีต",
        Account:"SIXMOREVODKA",
        link: "@sixmorevodka",
        time:'5 ชม.',
        text:"We published a truckload of art from Rising Tides on our website, as well as concepts and sketches for the new cards.",
        image: require('../assets/monika.jpg'),
        },
        {follow: true},
         {
        avatar: require('../assets/ekko.jpg'),
        tweetby: "",
        Account:"League of Legends",
        link: "@LeagueOfLegends",
        time:'10 ชม.',
        text:"Patch 10.11 Highlights",
        image: require('../assets/lolastro.jpg'),
        },
         {
        avatar: require('../assets/porter.jpg'),
        tweetby: "ไอคอนกำลังเข้าเมือง ได้รีทวีต",
        Account:"porter robinson",
        link: "@porterrobinson",
        time:'20 ชม.',
        text:"GET YOUR WISH (OFFICIAL MUSIC VIDEO)",
        image: require('../assets/getyourwish.jpg'),
        },
      ],
      posticon: [
        {text:"comment" ,styles:"comment", icon:"mdi-comment-outline", tweet:"59K"},
        {text:"retweet" ,styles:"retweet", icon:"mdi-twitter-retweet", tweet:"61K"},
        {text:"heart" ,styles:"heart", icon:"mdi-heart-outline", tweet:"70K"},
        {text:"shared" ,styles:"shared", icon:"mdi-export-variant"},
      ],
      items: [
        {
          avatar: require('../assets/ilya.jpg'),
          title: 'イリヤ・クブシノブ',
          subtitle: "@Kuvshinov_Ilya",
        },
        { divider: true},
        {
          avatar: require('../assets/vanoss.jpg'),
          title: 'VanossGaming',
          subtitle: "@VanossGaming",
        },
        { divider: true},
        {
          avatar: require('../assets/ape.jpg'),
          title: 'ConcernedApe',
          subtitle: "@ConcernedApe",
        },
        { divider: true},
      ],

   }),
};
</script>

<style scoped>
  .comment:hover{
    color: #42A5F5
  }
  .retweet:hover{
    color: #4CAF50
  }
  .heart:hover{
    color: #F06292
  }
  .shared:hover{
    color: #42A5F5
  }
</style>

