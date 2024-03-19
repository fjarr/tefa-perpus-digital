<template>
  <div>
    <div class="container-fluid">
      <div class="row">
        <div class="col-lg-2">
          <nuxt-link to="../">
            <i class="bi bi-arrow-left-short"></i>
          </nuxt-link>
        </div>
        <div class="col-lg-12">
          <div class="mt-1">
            <input type="search" class="form-control rounded-5" placeholder="Mau baca apa hari ini?" />
          </div>
        </div>
        <div class="my-3 text-muted">menampilkan 3 dari 3</div>
      </div>
      <div class="row">
        <div class="col-sm-2">
          <nuxt-link to="../detail">
            <div class="card mb-3">
              <div class="card-body">
                <img src="~/assets/img/buku1.jpg" class="cover" alt="cover 1" />
              </div>
            </div>
          </nuxt-link>
        </div>
        <div class="col-sm-2">
          <div class="card mb-3">
            <div class="card-body">
              <img src="~/assets/img/buku2.jpeg" class="cover" alt="cover 2" />
            </div>
          </div>
        </div>
        <div class="col-sm-2">
          <div class="card mb-3">
            <div class="card-body">
              <img src="~/assets/img/buku3.jpeg" class="cover" alt="cover 3" />
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<style scoped>
.card-body {
  width: 100%;
  height: 16em;
  padding: 0;
}

.cover {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: 0 30;
}

i {
  font-size: 60px;
  color: #000000
}

@media only screen and (max-width: 820px) {
  i {
    font-size: 35px;
    color: #000000;
  }

  .card-body {
    width: 100%;
    height: 8em;
    padding: 1;
  }

  .cover {
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: 0 30;
  }

}
</style>