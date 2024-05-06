<template>
  <div class="container-fluid" style="width: 95%">
    <div class="row">
      <div class="col-2">
        <nuxt-link to="../../">
          <i class="bi bi-arrow-left-short"></i>
        </nuxt-link>
      </div>
      <div class="col-10">
        <h2 style="
            text-align: center;
            font-family: inter;
            margin-top: 20px;
          ">
          RIWAYAT KUNJUNGAN
        </h2>
      </div>
      <div class="col-lg-12">
        <div class="my-3">
          <form @submit.prevent="filter">
          <input v-model="keyword" type="search" class="form-control form-control-lg rounded-5" placeholder="filter...." />
          </form>
        </div>
        <div class="my-3 text-muted">menampilkan {{ visitors.length }} dari {{ visitor }}</div>
      </div>
    </div>
    <table class="table table-bordered">
      <thead>
        <tr>
          <td>No</td>
          <td>Nama</td>
          <td>Keanggotaan</td>
          <td>Waktu</td>
          <td>Keperluan</td>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(visitor, i) in visitors" :key="i">
          <td>{{ i + 1 }}</td>
          <td>{{ visitor.nama }}</td>
          <td>{{ visitor.keanggotaan.nama }}</td>
          <td>{{ visitor.tanggal }}/{{ visitor.waktu }}</td>
          <td>{{ visitor.keperluan.nama }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<style scoped>
i {
  font-size: 60px;
  color: #000000;
}

@media only screen and (max-width: 820px) {
  table {
    font-size: 5px;
  }

  h2 {
    font-size: 15px;
  }

  i {
    font-size: 35px;
    color: #000000;
  }
}
</style>
<script setup>
useHead({ title: "daftar pengunjung" })
const supabase = useSupabaseClient()
const visitors = ref([])
const visitor = ref(0)
const keyword =ref("")
const getPengunjung = async () => {
  const { data, error } = await supabase.from('pengunjung')
    .select(`*, keanggotaan(*), keperluan(*)`)
    .order("id", { ascending: false });
  if (data) visitors.value = data
}

const hitungData = async() => {
  const { data, count } = await supabase.from("pengunjung").select("*", { count : 'exact'})
  if (data) visitor.value = count

}
const filter = async () => {
  const { data, error } = await supabase.from('pengunjung')
    .select(`*, keanggotaan(*), keperluan(*)`)
    .ilike('nama',`%${keyword.value}%`)
  if (data) visitors.value = data
}

onMounted(() => {
  hitungData()
  getPengunjung()

})
</script>