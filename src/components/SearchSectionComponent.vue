<template>

  <section class="search">
    <div class="wrapper">
      <div class="search-content">
        <h2>Please select an image from your computer</h2>
        <div class="search-form">
          <div class="search-image">
            <label for="fileImage"><span>Browse</span></label>
            <input id="fileImage" type="file" accept=".jpg, .jpeg, .png" @change="showTextInput">
            <p class="pathElem"></p>
          </div>
          <button class="load" @click="save">Upload image</button>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "SearchSectionComponent",

  methods: {
    save(){
      let file1 = document.querySelector("#fileImage");
      let f = file1.files[0];
      if (f) {
        localStorage.setItem('myImage', URL.createObjectURL(f));
      }
      this.createCard();
      this.FollowImg();
      this.addScale();
    },

    showTextInput(){
      let inputLoad = document.querySelector("#fileImage");
      let valueInput = document.querySelector("p.pathElem");
      valueInput.innerText = inputLoad.value;

      let loadButton = document.querySelector("button.load");
      loadButton.addEventListener("click", () => {
        valueInput.innerText = "";
      });
    },



    createCard(){
      let cards = document.querySelector('.cards');

      let createDivCard = document.createElement('div');
      createDivCard.classList.add('card');

      createDivCard.innerHTML += `
      <figure class="cardAddScaleId add-input">
        <img class="image-step" src="${localStorage.getItem('myImage')}">
        <figcaption>10/20/ 2010</figcaption>
        <i class="search-icon fa-solid fa-magnifying-glass-plus"></i>
      </figure>
      <div class="card-info">
        <p>Lorem Ipsum is simply</p>
        <button class="btn-f">
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
        </div>`;
      cards.insertBefore(createDivCard, cards.firstChild);

    },

    addScale(){
      let image_step = document.querySelector(".image-step");
      let spanBg = document.querySelector(".bg-absolute");
      let body = document.querySelector("body");

      image_step.addEventListener("click", () => {
        let createBigImage = document.createElement("img");
        createBigImage.src = image_step.src;
        createBigImage.classList.add("image-step", "absoluteImg");

        spanBg.style.opacity = "0.7";
        spanBg.style.zIndex = "2";

        body.appendChild(createBigImage);
      })
    },

    FollowImg(){
      let cardInfo = document.querySelector(".card-info .btn-f");
      cardInfo.addEventListener("click", () => {
        cardInfo.classList.toggle("follow-card");
      });
    }
  }
}
</script>



<style scoped>


  section.search{
    padding: 40px 0 60px 0;
  }

  section.search .search-content{
    padding-left: 16%;
  }

  section.search h2{
    font-size: 28px;
    font-family: "HelveticaBold", sans-serif;
    margin-top: 0;
    color: #565555;
  }

  section.search .search-form{
    display: flex;
  }

  section.search .search-form .search-image{
    box-shadow: inset 0px 6px 12px -7px #b4b4b4;
    border: 1px solid #cacaca;
    width: 440px;
    padding: 5px;
    border-radius: 5px;
    display: flex;
    align-items: center;
    position: relative;
    overflow: hidden;
  }
  section.search .search-form .search-image input{
    width: 100%;
    height: 100%;
    order: 0;
    opacity: 0;
    cursor: pointer;
  }
  section.search .search-form .search-image .pathElem{
    margin: 0;
    position: absolute;
    left: 10px;
    top: 0%;
    transform: translate(0%, 80%);
    pointer-events: none;
    color:#565555;
  }
  section.search .search-form .search-image label{
    color: #fff;
    background: #c1bfbf;
    border: #c1bfbf 1px solid;
    border-radius: 5px;
    padding: 5px 11px;
    order: 1;
    font-size: 18px;
    font-family: "HelveticaRegular", sans-serif;
    z-index: 1;
  }
  section.search .search-form .load{
    background: linear-gradient(to top, #ff6700, #ffa400);
    padding: 10px 20px;
    color: #fff;
    font-size: 24px;
    font-family: "HelveticaBold", sans-serif;
    outline: #ff7d00;
    border: #ff7d00 1px solid;
    border-radius: 5px;
    margin-left: 14px;
  }

  @media screen and (max-width: 992px){
    section.search .search-content{
      padding: 0;
      margin: auto;
    }
  }

  @media screen and (max-width: 768px){
    section.search .search-form{
      display: block;
    }
    section.search .search-form .load{
      margin-left: 0px;
      margin-top: 10px;
    }
  }

  @media screen and (max-width: 480px){
    section.search h2{
      font-size: 22px;
    }
    section.search .search-form .search-image{
      width: 340px;
    }
  }




</style>