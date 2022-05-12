<template>
  <div class="space"></div>
  <ul>
    <li v-for="(item,index) in list_fruit">
      <div class="container">
        <div class="icon content">
          <input type="checkbox" @click="checked_or_unchecked(index)">
          <img :src="item.url" alt="">
        </div>
        <div class="desc content">
          <p id="name">{{ item.name }}</p>
          <p id="price">￥{{ item.price }}</p>
        </div>
        <div class="counter content">
          <span class="iconfont icon-jian" @click="count_reduce(index)"></span>
          <span class="count">{{ item.count }}</span>
          <span class="iconfont icon-jia" @click="count_plus(index)"></span>
        </div>
      </div>
      <div class="line"></div>
    </li>
  </ul>
  <div class="space"></div>
  <div class="container2">
    <span class="cont2">
      已选<span class="count">{{ count_total }}</span>件
    </span>
    <span class="cont2">
      合计￥<span class="count">{{ price_total }}</span>
    </span>
    <a href="#">
      <button>结算</button>
    </a>
  </div>
</template>

<script>
export default {
  name: "FruitShop",
  components: {},
  data() {
    return {
      count_total: 0,
      price_total: 0,
      list_fruit: [
        {
          "url": "src/assets/img/橙子.png",
          "name": "橙子",
          "price": "5",
          "count": "10",
          status: 0
        },
        {
          "url": "src/assets/img/牛油果.png",
          "name": "牛油果",
          "price": "20",
          "count": "2",
          status: 0
        },
        {
          "url": "src/assets/img/桃子.png",
          "name": "桃子",
          "price": "648",
          "count": "5",
          status: 0
        },
        {
          "url": "src/assets/img/葡萄.png",
          "name": "葡萄",
          "price": "17",
          "count": "1",
          status: 0
        },
        {
          "url": "src/assets/img/香蕉.png",
          "name": "香蕉",
          "price": "12",
          "count": "2",
          status: 0
        },
        {
          "url": "src/assets/img/香蕉.png",
          "name": "香蕉",
          "price": "12",
          "count": "2",
          status: 0
        },
        {
          "url": "src/assets/img/香蕉.png",
          "name": "香蕉",
          "price": "12",
          "count": "2",
          status: 0
        },
        {
          "url": "src/assets/img/香蕉.png",
          "name": "香蕉",
          "price": "12",
          "count": "2",
          status: 0
        },
        {
          "url": "src/assets/img/香蕉.png",
          "name": "香蕉",
          "price": "12",
          "count": "2",
          status: 0
        },
        {
          "url": "src/assets/img/香蕉.png",
          "name": "香蕉",
          "price": "12",
          "count": "2",
          status: 0
        },
        {
          "url": "src/assets/img/香蕉.png",
          "name": "香蕉",
          "price": "12",
          "count": "2",
          status: 0
        },
        {
          "url": "src/assets/img/香蕉.png",
          "name": "香蕉",
          "price": "12",
          "count": "2",
          status: 0
        }
      ]
    }
  },
  methods: {
    count_reduce(index) {
      if (this.list_fruit[index].count>1){
        --this.list_fruit[index].count;
        if (this.list_fruit[index].status === 1){
          --this.count_total;
          this.price_total -= parseInt(this.list_fruit[index].price)
        }
      }else {
        alert("最少选择一个商品！")
      }
    },
    count_plus(index) {
      ++this.list_fruit[index].count;
      if (this.list_fruit[index].status === 1){
        ++this.count_total;
        this.price_total += parseInt(this.list_fruit[index].price)
      }
    },
    checked_or_unchecked(index) {
      if (this.list_fruit[index].status === 0){
        ++ this.list_fruit[index].status
        // console.log(this.list_fruit[index].status);
        this.count_total += parseInt(this.list_fruit[index].count);
        this.price_total += parseInt(this.list_fruit[index].price) * parseInt(this.list_fruit[index].count);
      } else {
        -- this.list_fruit[index].status
        // console.log(this.list_fruit[index].status);
        this.count_total -= parseInt(this.list_fruit[index].count);
        this.price_total -= parseInt(this.list_fruit[index].price) * parseInt(this.list_fruit[index].count);
      }
    }
  }
}
</script>

<style lang="less" scoped>
.container {
  display: flex;
  flex-direction: row;
  height: 100px;

  .content {
    flex: 1;
  }

  .icon {
    display: inline-flex;

    img {
      width: 80px;
      height: 80px;
      display: inline-block;
      align-self: center;
      border-radius: 5px;
    }

    input {
      display: inline-block;
      align-self: center;
      margin: 0 20px 0 20px;
    }
  }

  .desc {
    font-weight: bold;
    text-align: center;
    line-height: 20px;
    margin: 20px 0 0 15px;

    #price {
      color: crimson;
      margin-top: 30px;
    }
  }

  .counter {
    align-self: flex-end;
    margin-bottom: 10px;

    .count {
      margin: 0 10px 0 10px;
    }
  }
}

.line {
  height: 1px;
  background-color: #f5f2f0;
  margin: 0 15px;
}

.container2 {
  background-color: #f5f5f5;
  width: 100%;
  height: 50px;
  position: fixed;
  bottom: 0;
  display: flex;
  flex-direction: row;

  .cont2 {
    flex: 1;
    align-self: center;
  }

  .count {
    color: #FC4F59;
    margin: 0 2px 0 2px;
    font-weight: bold;
  }

  button {
    width: 130px;
    height: 36px;
    background-color: #FC4F59;
    color: white;
    border: none;
    border-radius: 5px;
    margin: 7px 7px;
  }
}

.space {
  width: 100%;
  height: 50px;
}
</style>