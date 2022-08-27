<template>
  <section>
    <div class="wrapper">
      <div class="cards">
        <div class="card" v-for="data in this.imagesPost" :key="data.id">
          <figure class="cardAddScaleId" @click="addScale">
            <img :src="data.src" alt="" class="image-step">
            <figcaption>{{ data.datePublished }}</figcaption>
            <i class="search-icon fa-solid fa-magnifying-glass-plus"></i>
          </figure>
          <div class="card-info">
            <p>{{ data.caption }}</p>
            <button class="btn-f" @click="FollowImg">
              <i class="fa-solid fa-star"></i>
            </button>
          </div>
          <hr>
          <div class="share">
            <span>Share</span>
            <a href="#"><i class="fars fa-brands fa-twitter"></i></a>
            <a href="#"><i class="fars fa-brands fa-facebook"></i></a>
            <a href="#"><i class="fars fa-brands fa-pinterest"></i></a>
            <a href="#"><i class="fars fa-brands fa-telegram"></i></a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>



export default {
  name: "CardsSection",
  props:{
    imagesPost:{
      type: Array,
    }
  },

  methods:{
    //
    addScale(e){
      let body = document.querySelector("body");
      let spanBg = document.querySelector(".bg-absolute");
      for (let i = 0; i <= e.path.length; i++){
        if(e.path[i].classList.contains("image-step")){
          let cardScale = e.path[i];

          let createBigImage = document.createElement("img");
          createBigImage.src = cardScale.src;
          createBigImage.classList.add("image-step", "absoluteImg");

          spanBg.style.opacity = "0.7";
          spanBg.style.zIndex = "2";

          body.appendChild(createBigImage);

          break;
        }
      }
    },
    FollowImg(e){
      let buttonClick = e.path[2];
      buttonClick.classList.toggle("follow-card");
    }
  }

}



</script>

<style>

.cards{
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 30px;
  padding-bottom: 50px;

}
.cards .card{
  padding: 6px;
  border: #d6d6d6 1px solid;
  box-shadow: #676666 0px 0px 6px -2px;
  max-height: 300px;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
}

.cards .card hr{
  background: #e0dfdf;
  color: #e0dfdf;
  border: #e0dfdf 1px solid;
  margin: 0;
}


.cards .card .card-info{
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 5px 5px 5px 10px;
}
.cards .card .card-info p {
  margin: 0;
  color: #979393;
  font-size: 15px;
}

.cards .card .card-info button.btn-f {
  background: #b1aeae;
  color: white;
  border-radius: 50%;
  border: none;
  padding: 5px;
}

.cards .card .card-info button.btn-f.follow-card {
  background: #ff7d00;
}

.fars {
  color: #b1aeae;
  font-size: 20px;
  transition: 200ms;
}
.fa-twitter:hover {
  color: #379cff;
}
.fa-facebook:hover {
  color: #003164;
}
.fa-pinterest:hover {
  color: #b20135;
}
.fa-telegram:hover {
  color: #379cff;
}





.cards .card .share{
  display: flex;
  justify-content: flex-end;
  padding: 10px 5px 5px 5px;
}
.cards .card .share a{
  margin: 0 2px;
}

.cards .card .share span{
  margin-right: 15px;
  font-size: 14px;
  color: #979393;
}

.cards .card figure{
  position: relative;
  margin: 0;
  height: 230px;
  overflow: hidden;
}
.cards .card figure img{
  object-fit: cover;
  width: 100%;
  height: 100%;


}

.cards .card figure figcaption{
  position: absolute;
  left: 5px;
  bottom: 10px;
  color: white;
  font-family: "HelveticaRegular", sans-serif;
}

.cards .card figure .search-icon {
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  opacity: 0;
  transition: 200ms;
  color: #fff;
  font-size: 25px;
  pointer-events: none;
}
.cards .card figure:hover > .search-icon{
  opacity: 1;
}


.absoluteImg {
  position: fixed;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  z-index: 3;
  max-width: 60vw;
  max-height: 60vh;
  width: auto;
  height: auto;
}


@media screen and (max-width: 992px){
  .cards{
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 15px;
    padding-bottom: 50px;

  }
}

@media screen and (max-width: 768px){
  .cards{
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 15px;
    padding-bottom: 50px;

  }
}

@media screen and (max-width: 480px){
  .cards{
    display: grid;
    grid-template-columns: repeat(1, 1fr);
    gap: 15px;
    padding-bottom: 50px;

  }
}

</style>