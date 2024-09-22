<template>
  <div class="container-fluid" style="width: 95%">
    <div class="row">
      <div class="col-2">
        <nuxt-link to="../../">
          <i class="bi bi-arrow-left-short"></i>
        </nuxt-link>
      </div>
      <div class="col-10">
        <h2 class="text-center title">RIWAYAT KUNJUNGAN</h2>
      </div>
      <div class="col-12">
        <div class="my-3">
          <form @submit.prevent="filter">
            <input
              v-model="keyword"
              type="search"
              class="form-control form-control-lg rounded-5"
              placeholder="filter...."
            />
          </form>
        </div>
        <div class="my-3 text-muted">
          Menampilkan {{ visitors.length }} dari {{ visitor }}
        </div>
      </div>
    </div>
    <table class="table table-bordered">
      <thead>
        <tr>
          <th>No</th>
          <th>Nama</th>
          <th>Keanggotaan</th>
          <th>Waktu</th>
          <th>Keperluan</th>
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

.title {
  font-family: inter;
  margin-top: 20px;
}

.table {
  margin-top: 20px;
  font-size: 1rem;
}

@media only screen and (max-width: 820px) {
  table {
    font-size: 0.8rem;
  }

  .title {
    font-size: 1.2rem;
  }

  i {
    font-size: 35px;
  }
}
</style>

<script setup>
useHead({ title: "daftar pengunjung" })
const supabase = useSupabaseClient()
const visitors = ref([])
const visitor = ref(0)
const keyword = ref("")

const getPengunjung = async () => {
  const { data } = await supabase.from('pengunjung')
    .select(`*, keanggotaan(*), keperluan(*)`)
    .order("id", { ascending: false });
  if (data) visitors.value = data
}

const hitungData = async () => {
  const { count } = await supabase.from("pengunjung").select("*", { count: 'exact' })
  visitor.value = count
}

const filter = async () => {
  const { data } = await supabase.from('pengunjung')
    .select(`*, keanggotaan(*), keperluan(*)`)
    .ilike('nama', `%${keyword.value}%`)
  if (data) visitors.value = data
}

onMounted(() => {
  hitungData()
  getPengunjung()
})
</script>
