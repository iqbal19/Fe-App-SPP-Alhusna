<template>
  <div>
    <div class="mb-[15px] flex flex-col lg:flex-row justify-between  gap-2">
      <div class="flex flex-row gap-2">
        <button class="btn-primary text-sm" @click="$emit('clickButton')"><i class="fas fa-plus mr-2"></i>Tambah Siswa</button>
        <button class="btn-primary text-sm" @click="$emit('clickFile')"><i class="fas fa-plus mr-2"></i>Dengan File</button>
      </div>
      <div class="flex flex-col lg:flex-row gap-2">
        <select v-model="valueContent.id_periode" class="base-input w-full lg:w-1/6" @change="$emit('changeSelect', 'periode')">
          <!-- <option value="">Semua</option> -->
          <option v-for="(dt, index) in periode" :key="index" :value="dt.id">{{dt.tahunAjaran}}</option>
        </select>
        <select v-model="valueContent.idKelas" class="base-input w-48" @change="$emit('changeSelect', 'kelas')">
          <option value="">Semua Kelas</option>
          <option value="belum">Belum ada kelas</option>
          <option v-for="(kls, index) in itemKelas" :key="index" :value="kls.idKelas"> {{kls.namaKelas}} </option>
        </select>
        <select v-model="valueContent.status" class="base-input w-32" @change="$emit('changeSelect', 'status')">
          <option value="">Semua</option>
          <option value="aktif">Aktif</option>
          <option value="tidak-aktif">Lulus</option>
        </select>
        <!-- <input type="text" placeholder="Cari admin ..." class="w-full lg:w-80 base-input"> -->
        <div class="flex text-black">
          <span class="bg-white border rounded-l inset-y-0 left-0 flex items-center p-2.5 border-black-light">
              <i class="fas fa-search"></i>
          </span>
          <input v-model="valueContent.search" type="text" class="-ml-0.5 w-full lg:w-72 base-input placeholder-black" placeholder="Cari nama..." autocomplete="off" @input="$emit('eventChange', $event)" />
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  props: {
    value: { type: Object, default: () => {} },
    itemKelas: { type: Array, default: () => [] },
    periode: { type: Array, default: () => [] }
  },
  computed: {
    valueContent: {
			get(): any {
				return (this as any).value
			},
			set(value): void {
				;(this as any).$emit('input', value)
			}
		}
  }
})
</script>