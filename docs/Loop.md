# v-for
Kita dapat menggunakan v-for arahan untuk merender daftar item berdasarkan array. Direktif v-for memerlukan sintaks khusus dalam bentuk item in items, di mana items array data sumber dan item merupakan alias untuk elemen array yang sedang diiterasi:
example Code :
data() {
  return {
    items: [{ message: 'Foo' }, { message: 'Bar' }]
  }
}

<li v-for="item in items">
  {{ item.message }}
</li>

Di dalam v-forlingkup, ekspresi template memiliki akses ke semua properti lingkup induk. Selain itu, v-forjuga mendukung alias kedua opsional untuk indeks item saat ini:

data() {
  return {
    parentMessage: 'Parent',
    items: [{ message: 'Foo' }, { message: 'Bar' }]
  }
}

templat

<li v-for="(item, index) in items">
  {{ parentMessage }} - {{ index }} - {{ item.message }}
</li>

Induk - 0 - Foo
Induk - 1 - Bar