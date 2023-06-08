<template>
  <div class="relative flex flex-col items-center justify-center h-screen space-y-4">
    <h1 class="absolute top-0 text-4xl">Modal Page</h1>
    <div class="flex items-center w-3/4 pb-2 space-x-2 border-b">
      <p>Basic：</p>
      <button
        type="button"
        class="p-2 border cursor-pointer hover:bg-primary hover:text-white"
        data-te-toggle="modal"
        data-te-target="#ttt"
        data-te-ripple-init
        data-te-ripple-color="light"
      >
        ModalBtn
      </button>
      <div
        class="p-2 border cursor-pointer hover:bg-primary hover:text-white"
        @click="getModalBasic"
      >
        自訂按下開啟, 兩秒後自動關閉
      </div>
    </div>
    <div class="flex items-center w-3/4 pb-2 space-x-2 border-b">
      <p>Static：</p>
      <button
        type="button"
        class="p-2 border cursor-pointer hover:bg-primary hover:text-white"
        data-te-toggle="modal"
        data-te-target="#staticBackdrop"
        data-te-ripple-init
        data-te-ripple-color="light"
      >
        ModalStaticBtn
      </button>
      <div
        class="p-2 border cursor-pointer hover:bg-primary hover:text-white"
        @click="getModalStatic"
      >
        自訂按下開啟, 兩秒後自動關閉
      </div>
    </div>
    <!-- Modal Basic -->
    <client-only>
      <Modal ref="base" />
      <Modal name="ttt" />
      <!-- Modal Static -->
      <ModalStatic name="staticBackdrop" />
      <ModalStatic ref="static" />
    </client-only>
    <div class="absolute cursor-pointer top-4 left-10 hover:text-red" @click.prevent="$router.back()">返回</div>
  </div>
</template>

<script>
export default {
  name: 'ModalPage',
  data() {
    return {}
  },
  methods: {
    // 自訂開關method, 細節看 Methods
    // https://tailwind-elements.com/docs/standard/components/modal/#docsTabsAPI
    getModalBasic() {
      const observer = this.$refs.base.$el
      const modal = new this.$modal(observer)
      modal.show()
      setTimeout(() => {
        modal.hide()
      }, 2000)
    },
    getModalStatic() {
      const observer = this.$refs.static.$el
      const modal = new this.$modal(observer)
      modal.show()
      setTimeout(() => {
        modal.hide()
      }, 2000)
    }
  },
}
</script>
