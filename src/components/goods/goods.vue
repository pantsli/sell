<template>
  <div class="goods">
    <div class="menu-wrapper">
      <ul>
        <li v-for="item in goods">
          <span class="text">
            <span v-show="item.type>0" class="icon">{{item.name}}</span>
          </span>
        </li>
      </ul>
    </div>
    <div class="foods-wrapper">foods-wrapper</div>
  </div>
</template>

<script type="text/ecmascript-6">
  const ERR_OK = '0';

  export default {
    props: {
      seller: {
        type: Object
      }
    },
    data() {
      return {
        goods: []
      };
    },
    created() {
      this.classMap = ['decrease', 'discount', 'special', 'invoice', 'guarantee'];
      this.$http('/api/goods').then((response) => {
        response = response.body;
        if (response.errno === ERR_OK) {
          this.goods = response.data;
          console.log(this.goods);
        }
      });
    }
  };
</script>

<style lang="stylus" rel="stylesheet/stylus">
  @import "goods"
</style>
