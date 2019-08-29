<template>
  <div id="app">
    <div class="body_view">
 <div id="myCarousel" class="carousel slide" data-ride="carousel">

  <!-- Indicators
  <ul class="carousel-indicators">
    <li data-target="#myCarousel" data-slide-to="0" class="active"></li>
    <li data-target="#myCarousel" data-slide-to="1"></li>
    <li data-target="#myCarousel" data-slide-to="2"></li>
  </ul>-->
  
  <!-- The slideshow -->
  <div class="carousel-inner">
    <div v-for="slider in sliders" class="carousel-item"  v-bind:class="{ 'active' : slider.active}">
      <img v-bind:src=" slider.image "  height="500" />
       <div class="img" style="background-image: url(/static/img/slider1.9ec6939.jpg);"></div>
    </div>
  </div>
  
  <!-- Left and right controls
  <a class="carousel-control-prev" href="#myCarousel" data-slide="prev">
    <span class="carousel-control-prev-icon"></span>
  </a>
  <a class="carousel-control-next" href="#myCarousel" data-slide="next">
    <span class="carousel-control-next-icon"></span>
  </a>-->
</div>
<div class="container">
    <nav class="navbar navbar-expand-sm  navbar-dark">
    <a class="navbar-brand" href="#">{{ mainLogo }}</a>

    <!-- Toggler/collapsibe Button -->
  <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#collapsibleNavbar">
    <span class="navbar-toggler-icon"></span>
  </button>

    <div class="collapse navbar-collapse mt-2 mt-md-0" id="collapsibleNavbar" style="justify-content: flex-end;">
    <ul class="navbar-nav">
      <li v-for="mi in mainItems" class="nav-item">
        <a class="nav-link" v-bind:href=" mi.herf " >{{ mi.title }}</a>
      </li>

      <li class="nav-item dropdown clickLang" >
          <a class="nav-link dropdown-toggle" href=" " id="dropdown01" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">{{ langMain }}</a>
          <div class="dropdown-menu" aria-labelledby="dropdown01">
            <a v-for="lang in langItem" class="dropdown-item" href="#" v-on:click="clickLang(lang)">{{ lang }}</a>
          </div>
        </li>

    </ul>
    </div>
  </nav>
<div class="navbar-toggleable-md collapse show head" aria-expanded="true" style="">
  <ul class="nav text-md-center justify-content-md-between">
              <li v-for="mti in mainTwoItems" class="nav-item dropdown" >
                <a class="nav-link dropdown-toggle" v-href=" mti.href " id="dropdown01" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">{{ mti.title }}</a>
                <div class="dropdown-menu" aria-labelledby="dropdown01">
                  <a v-for=" mtii in mti.items " class="dropdown-item" v-href=" mtii.href ">{{ mtii.title }}</a>
                </div>
              </li>
              
              <li class="nav-item cart">
                <span class="cricle"><i class="fa fa-shopping-cart" aria-hidden="true"></i></span><span>{{ cartName }}</span>
              </li>
            </ul>
           </div>

    <router-view/>

</div>
</div>
  </div>
</template>

<script>
export default {
  name: 'App',
    data () {
    return {
      mainLogo : 'ДОБРИВО',
      mainItems : [
        {title: 'ОПЛАТА И ДОСТВКА', href:'#'},
        {title: 'НОВОСТИ', href:'#'},
        {title: 'СПРАВОЧНИК', href:'#'},
        {title: 'СЕРТИФИКАТЫ', href:'#'}
      ],
      mainTwoItems:[
        {title:'НАГРО-УДОБРЕНИЕ', href:'#', items:[
          {title:'НАГРО-УДОБРЕНИЕ 1', href:'#'},
          {title:'НАГРО-УДОБРЕНИЕ 2', href:'#'},
          {title:'НАГРО-УДОБРЕНИЕ 3', href:'#'},
        ]},
        {title:'БИОДИЗЕЛЬ', href:'#', items:[
          {title:'БИОДИЗЕЛЬ 1', href:'#'},
          {title:'БИОДИЗЕЛЬ 2', href:'#'},
          {title:'БИОДИЗЕЛЬ 3', href:'#'},
        ]},
        {title:'СИЛКО', href:'#', items:[
          {title:'СИЛКО 1', href:'#'},
          {title:'СИЛКО 2', href:'#'},
          {title:'СИЛКО 3', href:'#'},
        ]},
        {title:'ИНТЕРНЕТ-МАГАЗИН', href:'#', items:[
          {title:'ИНТЕРНЕТ-МАГАЗИН 1', href:'#'},
          {title:'ИНТЕРНЕТ-МАГАЗИН 2', href:'#'},
          {title:'ИНТЕРНЕТ-МАГАЗИН 3', href:'#'},
        ]},
        {title:'ВОПРОСЫ-ОТВЕТЫ', href:'#', items:[
          {title:'ВОПРОСЫ-ОТВЕТЫ 1', href:'#'},
          {title:'ВОПРОСЫ-ОТВЕТЫ 2', href:'#'},
          {title:'ВОПРОСЫ-ОТВЕТЫ 3', href:'#'},
        ]},
        {title:'КОНТАКТЫ', href:'#', items:[
          {title:'КОНТАКТЫ 1', href:'#'},
          {title:'КОНТАКТЫ 2', href:'#'},
          {title:'КОНТАКТЫ 3', href:'#'},
        ]},
      ],
      sliders: [
        { title: 'Slider 1', image: require('@/assets/slider1.jpg'), active:true },
        { title: 'Slider 2', image: require('@/assets/slider2.jpg'), active:false },
        { title: 'Slider 3', image: require('@/assets/slider3.jpg'), active:false },
        { title: 'Slider 4', image: require('@/assets/slider4.jpg'), active:false },
      ],
      cartName : 'КОРЗИНА',
      langItem:['RU', 'UA', 'EN'],
      langMain:'RU'
    }
  },
  methods:{
    clickLang:function(lang){
      this.langMain = lang;
    }
  },
  mounted () {
    $('#myCarousel .carousel-item img').each(function(){
      var getSrc = $(this).attr('src');
      $(this).hide();
      $(this).closest('.carousel-item').find('.img').css({'background-image': 'url('+getSrc+')'});
    });

  }
}
</script>

