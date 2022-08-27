<template>
  <span class="bg-absolute" @click="hideSpanBg"></span>
  <HeaderComponent />

  <main class="page-content">
      <SearchSectionComponent @createCardTag="this.localStorage1"/>
      <CardsSection :imagesPost="this.imagesPost" />
  </main>

  <footer class="footer">
    <div class="wrapper">
      <h6>© 2013 Photocage app  powered by cssauthor.com</h6>
    </div>
  </footer>


</template>




<script>
import HeaderComponent from './components/HeaderComponent.vue';
import SearchSectionComponent from './components/SearchSectionComponent.vue';
import CardsSection from './components/CardsSection.vue';


export default {
  name: 'App',
  components: {
    HeaderComponent, SearchSectionComponent, CardsSection
  },
  data: () => ({
    imagesPost: [
      {id: "1", src:"https://picsum.photos/seed/picsum/200/200", datePublished: "10/08/ 2010",
        caption: "Lorem Ipsum is simply", isFollow: true},
      {id: "2", src:"https://picsum.photos/id/234/400/300", datePublished: "10/08/ 2010",
        caption: "Lorem Ipsum is simply", isFollow: true},
      {id: "3", src:"https://picsum.photos/id/223/400/300", datePublished: "10/08/ 2010",
        caption: "Lorem Ipsum is simply", isFollow: true},
      {id: "4", src:"https://picsum.photos/id/211/500/500", datePublished: "10/08/ 2010",
        caption: "Lorem Ipsum is simply", isFollow: true},
      {id: "5", src:"https://picsum.photos/id/237/400/600", datePublished: "10/08/ 2010",
        caption: "Lorem Ipsum is simply", isFollow: true},
      {id: "6", src:"https://picsum.photos/id/225/400/400", datePublished: "10/08/ 2010",
        caption: "Lorem Ipsum is simply", isFollow: true},
      {id: "7", src:"https://picsum.photos/id/212/400/500", datePublished: "10/08/ 2010",
        caption: "Lorem Ipsum is simply", isFollow: true},
    ],
    localStorage1: ""
  }),
  methods:{
    hideSpanBg(){
      let spanBg = document.querySelector(".bg-absolute");
      spanBg.style.opacity = "0";
      spanBg.style.zIndex = "-1";
      let ablosuteImg = document.querySelector(".absoluteImg")
      ablosuteImg.remove()
    }
  }
}
</script>

<style>



body{
  margin: 0;
  padding: 0;
  font-family: "HelveticaRegular", sans-serif;
}

.wrapper{
  max-width: 1024px;
  margin: auto;
}

.footer{
  padding: 10px 0;
  text-align: end;
  font-size: 17px;
  color: #8b8a8a;
  font-family: "HelveticaLight", sans-serif;
}

span.bg-absolute{
  position: fixed;
  width: 100vw;
  height: 100vh;
  background: #000;
  z-index: -1;
  opacity: 0;
  display: block;
}





@font-face {
  font-family: "Lobster";
  src: url("../src/assets/font/Lobster/Lobster-Regular.ttf") format("truetype");
  font-weight: normal;
  font-style: normal;
}

@font-face {
  font-family: "HelveticaBold";
  src: url("../src/assets/font/Helvetica/helvetica_bold.otf") format("opentype");
  font-weight: bold;
  font-style: normal;
}
@font-face {
  font-family: "HelveticaRegular";
  src: url("../src/assets/font/Helvetica/helvetica_regular.otf") format("opentype");
  font-weight: normal;
  font-style: normal;
}

@font-face {
  font-family: "HelveticaLight";
  src: url("../src/assets/font/Helvetica/helvetica_light.otf") format("opentype");
  font-weight: 200;
  font-style: normal;
}


@media screen and (max-width: 992px){
  .wrapper{
    max-width: 768px;
    margin: auto;
    padding: 0 15px;
  }
}
@media screen and (max-width: 768px){
  .wrapper{
    max-width: max-content;
    margin: auto;
  }
}
</style>
