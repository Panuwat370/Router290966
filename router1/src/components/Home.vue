<!-- Home.vue -->
<template>
  <div class="container text-center">
    <div class="row">
      <div class="col mt-5" v-for="(restaurant, index) in travelList" :key="index">
        <div class="card" style="width: 18rem">
          <img :src="restaurant.imagesP" class="card-img-top" :width="sizeW" :height="sizeH" />
          <div class="card-body">
            <h2>สินค้าชิ้นที่ {{ index + 1 }}</h2>
            <h5 class="card-title">{{ restaurant.name }}</h5>
            <p class="card-text">ราคา {{ restaurant.price }}</p>
            <button
              class="btn btn-danger"
              data-bs-toggle="modal"
              data-bs-target="#staticBackdrop"
              @click="goToOtherComponent(restaurant.name, restaurant.imagesP, index)"
            >
              ซื้อ
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue' // import ref

export default {
  methods: {
    goToOtherComponent(name, imagesP, index) {
      // ส่งค่าไปยังคอมโพเนนต์ OtherComponent.vue ผ่านคิวรี่พารามิเตอร์
      this.$router.push({
        name: 'other',
        query: {
          index: index,
          restaurantName: name,
          restaurantImagesP: imagesP
        }
      })
    }
  },
  setup() {
    const travelList = ref([
      {
        name: 'หนังสือขายดียอดฮิต',
        price: 259,
        imagesP:
          'https://th.bing.com/th/id/R.db40a3f0e1794ac34347cd26f5e2bcce?rik=BMgH2FC0jswixA&riu=http%3a%2f%2fwww.namobook.com%2fmedia%2fcatalog%2fproduct%2fcache%2f1%2fimage%2f800x800%2f9df78eab33525d08d6e5fb8d27136e95%2fa%2fh%2fah003.jpg&ehk=NPajBf5mEdpf512s15jtEvyN0PXsDf5qEtImKVjoXPo%3d&risl=&pid=ImgRaw&r=0'
      },
      {
        name: 'หนังสือขายดียอดฮิต',
        price: 259,
        imagesP: 'https://cf.shopee.co.th/file/cc1e1c266bfcd71785f6526caec1b254'
      },
      {
        name: 'หนังสือขายดียอดฮิต',
        price: 259,
        imagesP:
          'https://th.bing.com/th/id/R.d9af9e5f5eb2b3cb70f3738be5c5fe85?rik=V28KJjByK8rhKA&riu=http%3a%2f%2fwww.thaibookworld.com%2fimage%2fcache%2fbook2%2f9786165110136L-500x500.gif&ehk=zNZAdwswrPG6smn5MHe0YTf%2b5T02M3bKvxiG6HcZ7x4%3d&risl=&pid=ImgRaw&r=0'
      }
    ])

    const sizeW = 350
    const sizeH = 250

    return {
      // return ตัวแปรออกมาจาก setup
      travelList,
      sizeW,
      sizeH
    }
  }
}
</script>
