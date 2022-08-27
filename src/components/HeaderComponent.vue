<template>
  <header class="head">
    <div class="wrapper">
      <nav class="nav">
        <a href="#" class="title"><span>Photo</span>Cage app</a>
        <ul>
          <li class="list-item">
            <a href="#">
              <img src="../assets/images/nav-icon1.png">
              <span>Home</span>
            </a>
          </li>
          <li class="list-item active">
            <a href="#">
              <img src="../assets/images/nav-icon2.png">
              <span>Gallery</span>
            </a>
          </li>
          <li class="list-item">
            <a href="#">
              <img src="../assets/images/nav-icon3.png">
              <span>Members</span>
            </a>
          </li>
          <li class="list-item">
            <a href="#">
              <img src="../assets/images/nav-icon4.png">
              <span>Logout</span>
            </a>
          </li>
        </ul>
      </nav>
    </div>
  </header>
</template>

<script>
export default {
  name: "HeaderComponent"
}
</script>

<style scoped>
.head{
  border-bottom: 1px solid #cccccc;
  background: linear-gradient(to top, #e0e0e0, #ffffff);
}



.head .wrapper .nav{
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0px 25px;
}

.head .wrapper .nav a.title{
  text-decoration: none;
  color: #676666;
  font-family: "Lobster", sans-serif;
  font-size: 49px;
}
.head .wrapper .nav a.title span{
  color: #ff7700;
}

.head .wrapper .nav ul{
  display: flex;
  list-style: none;
  width: auto;
  padding: 0;
  margin: 0;
  height: 100%;
  align-self: flex-end;
}


.head .wrapper .nav ul li.list-item{
  text-align: center;
  padding: 24px 20px 20px 20px;
  border-right: 1px solid linear-gradient(to top, #dcdcdc, #ffffff);

}
.head .wrapper .nav ul li.list-item:last-child{
  border-right: none;
}

.head .wrapper .nav ul li.list-item.active{
  border-bottom: 4px solid #ff7d00;
  background: linear-gradient(to top, #cac2c2, #ffffff);
}

.head .wrapper .nav ul li.list-item a{
  text-decoration: none;
}
.head .wrapper .nav ul li.list-item a span{
  display: block;
  font-family: "HelveticaLight", sans-serif;
  color: #545454;
  font-size: 16px;

}



@media screen and (max-width: 768px){
  .head .wrapper .nav a.title{
    font-size: 35px;
    text-align: center;
    order: 2;
    padding: 20px 0;
  }
  .head .wrapper .nav ul{
    order: 1;
  }

  .head .wrapper .nav{
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 0px;
    flex-direction: column;

  }
}



</style>