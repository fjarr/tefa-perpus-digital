<template>
  <div class="container-fluid" style="width: 95%">
    <div class="row">
      <div class="col-2">
        <nuxt-link to="../">
          <i class="bi bi-arrow-left-short"></i>
        </nuxt-link>
      </div>
      <div class="col-8">
        <h2 style="
            text-align: center;
            font-family: inter;
            margin-top: 20px;
            text-align: center;
          ">
          ISI FORM PENGUNJUNG
        </h2>
      </div>
      <div class="col-lg-12">
        <form>
          <div class="mb-3">
            <input type="text" class="form-control form-control-lg rounded-5" placeholder="NAMA........" />
          </div>
          <div class="mb-3">
            <select class="form-control form-control-lg form-select rounded-5">
              <option value="">KATEGORI</option>
              <option value="Siswa">Siswa</option>
              <option value="Guru">Guru</option>
              <option value="Staf">Staf</option>
              <option value="Umum">Umum</option>
            </select>
          </div>
          <div class="mb-3">
            <div class="row">
              <div class="col-md-4">
                <select class="form-control form-control-lg form-select rounded-5 mb-2">
                  <option value="">KELAS</option>
                  <option value="X">X</option>
                  <option value="XI">XI</option>
                  <option value="XII">XII</option>
                </select>
              </div>
              <div class="col-md-4">
                <select class="form-control form-control-lg form-select rounded-5 mb-2">
                  <option value="">JURUSAN</option>
                  <option value="PPLG">PPLG</option>
                  <option value="TJKT">TJKT</option>
                  <option value="TSM">TSM</option>
                  <option value="DKV">DKV</option>
                  <option value="TOI">TOI</option>
                </select>
              </div>
              <div class="col-md-4">
                <select class="form-control form-control-lg form-select rounded-5 mb-2">
                  <option value="">NO KELAS</option>
                  <option value="1">1</option>
                  <option value="2">2</option>
                  <option value="3">3</option>
                  <option value="4">4</option>
                </select>
              </div>
            </div>
          </div>
          <div class="input-group mt-3">
            <textarea class="form-control rounded-5 mb-2" aria-label="With textarea"
              placeholder="KEPERLUAN........"></textarea>
          </div>
          <div class="input-group mt-4">
            <button type="button" class="btn btn-outline-primary rounded-4"
              style="color: black; font-family: lnria-serif">
              KIRIM
            </button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>
<style scoped>
i{
  font-size: 60px; color: #000000
}
@media only screen and (max-width: 820px) {
  h2 {
    font-size: 15px;
  }

  i{
    font-size: 35px;
    color: #000000;
  }
}
</style>

