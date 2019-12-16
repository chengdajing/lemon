<template>
  <div>
    <swiper
      :indicator-dots="indicatorDots"
      :autoplay="autoplay"
      :interval="interval"
      :duration="duration"
    >
      <block v-for="img in imgUrls" :key="img">
        <swiper-item>
          <image :src="img" style="width:100%" />
        </swiper-item>
      </block>
    </swiper>
    <i-grid i-class="no-border">
    <i-grid-item @click="goType(grid)" v-for="grid in grids" :key="grid" i-class="no-border">
        <i-grid-icon>
            <image :src="grid.image" />
        </i-grid-icon>
        <i-grid-label>{{grid.title}}</i-grid-label>
    </i-grid-item>
  </i-grid>
  <i-panel :title="title_name">
    <view style="padding: 15px;">
      <i-card v-for="item in top" :key="item" i-class="split" :extra="item.name" :thumb="item.image">
          <view slot="content">{{item.remark}}</view>
          <view slot="footer">{{item.address}}</view>
      </i-card>
    </view>
  </i-panel>
  </div>
</template>

<script>
export default {
  data () {
    return {
      title_name: "热门穿搭",
      grids: [
        {title:"裤子",image:"/static/images/1.png"},
        {title:"棉服",image:"/static/images/2.png"},
        {title:"裙子",image:"/static/images/3.png"},
        {title:"鞋",image:"/static/images/4.png"}
      ],
      top: [
        {name:"回力专卖店",address:"地址1",image:"https://img.alicdn.com/imgextra/i1/2200678870940/O1CN013hIJBu1IoYsPG4qiF_!!0-item_pic.jpg_430x430q90.jpg",remark:"介绍1"},
        {name:"森马专卖店",address:"地址2",image:"https://gd4.alicdn.com/imgextra/i1/674264529/O1CN01k3LXTd1jKKMGLflLu_!!674264529.jpg_50x50.jpg_.webp",remark:"介绍2"},
        {name:"花花公子专卖店",address:"地址3",image:"https://img.alicdn.com/imgextra/i2/133449778/O1CN01ZAmeYV2M6NDL2xW4N_!!0-saturn_solar.jpg_220x220.jpg_.webp",remark:"介绍3"},
        {name:"以纯专卖店",address:"地址4",image:"https://img.alicdn.com/imgextra/i1/53279892/O1CN01KlkukL2MwaSPUOA2G_!!0-saturn_solar.jpg_220x220.jpg_.webp",remark:"介绍4"}
      ],
      imgUrls: [
        'http://img4.imgtn.bdimg.com/it/u=1310451738,1415307076&fm=26&gp=0.jpg?w=640',
        'http://img3.imgtn.bdimg.com/it/u=1239448510,2631450035&fm=26&gp=0.jpg?w=640',
        'http://img5.imgtn.bdimg.com/it/u=2130833958,3658862499&fm=26&gp=0.jpg?w=640'
      ],
      indicatorDots: false,
      autoplay: false,
      interval: 5000,
      duration: 1000
    }
  },

  methods: {
    goType(type){
      console.log(type)
      let url = '../list/main?type=' + type.title
      mpvue.navigateTo({ url })
    }
  },

  created () {
  }
}
</script>

<style scoped>
div >>> .no-border {
  border-width: 0pt;
}
div >>> .split {
  margin-bottom: 10pt;
}
</style>
