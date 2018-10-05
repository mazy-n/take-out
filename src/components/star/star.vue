<template>
   <div class="star" :class="starType">
       <span v-for="itemClass in itemClasses" :key="itemClass.id" :class="itemClass" class="star-item"></span>
   </div>
</template>

<script type="text/ecmascript-6">
const LEN = 5; // 星星个数
const STAR_ON = 'on';
const STAR_HALF = 'half';
const STAR_OFF = 'off';

export default {
  name: 'star',
  props: {
    size: {
      type: Number
    },
    score: {
      type: Number
    }
  },
  data () {
    return {};
  },
  computed: {
    starType () {
      return 'star-' + this.size;
    },
    itemClasses () {
      let result = [];
      let score = Math.floor(this.score * 2) / 2;
      let hasHalf = score % 1 !== 0;
      score = Math.floor(score);
      for (let index = 0; index < score; index++) {
        result.push(STAR_ON);
      }
      if (hasHalf) {
        result.push(STAR_HALF);
      }
      while (result.length < LEN) {
        result.push(STAR_OFF);
      }
      return result;
    }
  }
};
</script>

<style>
.star{
    font-size: 0;
}
.star-item{
    display: inline-block;
    background-repeat: no-repeat;
}
.star-item:last-child{
    margin-right: 0;
}
.star-48>.star-item{
    width: 20px;
    height: 20px;
    margin-right: 22px;
    background-size: 20px 20px;
}
.star-48>.on{
    background-image: url('./img/star48_on@2x.png');
}
.star-48>.half{
    background-image: url('./img/star48_half@2x.png');
}
.star-48>.off{
    background-image: url('./img/star48_off@2x.png');
}
.star-36>.star-item{
    width: 15px;
    height: 15px;
    margin-right: 6px;
    background-size: 15px 15px;
}
.star-36>.on{
    background-image: url('./img/star36_on@2x.png');
}
.star-36>.half{
    background-image: url('./img/star36_half@2x.png');
}
.star-36>.off{
    background-image: url('./img/star36_off@2x.png');
}
.star-24>.star-item{
    width: 10px;
    height: 10px;
    margin-right: 3px;
    background-size: 10px 10px;
}
.star-24>.on{
    background-image: url('./img/star24_on@2x.png');
}
.star-24>.half{
    background-image: url('./img/star24_half@2x.png');
}
.star-24>.off{
    background-image: url('./img/star24_off@2x.png');
}
</style>
