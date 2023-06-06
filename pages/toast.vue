<template>
  <div
    class="flex flex-col items-center justify-center h-screen space-y-4 relative"
  >
    <h1 class="text-4xl absolute top-0">Toast Page</h1>
    <div class="border-b pb-2 flex items-center w-3/4 space-x-2">
      <p>Basic：</p>
      <div
        class="border p-2 cursor-pointer hover:bg-primary hover:text-white"
        @click="getToastBasic"
      >
        自訂按下開啟
      </div>
      <div
        class="border p-2 cursor-pointer hover:bg-primary hover:text-white"
        @click="getToastBasic"
      >
        自訂按下關閉
      </div>
    </div>
    <div class="border-b pb-2 w-3/4 flex items-center space-x-2">
      <p>Static：</p>

    </div>
    <!-- Modal Basic -->
    <Toast ref="test" />
    <!-- Modal Static -->

    <div
      class="absolute top-4 left-10 cursor-pointer hover:text-red"
      @click.prevent="$router.back()"
    >
      返回
    </div>
  </div>
</template>

<script>
export default {
  name: 'ToastPage',
  data() {
    return {}
  },
  methods: {
    // 自訂開關method, 細節看 Methods
    // https://tailwind-elements.com/docs/standard/components/toast/#docsTabsAPI
    getToastBasic() {
      const observer = this.$refs.test.$el
      const toast = new this.$toast(observer)
      toast.show()
      setTimeout(() => {
        toast.hide()
      }, 1000)
    },
    getModalStatic() {
      const observer = this.$refs.static.$el
      const modal = new this.$modal(observer)
      modal.show()
      setTimeout(() => {
        modal.hide()
      }, 2000)
    },
  },
}
</script>
