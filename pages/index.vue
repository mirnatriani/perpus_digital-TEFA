<template>
  <div class="container-fluid">
    <div class="row my-5">
      <div class="col-lg-6">
        <nuxt-link to="/pengunjung/tambah">
          <div class="card bg-pengunjung rounded-5">
            <div class="card-body">
              <h2>Pengunjung</h2>
            </div>
          </div>
        </nuxt-link>
      </div>

      <div class="col-lg-6">
        <nuxt-link to="/buku">
          <div class="card bg-buku rounded-5">
            <div class="card-body">
              <h2>Cari Buku</h2>
            </div>
          </div>
        </nuxt-link>
      </div>

      <div class="col-lg-6">
        <div class="card pengunjung rounded-5 mt-5">
          <div class="card-body">
            <h2>Jumlah Pengunjung</h2>
          </div>
        </div>
      </div>

      <div class="col-lg-6">
        <div class="card buku rounded-5 mt-5">
          <div class="card-body">
            <h2>Jumlah Buku</h2>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.card {
  height: 250px;
  box-shadow: 1px 1px 10px #424242;
}
.card.bg-pengunjung {
  background-image: url("../assets/img/bg-home-kunjungan.jpg");
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
}
.card.bg-buku {
  background: url("../assets/img/bg-home-cari-buku.jpg") no-repeat center center;
  background-size: cover;
}
.card.pengunjung {
  background-color: #f3eebb;
}
.card.buku {
  background-color: #c5fbc0;
}
</style>
