<template>
  <div class="container-fluid" style="width: 95%">
    <div class="row">
      <div class="col-2">
        <nuxt-link to="../">
          <i class="bi bi-arrow-left-short"></i>
        </nuxt-link>
      </div>
      <div class="col-8">
        <h2 class="text-center title">
          ISI FORM PENGUNJUNG
        </h2>
      </div>
      <div class="col-lg-12">
        <form @submit.prevent="kirimData">
          <div class="mb-3">
            <input 
              v-model="form.nama" 
              type="text" 
              class="form-control form-control-lg rounded-5" 
              placeholder="NAMA........" 
            />
          </div>
          <div class="mb-3">
            <select v-model="form.keanggotaan" class="form-control form-control-lg form-select rounded-5">
              <option value="">KATEGORI</option>
              <option v-for="(member, i) in members" :key="i" :value="member.id">{{ member.nama }}</option>
            </select>
          </div>
          <div class="mb-3" v-if="form.keanggotaan == 2">
            <div class="row">
              <div class="col-md-4">
                <select v-model="form.kelas" class="form-control form-control-lg form-select rounded-5 mb-2">
                  <option value="">KELAS</option>
                  <option value="X">X</option>
                  <option value="XI">XI</option>
                  <option value="XII">XII</option>
                </select>
              </div>
              <div class="col-md-4">
                <select v-model="form.jurusan" class="form-control form-control-lg form-select rounded-5 mb-2">
                  <option value="">JURUSAN</option>
                  <option value="PPLG">PPLG</option>
                  <option value="TJKT">TJKT</option>
                  <option value="TSM">TSM</option>
                  <option value="DKV">DKV</option>
                  <option value="TOI">TOI</option>
                </select>
              </div>
              <div class="col-md-4">
                <select v-model="form.no_kelas" class="form-control form-control-lg form-select rounded-5 mb-2">
                  <option value="">NO KELAS</option>
                  <option v-for="i in 4" :key="i" :value="i">{{ i }}</option>
                </select>
              </div>
            </div>
          </div>
          <div class="input-group mt-3">
            <select v-model="form.keperluan" class="form-control form-control-lg form-select rounded-5 mb-2">
              <option value="">Keperluan</option>
              <option v-for="(item, i) in objectives" :key="i" :value="item.id">{{ item.nama }}</option>
            </select>
          </div>
          <div class="input-group mt-4">
            <button type="submit" class="btn btn-outline-primary rounded-4" style="color: black; font-family: lnria-serif">
              KIRIM
            </button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script setup>
useHead({ title: "form pengunjung" })
const supabase = useSupabaseClient()
const members = ref([])
const objectives = ref([])

const form = ref({
  nama: "", 
  keanggotaan: "",
  no_kelas: "",
  jurusan: "",
  kelas: "",
  keperluan: "",
})

const kirimData = async () => {
  const { error } = await supabase.from('pengunjung').insert([form.value])
  if (!error) navigateTo('/pengunjung')
}

const getKeanggotaan = async () => {
  const { data } = await supabase.from('keanggotaan').select('*')
  if (data) members.value = data
}

const getKeperluan = async () => {
  const { data } = await supabase.from('keperluan').select('*')
  if (data) objectives.value = data
}

onMounted(() => {
  getKeanggotaan()
  getKeperluan()
})
</script>

<style scoped>
i {
  font-size: 60px; 
  color: #000000;
}

.title {
  font-family: inter;
  margin-top: 20px;
}

@media only screen and (max-width: 820px) {
  h2 {
    font-size: 15px;
  }

  i {
    font-size: 35px;
  }
}
</style>
