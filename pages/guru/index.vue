<template>
  <div>
    <page-default />
  </div>
</template>

<script>
export default {
  name: 'IndexGuruUserPage',
  components: {
    PageDefault: () => import('@/components/features/guru/pages/PageListGuru.vue')
  },
  middleware: ['auth', 'cek-admin'],
  data() {
    return {}
  }
}
</script>