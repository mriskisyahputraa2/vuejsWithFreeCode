# computed
Dalam Vue.js, computed properties digunakan untuk membuat properti yang dinamis dan bergantung pada properti lain dalam komponen. Ini memungkinkan Anda untuk membuat properti yang secara otomatis diperbarui setiap kali properti yang mendasar diperbarui. Hal ini membantu Anda membuat logika yang rumit dalam komponen dengan mudah dan membuat aplikasi Anda lebih bersih dan mudah dikelola.

# components
Komponen memungkinkan kita membagi UI menjadi bagian-bagian yang independen dan dapat digunakan kembali, dan memikirkan masing-masing bagian secara terpisah. Merupakan hal yang umum bagi aplikasi untuk diatur ke dalam pohon komponen bersarang.
ex, jika kita memiliki header, main, articel 1-3, hal ini bisa di bagi menjadi beberapa bagian kecil

# example code: 
1. export default {
  data() {
    return {
      count: 0
    }
  },
  template: `
    <button @click="count++">
      You clicked me {{ count }} times.
    </button>`
}

== Template disisipkan sebagai string JavaScript di sini, yang akan dikompilasi oleh Vue dengan cepat. Anda juga dapat menggunakan pemilih ID yang menunjuk ke suatu elemen (biasanya <template>elemen asli) - Vue akan menggunakan kontennya sebagai sumber template.

Contoh di atas mendefinisikan satu komponen dan mengekspornya sebagai ekspor default dari sebuah .jsfile, tetapi Anda dapat menggunakan ekspor bernama untuk mengekspor beberapa komponen dari file yang sama.

2. 
// build in html
<login-form/> 

// build in js
app.component('login-form', {
            template: `
                <form @submit.prevent="handelSubmit"> 
                    <h1>{{ title }}</h1>
                    <input type="text" placeholder="username" v-model="email" />  
                    <input type="password" placeholder="password" v-model="password" /> 
                    <button>Log in</button>   
                </form>
            `,
            data(){
                return{
                    title: 'Login Form',
                    email: '',
                    password: ''
                }
            },
            methods: {
                handelSubmit(){
                    console.log(this.email, this.password)
                }
            }
        })



# component props / menangkap komponent



# computed 
Ekspresi dalam templat sangat nyaman, tetapi dimaksudkan untuk operasi sederhana. Menempatkan terlalu banyak logika di template Anda dapat membuatnya membengkak dan sulit dipertahankan. Misalnya, jika kita memiliki objek dengan array bersarang:
js

export default {
  data() {
    return {
      author: {
        name: 'John Doe',
        books: [
          'Vue 2 - Advanced Guide',
          'Vue 3 - Basic Guide',
          'Vue 4 - The Mystery'
        ]
      }
    }
  }
}

Dan kami ingin menampilkan pesan yang berbeda tergantung pada apakah authorsudah memiliki beberapa buku atau belum:
templat

<p>Has published books:</p>
<span>{{ author.books.length > 0 ? 'Yes' : 'No' }}</span>

Pada titik ini, template menjadi sedikit berantakan. Kita harus melihatnya sejenak sebelum menyadari bahwa ia melakukan perhitungan tergantung pada author.books. Lebih penting lagi, kita mungkin tidak ingin mengulang sendiri jika kita perlu memasukkan perhitungan ini ke dalam template lebih dari satu kali.

Itu sebabnya untuk logika kompleks yang menyertakan data reaktif, disarankan untuk menggunakan properti yang dihitung . Berikut contoh yang sama, di-refactored:
js

export default {
  data() {
    return {
      author: {
        name: 'John Doe',
        books: [
          'Vue 2 - Advanced Guide',
          'Vue 3 - Basic Guide',
          'Vue 4 - The Mystery'
        ]
      }
    }
  },
  computed: {
    // a computed getter
    publishedBooksMessage() {
      // `this` points to the component instance
      return this.author.books.length > 0 ? 'Yes' : 'No'
    }
  }
}

templat

<p>Has published books:</p>
<span>{{ publishedBooksMessage }}</span>

