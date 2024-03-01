<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-lg-12">
        <h2 class="text-center my-4">Cari Buku</h2>
        <div class="my-3">
          <input type="search" class="form-control rounded-5" placeholder="Mau baca apa hari ini">
        </div>
        <div class="my-3 text-muted">menampilkan 4 dari 4</div>
        <div class="row">
          <div class="col-lg-2">
            <div class="card mb-3">
              <div class="card-body">
                <img src="~assets/img/gambar1.jpeg" class="gambar" alt="gambar1" />
              </div>
            </div>
          </div>
          <div class="col-lg-2">
            <div class="card mb-3">
              <div class="card-body">
                <img src="~assets/img/gambar2.jpg" class="gambar" alt="gambar2" />
              </div>
            </div>
          </div>
          <div class="col-lg-2">
            <div class="card mb-3">
              <div class="card-body">
                <img src="~assets/img/gambar3.jpg" class="gambar" alt="gambar3" />
              </div>
            </div>
          </div>
          <div class="col-lg-2">
            <div class="card mb-3">
              <div class="card-body">
                <img src="~assets/img/gambar4.jpg" class="gambar" alt="gambar4" />
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="d-flex justify-content-end">
    <NuxtLink to="/" class="btn btn-secondary btn-lg rounded-5 px-5">Kembali</NuxtLink>
  </div>
</template>
<style scoped>
.card-body {
  width: 100%;
  height: 20em;
  padding: 0;
}
.gambar {
  width: 100%;
  height: 100%;
  object-fit: gambar;
  object-position: 0 30;
}
</style>
