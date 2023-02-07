    # Lifecycle Hooks
Lifecycle Hooks adalah metode yang dapat digunakan untuk memantau dan memodifikasi tahapan dalam hidup sebuah komponen Vue. Ini memungkinkan kita untuk mengeksekusi kode spesifik pada saat tahapan tertentu dalam komponen, seperti saat komponen dibuat, diperbarui, atau dihapus. 
Tujuan dari penggunaan lifecycle hooks adalah untuk memberikan kontrol lebih terhadap component dan melakukan tindakan-tindakan tertentu seperti memuat data, memperbarui tampilan, dan membersihkan resource sebelum component dimatikan.


# Lifecycle Hooks, sering digunakan saat:
1. memeriksa apakah user diberi otoritas or tidak 
2. Memanggil API ke dalam backend atau penyimpanan browser
3. membuat events atau saat akan di unmount meremove / membersihkan events
4. dan dapat menyimpan data, atau menjalankan semacam pemeriksaan sebelum unmount atau membersihkan data


# List Lifecycle hook : 
1. beforeCreate: Hook ini dipanggil sebelum instance dari komponen Vue dibuat, dan belum diinisialisasi.
 
2. created: Hook ini dipanggil setelah instance dari komponen Vue telah dibuat dan diinisialisasi.
 
3. beforeMount: Hook ini dipanggil sebelum instance dari komponen Vue dipasang ke DOM.
 
4. mounted: Hook ini dipanggil setelah instance dari komponen Vue telah dipasang ke DOM.
Hook mounted dalam Vue.js merupakan lifecycle hook yang dipanggil setelah komponen telah ditempatkan pada DOM. Ini berarti bahwa semua elemen dalam komponen sudah siap digunakan dan dapat dimanipulasi. Hook ini sangat berguna ketika Anda ingin melakukan inisialisasi atau memuat data ketika komponen pertama kali ditempatkan pada halaman.

Contohnya, Anda dapat menggunakan hook mounted untuk memuat data dari API, memulai animasi, atau memasang event listener pada elemen dalam komponen. Dengan demikian, Anda dapat memastikan bahwa semua tugas inisialisasi selesai sebelum komponen ditampilkan pada halaman.
 
5. beforeUpdate: Hook ini dipanggil sebelum instance dari komponen Vue diperbarui.
 
6. updated: Hook ini dipanggil setelah instance dari komponen Vue diperbarui.
 
7. beforeDestroy: Hook ini dipanggil sebelum instance dari komponen Vue dimusnahkan.
 
8. destroyed: Hook ini dipanggil setelah instance dari komponen Vue dimusnahkan.


# Lifecycle hook yang paling sering digunakan pada Vue.js adalah:

    created: digunakan untuk melakukan aktivitas seperti memuat data atau melakukan inisialisasi setelah component telah dibuat dan elemennya telah dimuat.

    mounted: digunakan untuk melakukan aktivitas setelah component telah ditempatkan pada DOM dan siap untuk diterima input atau interaksi pengguna.

    beforeDestroy: digunakan untuk melakukan aktivitas seperti membersihkan resource sebelum component dimatikan.

Namun, pemilihan lifecycle hook yang sesuai akan tergantung pada kebutuhan dan logika aplikasi yang dikembangkan.
