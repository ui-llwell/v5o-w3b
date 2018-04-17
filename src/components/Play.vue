<template>
  <div class="play">
    <div class="top">
      <div class="video">
        <img src="../assets/img/P1.png" alt="">
      </div>
    </div>
    <div class="bottom">
      <div class="describe">
          <div class="title">{{word}}</div>
          <div class="content">
            Nutricia Aptamil 金装爱他美澳洲畅销奶粉品牌，来自新西兰纯净奶源，原料天然，无蔗糖，无香精，口感清淡，宝贝喜爱。特添加益生元组合，有助于改善肠道环境，为宝宝的健康成长提供科学的支持。
          </div>
          <div class="time">
            {{id}}
          </div>
        </div>
      <div class="list-item">
        <ul class="clearfix">
          <li v-for="(item,index) in playItemList" v-bind:key="index">
            <div class="img">
              <a href="">
                <img class="lazy" src="../assets/img/L2.png" />
              </a>
            </div>
            <div class="txt">
              <h3>{{item.name}}</h3>
              <div class="price">
                <span>{{item.time}}</span>
              </div>
            </div>

          </li>

        </ul>
      </div>
    </div>
    <!-- <router-link to="/play">
      <div class="toPlay">
        {{$route.params.id}}
      </div>
    </router-link> -->
  </div>

</template>

<script>
  import axios from 'axios'
  export default {
    name: 'HelloWorld',
    data() {
      return {
        id: "",
        word: "ppppp",
        playItemList:[]
      }
    },
    created() {
      this.id = this.$route.query.id;
    },
    mounted: function() {
      axios.get("http://localhost:8080/static/test.json", {
        params: {
          id: this.id,
        }
      }).then(response => {
        console.log(response.data.play)

        // this.itemList = response.data.item;
        this.word = response.data.play.playcon;
        // this.playItemList = response.data.playItem;
        // console.log(this.playItemList)
        response.data.playItem.forEach((item)=>{
          this.playItemList.push(item);
        })
      });
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="less">
  .play {
    .top {
      width: 375px;
      position: relative;
      text-align: center;
      .video {
        width: 100%;
        img {
          width: 100%;
          max-height: 180px;
        }
      }

    }
    .bottom{
      background: #313131;
          padding-bottom: 25px;
      .describe {
        padding: 15px;
        .title {
          font-size: 16px;
          font-weight: 600;
          color: #fff;
          text-align: left;
        }
        .content {
          font-size: 10px;
          color: #e1e1e1;
          text-align: left;
        }
        .time {
          font-size: 12px;
          color: #7d7d7d;
          text-align: left;
        }
      }
      .list-item {
        // padding: 25px 0;
        margin:0 25px;
        background:#1b1b1b;
        li {
          background:#181818;
          overflow: hidden;
          position: relative;
          float: left;
          // width: calc(100% / 2);
          width:~"calc(50% - 1px)";
          margin-top:2px;
          height:240px;
          .img {
            height: 150px;
            margin-top:30px;
            img {
              width: 100%;
              height: 100%
            }
          }
          .txt {
            padding: 5px;
            h3 {
              font-size: 10px;
              // -webkit-line-clamp: 2;
              // -webkit-box-orient: vertical;
              // overflow: hidden;
            text-overflow:ellipsis;
            white-space: nowrap;
            overflow: hidden;
              text-align: center;
              color: #fff;
            }
            .price {

              font-size: 10px;
              text-align: center;
              color: #fff;
              margin: 5px 0;
            }
          }
        }
        li:nth-child(2n) {
          float: right;
          // border-left: 1px solid #b5b5b5;
        }
      }
    }
  }
  
  
</style>