<template>
  <div class="container-fluid">
    <div class="row my-5 justify-content-around">
      <div class="col-lg-5 mb-5">
        <nuxt-link to="/pengunjung/tambah" class="link-card">
          <div class="card bg-pengunjung rounded-5">
            <div class="card-body">
              <h2 class="card-title">PENGUNJUNG</h2>
            </div>
          </div>
        </nuxt-link>
      </div>
      <div class="col-lg-5 mb-5">
        <nuxt-link to="/buku" class="link-card">
          <div class="card bg-buku rounded-5">
            <div class="card-body">
              <h2 class="card-title">CARI BUKU</h2>
            </div>
          </div>
        </nuxt-link>
      </div>
    </div>
    <h2 class="statistik-title">STATISTIK</h2>
    <div class="row my-5 justify-content-around">
      <div class="col-lg-5 mb-5">
        <div class="card bg-spengunjung rounded-5">
          <div class="card-body">
            <div class="row">
              <div class="col">
                <h1 class="statistik-number">{{ visitor }}</h1>
              </div>
              <div class="col mt-5">
                <h2>PENGUNJUNG</h2>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="col-lg-5 mb-5">
        <div class="card bg-sbuku rounded-5">
          <div class="card-body">
            <div class="row">
              <div class="col">
                <h1 class="statistik-number">{{ book }}</h1>
              </div>
              <div class="col mt-5">
                <h2>BUKU</h2>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="row justify-content-center">
      <div class="col-12">
        <div class="chart">
          <chart-statistik />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
useHead({ title: "Home" })
const supabase = useSupabaseClient()
const book = ref(0)
const visitor = ref(0)

const hitungDatabuku = async () => {
  const { data, count } = await supabase.from("buku").select("*", { count: 'exact' })
  if (data) book.value = count
}

const hitungData = async () => {
  const { data, count } = await supabase.from("pengunjung").select("*", { count: 'exact' })
  if (data) visitor.value = count
}

onMounted(() => {
  hitungDatabuku()
  hitungData()
})
</script>

<style scoped>
.card {
  height: 176px;
  border-radius: 30px;
  box-shadow: 1px 1px 10px #000000;
}

.card.bg-pengunjung {
  background-image: url(../assets/img/pengunjung.png);
  background-size: cover;
  background-position: center;
}

.card.bg-buku {
  background-image: url(../assets/img/buku.png);
  background-size: cover;
  background-position: center;
}

.card.bg-spengunjung {
  background-color: #ffed92;
}

.card.bg-sbuku {
  background-color: #9da7ff;
}

.statistik-title {
  font-family: inter;
  margin-left: 100px;
}

.statistik-number {
  font-size: 110px;
}

.chart {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 100px;
}

.link-card {
  text-decoration: none;
  color: inherit;
}
</style>
