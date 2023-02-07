                1. v-model "argumen":
                v-model digunakan untuk menangkap nilai, yaitu argumen. sehingga nilai yang ditangkap dari argumen
                default bisa diubah sesuai keinginan pengguna. setiap data yang dimasukkan oleh user maka data akan berubah sesuai dengan user ketikan

                2. v-if="argumen":
                v-if sama dengan v-model menangkap argumen,v-if sama saja dengan if pada umunya ketika true akan tampil,
                ketika false tidak tampil

                v-else-if: jika v-else-if (false). maka, akan ke v-else. dan

                v-else: dan jika v-else true. maka program akan berhenti di v-else.

                3. v-show="argumen":
                v-show hampir sama dengan v-if, but when value-nya false. maka, ketika di inspect hasinya dibaris yang
                ada v-show maka div or syntax yang lain terdapat display:none;style itulah yang membuat elemenya hilang.

                4. v-clock:
                v-clock berfungsi menyembunyikan elemen-elemen yang ketika direload/rendering sebuah halaman web. tidak
                menampilkan element yang seharusnya tidak ditampilkan. dengan menambahkan display none di css maka
                halaman web akan siap dan lebih bagus lagi

                5. v-text:
                v-text akan menimpa text. sehingga harus menambahkan satu elemen lagi untuk memanggil argumen-nya

                6. v-bind
                v-bind mengubah atribut html menjadi sesuatu yang bisa di pakai di js or vuejs sehingga menjadi turunan component   