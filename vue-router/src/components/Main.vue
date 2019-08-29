<template>
<div class="row" style="    margin-top: 84px;">
      <div class="col-sm-8">

      <div class="row">
        <div class="col-sm-12">
          <div class="tabTitle a1">{{ leftRowName[0] }}</div>
          <div class="tabTitle a2">{{ leftRowName[1] }}</div>
          <div class="tabTitle a3" style="padding-bottom: 12px;">{{ leftRowName[2] }}</div>
        </div>
      </div>

      <div class="row">
        <div class="col-sm-4">
          <img v-bind:src=" image "  class="iamgeLeft" />
        </div>
        <div class="col-sm-6">
          <div class="table" v-for="lr in leftRowItems">
                <div class="roww">
                  <div class="cell">
                    <i class="fa fa-star" aria-hidden="true" ></i>
                  </div>
                  <div class="cell">
                    <div class="tt1">{{ lr.name1 }}</div>
                    <div class="tt2">{{ lr.name2 }}</div>
                    <div class="tt3">{{ lr.name3 }}</div>
                  </div>
                </div>
              </div>
        </div>
        <div class="col-sm-2"></div>
      </div>
      <div class="row">
        <div class="col-sm-4">
          <div class="tt4">{{ leftRowName[3] }}</div>
        </div>
        <div class="col-sm-6">
          <div class="tt5" v-html="leftRowName[4]"> </div>
              <div class="clickBut">{{ leftRowName[5] }}</div>
        </div>
        <div class="col-sm-2"></div>
      </div>

       
      </div>
      <div class="col-sm-4">
        
        <div class="calc_body">
          <div class="calc">
            <div class="st1" v-html="calcName[0]"></div>
            <div class="st2" v-html="calcName[1]"></div>

            <hr />

            <div class="form-group">
              <label for="exampleFormControlSelect1">{{ calcName[2] }}</label>
              <select class="form-control" id="exampleFormControlSelect1" v-model="selected" @change="calcSumma">
                <option seleted hidden disabled> - </option>
                <option v-for="cc in chooseCultures" v-bind:value="cc.price">{{ cc.value }}</option>
                
              </select>
            </div>

            <div class="form-group">
              <label for="exampleInputEmail1">{{ calcName[3] }}</label>
              <input type="text" class="form-control" id="exampleInputEmail1" aria-describedby="" v-model="value1" v-on:keyup="calcSumma" />
            </div>
            <div class="form-group">
              <label for="exampleInputEmail2"> {{ calcName[4] }} </label>
              <input type="text" class="form-control" id="exampleInputEmail2" aria-describedby="" v-model="value2" v-on:keyup="calcSumma"/>
            </div>
            <div class="form-group">
              <label for="exampleInputEmail3">{{ calcName[5] }}</label>
              <input type="text" class="form-control" id="exampleInputEmail3" aria-describedby="" v-model="value3" v-on:keyup="calcSumma" />
            </div>

            <hr />

            <ul class="error">
              <li v-for="error in errors">{{ error }}</li>
            </ul>

            <div class="st3">{{ calcName[6] }}</div>
            <div class="st4">{{ summa }}</div>
            <div class="st5">{{ calcName[7] }}</div>
          </div>
        </div>
      </div>
    </div>
</template>

<script>
export default {
  name: 'Main',
  data () {
    return {
      leftRowName:[
        'ОРГАНИЧЕСКОЕ',
        'НАНО-УДОБНИЕ',
        'ДОБРИВО',
        'Хотитите трали-вали ла-лала?',
        'УЗНАЙТЕ <br/> О НАГРО БОЛЬШЕ! ',
        'УЗНАТЬ БОЛЬШЕ'
      ],
      leftRowItems:[
        {name1:'ПРИРОСТ УРОЖАЯ', name2:'в сравнении с химическим удобрением', name3:'30%-250%'},
        {name1:'ЭКОНОМИЯ', name2:'химических удобрений в хозяйстве', name3:'до 70%'},
        {name1:'РОСТ КОРНЕВОЙ ', name2:'системы растений при использовании', name3:'в 3-10раз'},
      ],
      calcName : [
        'ПОСЧИТАЙТЕ<br/> ПРИБЫЛЬ', 
        '<b>ДОБРИВО</b> ЭФФЕКТИВНЕЕ ХИМИИ',
        'Выберите культуру',
        'Урожайность, ц/га',
        'Стоимость хим. удобрення, грн/га',
        'Посевная плошадь, га',
        'ПРИБЫЛЬ ОТ ДОБРИВА',
        'грн'
      ],
      selected:3500,
      chooseCultures:[
        {value:'Пшеница = 3500грн / т', price:3500},
        {value:'Овес = 4500грн / т', price: 4500},
        {value:'Кукурузда = 5600грн / т', price: 5600}
      ],
      value1:20,
      value2:300,
      value3:10,
      summa:50000,
      errors:[],
      image: require('@/assets/74364.jpeg')
    }
  },
  methods:{
    calcSumma:function(){

      var val1 = parseInt(this.value1), 
          val2 = parseInt(this.value2),
          val3 = parseInt(this.value3),
          select = parseInt(this.selected);

      console.log(val1, val2, val3, select)

      this.errors = [];

      if (isNaN(val1)) {
        this.errors.push(' Требуется указать "Урожайность, ц/га" ');
        return false;
      }
      if (isNaN(val2)) {
        this.errors.push(' Требуется указать "Стоимость хим. удобрення, грн/га" ');
        return false;
      }
      if (isNaN(val3)) {
        this.errors.push(' Требуется указать "Посевная плошадь, га" ');
        return false;
      }



      this.summa = ((val1 / 10)* select * val3) + (val2 * val3);

    }
  },
  mounted (){
    this.calcSumma()
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.error{
    color: red;
    list-style-type: none;
    font-size: 12px;
    padding: 0;
    margin: 0;
}
.error li{
      text-align: center;
    padding: 5px 0;
}
</style>