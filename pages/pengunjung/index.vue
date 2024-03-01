<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-lg-12">
        <h2 class="text-center my-4">RIWAYAT KUNJUNGAN</h2>
        <div class="my-3">
          <input type="search" class="form-control form-control-lg rounded-5" placeholder="filter..." />
        </div>
        <div class="my-3 text-muted">menampilkan 3 dari 3</div>
        <table class="table">
          <thead>
            <tr>
              <td>NO</td>
              <td>NAMA</td>
              <td>KEANGGOTAAN</td>
              <td>WAKTU</td>
              <td>KEPERLUAN</td>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td>1.</td>
              <td>Mirna Triani</td>
              <td>Siswa</td>
              <td>27 Februari 2024, 11.00.01</td>
              <td>Pinjam Buku</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
  <NuxtLink to="/" class="btn btn-secondary btn-lg rounded-5 px-5">Kembali</NuxtLink>
</template>
