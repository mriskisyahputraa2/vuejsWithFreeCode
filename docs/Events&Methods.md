# LISTENING TO EVENTS
  Kita dapat menggunakan v-on direktif, yang biasanya kita persingkat menjadi @simbol, untuk mendengarkan peristiwa DOM dan menjalankan beberapa JavaScript saat dipicu. Penggunaannya adalah v-on:click="handler"atau dengan pintasan, @click="handler".
  Nilai handler dapat berupa salah satu dari berikut ini:

  1. Inline handlers: JavaScript sebaris yang akan dieksekusi saat peristiwa dipicu (mirip dengan onclick atribut asli).
  2.Method handlers: Nama properti atau jalur yang menunjuk ke metode yang ditentukan pada komponen.

# Example Code:
1. Handler Inline:
Handler Inline, sebaris biasanya digunakan dalam kasus sederhana, misalnya:

  data() {
    return {
      count: 0
    }
  }

  <button @click="count++">Add 1</button>
  <p>Count is: {{ count }}</p>

# ===================================================================

2. Method Handlers 
Logika untuk banyak event handler akan lebih kompleks, dan sepertinya tidak layak dengan inline handler. Itu sebabnya v-onjuga bisa menerima nama atau path dari metode komponen yang ingin Anda panggil.
  
  data() {
  return {
    name: 'Vue.js'
  }
  },
  methods: {
    greet(event) {
      // `this` inside methods points to the current active instance
      alert(`Hello ${this.name}!`)
      // `event` is the native DOM event
      if (event) {
        alert(event.target.tagName)
      }
    }
  }

  <!-- `greet` is the name of the method defined above -->
  <button @click="greet">Greet</button>


# Event Modifiers
Ini adalah kebutuhan yang sangat umum untuk menelepon event.preventDefault()atau event.stopPropagation()di dalam event handler. Meskipun kita dapat melakukannya dengan mudah di dalam metode, akan lebih baik jika metode tersebut murni tentang logika data daripada harus berurusan dengan detail peristiwa DOM.

Untuk mengatasi masalah ini, Vue menyediakan pengubah acara untuk v-on. Ingatlah bahwa pengubah adalah postfix direktif yang dilambangkan dengan titik.

# SEBAGAI PEMBANTU EVENTS:
.stop  = berhenti
.prevent = mencegah
.self = dirisendiri
.capture  = menangkap
.once = sekali/pertama
.passive = passive biasanya digunakan dengan pemroses peristiwa sentuh untuk meningkatkan kinerja pada perangkat seluler .

Pengubah .capture, .once, dan .passive mencerminkan opsi dari addEventListenermetode asli

# example code: 
<!-- the click event's propagation will be stopped -->
<a @click.stop="doThis"></a>

<!-- the submit event will no longer reload the page -->
<form @submit.prevent="onSubmit"></form>

<!-- modifiers can be chained -->
<a @click.stop.prevent="doThat"></a>

<!-- just the modifier -->
<form @submit.prevent></form>

<!-- only trigger handler if event.target is the element itself -->
<!-- i.e. not from a child element -->
<div @click.self="doThat">...</div>




# NOTE
Urutan penting saat menggunakan pengubah karena kode yang relevan dihasilkan dalam urutan yang sama. Oleh karena itu, penggunaan @click.prevent.self akan mencegah tindakan default klik pada elemen itu sendiri dan turunannya , sementara @click.self.preventhanya akan mencegah tindakan default klik pada elemen itu sendiri.

# NOTE
Jangan gunakan .passivedan .preventbersama-sama, karena .passivesudah menunjukkan ke browser bahwa Anda tidak bermaksud mencegah perilaku default acara, dan kemungkinan besar Anda akan melihat peringatan dari browser jika Anda melakukannya.


# Key Modifiers 
Saat mendengarkan acara keyboard, kami sering kali perlu memeriksa tombol tertentu. Vue memungkinkan penambahan pengubah kunci untuk v-onatau @saat mendengarkan acara utama:

# Example Code: 
1. <input @keyup.enter="submit" /> or 
akan menjalankan events keyboard sesuai nama ex: enter


2. <input @keyup.page-down="onPageDown" />
Pada contoh di atas, handler hanya akan dipanggil jika $event.keysama dengan 'PageDown'.

# Key Aliases
Vue menyediakan alias untuk kunci yang paling umum digunakan:

1. .enter
2. .tab
3. .delete(menangkap tombol "Hapus" dan "Backspace")
4. .esc
5. .space
6. .up
7. .down
8. .left
9. .right


# System Modifier Keys
Anda dapat menggunakan pengubah berikut untuk memicu event listener mouse atau keyboard hanya ketika tombol pengubah yang sesuai ditekan:

.ctrl
.alt
.shift

# example code : 
<!-- Alt + Enter -->
<input @keyup.alt.enter="clear" />

<!-- Ctrl + Click -->
<div @click.ctrl="doSomething">Do something</div>


# Mouse Button Modifiers / Pengubah Tombol Mouse
 
.left
.right
.middle

Pengubah ini membatasi penangan ke peristiwa yang dipicu oleh tombol mouse tertentu.

# .exact Modifier / Pengubah

Pengubah .exactmemungkinkan kontrol kombinasi yang tepat dari pengubah sistem yang diperlukan untuk memicu suatu peristiwa.

# example code:

<!-- this will fire even if Alt or Shift is also pressed -->
<button @click.ctrl="onClick">A</button>

<!-- this will only fire when Ctrl and no other keys are pressed -->
<button @click.ctrl.exact="onCtrlClick">A</button>

<!-- this will only fire when no system modifiers are pressed -->
<button @click.exact="onClick">A</button>