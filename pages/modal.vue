<template>
  <div class="flex flex-col items-center justify-center h-screen space-y-4 relative">
    <div class="border-b pb-2 flex items-center w-3/4 space-x-2">
      <p>Basic：</p>
      <button
        type="button"
        class="border p-2 cursor-pointer hover:bg-primary hover:text-white"
        data-te-toggle="modal"
        data-te-target="#ttt"
        data-te-ripple-init
        data-te-ripple-color="light"
      >
        ModalBtn
      </button>
      <div
        class="border p-2 cursor-pointer hover:bg-primary hover:text-white"
        @click="getModalBasic"
      >
        自訂按下開啟, 兩秒後自動關閉
      </div>
    </div>
    <div class="border-b pb-2 w-3/4 flex items-center space-x-2">
      <p>Static：</p>
      <button
        type="button"
        class="border p-2 cursor-pointer hover:bg-primary hover:text-white"
        data-te-toggle="modal"
        data-te-target="#staticBackdrop"
        data-te-ripple-init
        data-te-ripple-color="light"
      >
        ModalStaticBtn
      </button>
      <div
        class="border p-2 cursor-pointer hover:bg-primary hover:text-white"
        @click="getModalStatic"
      >
        自訂按下開啟, 兩秒後自動關閉
      </div>
    </div>
    <!-- Modal Basic -->
    <Modal ref="base" />
    <Modal name="ttt" />
    <!-- Modal Static -->
    <ModalStatic name="staticBackdrop" />
    <ModalStatic ref="static" />
    <div class="absolute top-4 left-10 cursor-pointer hover:text-red" @click.prevent="$router.back()">返回</div>
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