<style>
@import url(http://fonts.googleapis.com/css?family=Roboto:400,100,100italic,300,300ita‌​lic,400italic,500,500italic,700,700italic,900italic,900);
html, body, html * {
  font-family: 'Roboto', sans-serif;
}

#app {

}

.navbar {        margin-top: 42px;
    padding: 0;padding-bottom: 0px;}
.navbar-brand{
   /* color: #000;*/
    font-size: 44px;
    font-weight: 600;
    padding-bottom: 0px;
}
.navbar-dark .navbar-nav .nav-link{
  color: #fff;
    font-size: 12px;
    cursor: pointer;
}
.head{
    border: 1px solid #afafaf;
    margin: 2px 0;
    box-shadow: 0px 1px 5px 0 #989797;
    background-color: #fff;
}
.head .dropdown .dropdown-toggle::after {
  transform: rotate(-90deg);
}
.head .dropdown.show .dropdown-toggle::after {
  transform: rotate(0deg);
}
.cart{
  padding: 12px 49px;
  cursor: pointer;
  font-size: 14px;
      display: flex;
      font-weight: 500;
      background-color: #37bb55;
    color: #fff;
}
.cart .cricle{
      display: flex;
    justify-content: center;
    align-items: center;
    border: 1px solid #fff;
    border-radius: 100px;
    width: 20px;
    height: 20px;
    font-size: 11px;
    margin-right: 4px;
}
.head a{
  color: #3c3c3c;
    font-size: 14px;
    font-weight: 500;
    padding: 12px 12px;
        cursor: pointer;
}

#myCarousel .img{
      background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
    width: 100%;
    height: 378px;
    display: block;
}

.body_view{
  position: relative;
}

.body_view #myCarousel{
  
}
.body_view .container{
    position: absolute;
    top: 0;
    left: 50%;
    transform: translate(-50%);
}
.tabTitle{
      font-size: 44px;
    color: #fff;
    line-height: 41px;
    font-weight: 600;
  }

.tabTitle.a1{    padding-left: 90px; }
.tabTitle.a2{    padding-left: 176px; }
.tabTitle.a3{     padding-left: 221px;}
.table{
  display:table;
}
.table .roww{
  display:table-row;
}
.table .cell{
  display:table-cell;
}
.fa.fa-star{
    color: #fbb040;
    font-size: 36px;
    margin-right: 10px;

}
.tt1{
      font-size: 29px;
    font-weight: 600;
}
.tt2{
  color: gray;
    font-size: 12px;
        line-height: 4px;
}
.tt3{
      color: #c7a075;
    font-size: 30px;
}
.tt4{
    width: 46%;
    text-align: right;
    float: right;
    padding-right: 16px;
    font-size: 16px;
    line-height: 18px;
}
.tt5{
  color: #25383f;
    font-size: 35px;
    font-weight: 700;
    line-height: 35px;
}
.clickBut{
      border: 4px solid;
    text-align: center;
    width: 67%;
    padding: 7px;
    font-size: 20px;
    font-weight: bold;
    margin: 19px 0;
    cursor: pointer;
}
.clickBut:active{
      background-color: #d8d8d8;
}
.calc_body{
  background-color: #e9e5e4;
    padding: 16px;
}
.calc_body .calc{
    background: #efefef;
    border: 2px dashed #babbbc;
    padding: 22px;
}

.calc_body hr{
      text-align: center;
    width: 70%;
    margin: 22px auto;
}
.calc_body label{
      margin-bottom: 3px;
    font-size: 14px;
}
.calc_body input, .calc_body select{
      outline: none;
    font-size: 14px;
    padding: 3px 8px;
    color: gray;
}
.calc_body .st1{
      text-align: center;
    font-weight: 600;
    font-size: 32px;
    line-height: 30px;
}
.calc_body .st2{
      margin-top: 12px;
}
.calc_body .st3{
      text-align: center;
    font-size: 15px;
    color: #d26441;
    margin-bottom: 7px;
}
.calc_body .st4{
  text-align: center;
    font-size: 47px;
    color: #d26441;
    /* margin-bottom: 7px; */
    font-weight: 600;
    line-height: 41px;
}

.clickLang .nav-link.dropdown-toggle{
      border: 1px solid #fff;
    padding: 2px 5px;
    position: relative;
    top: 5px;
    margin-left: 32px;
}

.calc_body .st5{
      text-align: center;
    font-size: 16px;
}

.iamgeLeft{
      width: 107px;
    position: relative;
    top: -80px;
    left: 27%;
}
@media (max-width: 576px){
  .head .nav {
          flex-direction: column;
  }
  .navbar{
    margin-top: 0px;
  }

  .tabTitle{
      font-size: 36px;
    color: #635d5d;
    text-align: center;
  }
  .clickBut{
    margin: 19px auto;
  }
  .tt4{
      float: inherit;
    width: 100%;
    text-align: center;
    margin: 19px 0;
  }
  .clickLang .nav-link.dropdown-toggle{
      top: -2px;
    margin-left: 0;
    width: 11%;
  }

  .tabTitle.a1, .tabTitle.a2, .tabTitle.a3{
    padding-left: 0px;
  }
  .iamgeLeft{
      top: 0px;
      left: 27%;
  }
}
</style>
