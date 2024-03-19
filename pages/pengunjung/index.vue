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
          <input type="search" class="form-control form-control-lg rounded-5" placeholder="filter...." />
        </div>
        <div class="my-3 text-muted">menampilkan 3 dari 3</div>
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
        <tr>
          <td>1</td>
          <td>Fajar ismail</td>
          <td>Siswa</td>
          <td>26 februari 2024, 10.10.00</td>
          <td>PINJAM BUKU</td>
        </tr>
        <tr>
          <td>2</td>
          <td>MAIL</td>
          <td>Siswa</td>
          <td>26 februari 2024, 7.20.00</td>
          <td>PINJAM BUKU</td>
        </tr>
        <tr>
          <td>3</td>
          <td>UDIN NGANGA</td>
          <td>Siswa</td>
          <td>25 februari 2024, 12.58.33</td>
          <td>PINJAM BUKU</td>
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