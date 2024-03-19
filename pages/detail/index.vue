<template>
  <div>
    <div class="container mt-4">
      <table style="width: 90%">
        <tr>
          <td rowspan="8">
            <img src="../../assets/img/buku1.jpg" alt="" srcset="" />
          </td>
          <td class="ps-5" colspan="5">
            <h1 style="font-family: inter">DETAIL BUKU</h1>
          </td>
        </tr>
        <tr>
          <td class="ps-5">JUDUL</td>
          <td class="ps-5">:</td>
          <td>Malin Kundang</td>
        </tr>
        <tr>
          <td class="ps-5">PENULIS</td>
          <td class="ps-5">:</td>
          <td>Happy Holy Kids</td>
        </tr>
        <tr>
          <td class="ps-5">PENERBIT</td>
          <td class="ps-5">:</td>
          <td>Buku Kita</td>
        </tr>
        <tr>
          <td class="ps-5">TAHUN TERBIT</td>
          <td class="ps-5">:</td>
          <td>20 Mei 2014</td>
        </tr>
        <tr>
          <td class="ps-5">KATEGORI</td>
          <td class="ps-5">:</td>
          <td>cerita</td>
        </tr>
        <tr>
          <td class="ps-5">RAK</td>
          <td class="ps-5">:</td>
          <td>109</td>
        </tr>
        <tr>
          <td class="ps-5">DESKRIPSI</td>
          <td class="ps-5">:</td>
          <td>
            Dongeng legenda dari Sumatera Bara berkisah tentang sebuah keluarga
            yang miskin karena ayahnya pergi merantau. Anaknya, Malin Kundang,
            yang menginjak remaja pun meninggalkan ibunya bertekad menjadi orang
            yang sukses. Setelah kaya, Malin kembali ke kampungnya, tetapi tidak
            mau mengakui ibunya yang miskin dan tua. Karena marah ibunya pun
            mengutuk anak itu...
          </td>
        </tr>
        <tr>
          <td rowspan="3"></td>
        </tr>
      </table>
      <div class="row">
        <div class="col"></div>
        <nuxt-link to="../buku">
          <div class="input-group mt-4">
            <button type="button" class="btn btn-outline-primary rounded-4">
              KEMBALI
            </button>
          </div>
        </nuxt-link>
      </div>
    </div>
  </div>
</template>
<style scoped>
img {
  width: 300px;
  height: 400px;
}

button {
  color: black;
  font-family: inter;
}

@media only screen and (max-width: 820px) {
  img {
    width: 6vh;
    height: auto;
  }

  table {
    font-size: 5px;
  }

  button {
    text-align: center;
    width: 40px;
    height: 20px;
    font-size: 5px;
    color: black;
    font-family: inter;
  }
}
</style>