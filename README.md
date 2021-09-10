<p align="center"><a href="https://vuejs.org/" target="_blank"><img src="https://vuejs.org/images/logo.svg" width="200"></a></p>

# Belajar-Vuejs

1. Mendownload Extensen pada browser yaitu extensi Vuejs
2. Menaruh [CDN](https://vuejs.org/v2/guide/installation.html#CDN) dari Vuejs ke program

   > CDN dapat didwonload dan sebagai asset dan juga bisa di akses secara online

   ```js
   <script src="https://cdn.jsdelivr.net/npm/vue@2.6.14"></script>
   ```

# [Options / DOM](https://vuejs.org/v2/api/#Options-DOM)

## el

1. Menginisialisasi objek Vue
   ```js
   new Vue();
   ```
2. Bungkus content dari HTMl atau halaman web yang nantinya bisa di akses oleh Vuejs

   > pembungkus harus di beri id atau name atau class agar nantinya dapat di baca oleh el dari vue

   ```html
   <div id="app">
     <!-- Content atau html yang akan dapat di akses oleh vue -->
   </div>
   ```

   > Setelah html yang inggin di aksess di bungkus maka pada objek vue tambahkan el yang dimana akan mengambil dari id atau name atau class yang sudah di tuliskan pada sebelumnya

   ```js
   new Vue({
     el: "#app",
   });
   ```

# [Options / Data](https://vuejs.org/v2/api/#Options-Data)

## Data

> Data merupakan sebuah properti pada vue yang berisi variabel yang dapat di isikan sebuah data

- Menambhkan properti data
  ```js
  new Vue({
    el: "#app",
    data: {
      name: "abdul",
      jurusan: "Informatika",
    },
  });
  ```
- Pemangilan
  ```html
      <h2>{{ name }}</h2>
      <h2>{{ jurusan }}</2>
  ```

## Method

> Metod merupakan sebuah properti yang akan di tambahkan dimana value nya berisi sebuah fungsi-fungsi yang nantinya dapat di pergunakan dan dapat di panggil pada halaman html

- menambhkan properti methods
  ```js
  new Vue({
    el: "#app",
    data: {
      name: "abdul",
    },
    methods: {
      // metod tanpa parameter
      getname: function () {
        return "Abdul " + this.name;
      },
      // metod dengan parameter
      updateName: function (newName) {
        return (this.name = newName);
      },
    },
  });
  ```
- Pemangilan
  ```html
  <h2>{{ getname() }}</h2>
  ```

## Computed Property

> Menambhkan sebuah properti sendiri, yang nantinya di simpan pada properti compted.

- Menambah properti computed
  ```js
      new Vue({
                  el: '#app',
                  data: {
                          name: 'SmartPhone',
                          qty: 0,
                          price: 5000000
                  },
                  methods: {
                          // isi metod
                      }
                  },
                  computed: {
                      totalPrice: function() {
                          return  this.qty * this.price
                      }
                  }
              })
  ```
- pemangilan

```html
{{ totalPrice }}
```

# [Directives](https://vuejs.org/v2/api/#Directives)

## v-text

> v-text untuk memangil sebuah variabel namun hanya dengan menambhkan atribut pada html namun data yang di tampilkan berupa String

```html
<!-- Mengunakan v-text -->
<span v-text="msg"></span>

<!-- Cara biasa -->
<span>{{msg}}</span>
```

## v-html

> v-html untuk memangil sebuah variabel namun hanya dengan menambhkan atribut pada html namun data yang di tampilkan berupa tag html

- Contoh data

```js
    data: {
            judul: '<h1> Coba v-html </h1>',
    },
```

- pemangilan

```html
<!-- Mengunakan v-text -->
<div v-html="html"></div>
```

## v-for

- data

```js
    'kelas': ['PHP', 'JAVA', 'Python'],
```

- Perualangan
  > Diaman k sebagai alias dari key variabel

```js
<ul>
  <li v-for="k in kelas">
    <h2>{{ k }}</h2>
  </li>
</ul>
```

- Cotoh perulangan 5x

```html
<ul>
  <li v-for="x in 5">{{ x }}</li>
</ul>
```

## v-if

- data

```js
    'kelas': [],
```

> Dimana if mengecek apakah variabel index terdapat data tidak ada data akan menjalankan v-else dan tag di dalam if akan di hapus
> v-else harus sejajar dan di bawah v-if jika terpisah dengan tag lain maka else diangap bukan bagian if di atas

```html
<ul v-if="kelas.length >= 1">
  <li v-for="(k , index) of kelas">
    <h4>{{ index+1 }} : {{ k }}</h4>
  </li>
</ul>
<li v-else>Kelas kosong</li>
```

> v-if di atas di tempatkan pada tag ul, namun dapat juga di tempatkan pada tag tamplate, perbedaan dengan sebelumnya jika mengunakan template, tag tamplate tidak akan di munculkan pada halaman html

```html
<template v-if="">
  ...
  <template></template
></template>
```

## v-show

> v-show hampir sama dengan if namun v-show tidak menghilangkan tag html, namun merubah display menjadi none.
> Pada v-show tidak dapat mengunakan tamplate seperti v-if

```html
<ul v-if="kelas.length >= 1">
  <li v-for="(k , index) of kelas">
    <h4>{{ index+1 }} : {{ k }}</h4>
  </li>
</ul>
```

# [Event Handling](https://vuejs.org/v2/guide/events.html)

## Listening to Events

- pada script

```js
         <script>
                const isi = {
                    bil: 0,
                }
                const vm = new Vue({
                    el: '#app',
                    data: isi,
                    // membuat metod
                    methods: {
                    },
                    computed: {
                        hitung: function () {
                            return this.bil % 2 === 0 ? "Genap" : "Ganjil"
                        }
                    }
                })
            </script>
```

- pengunaan

```html
<button v-on:click="bil++">Click</button>
```

## Event Modifiers

> Dimana dengan program di bawah saya emembuat sebuah menu navigasi jika salah 1 menu di klik maka class active akan muncul pada class

- pada script

```js
    data {
        'menu': 'tiga',
    },
    methods: {
        gantimenu: function (data, event) {
            this.menu_b = data

        },
    }
```

- cara pengunaan

```html
<a
  href="classbinding.html"
  v-bind:class="{active: menu === 'satu'}"
  v-on:click.prevent="gantimenu('satu')"
  >Tombol 1</a
>
<a
  href="classbinding.html"
  v-bind:class="{active: menu === 'dua'}"
  v-on:click.prevent="gantimenu('dua')"
  >Tombol 2</a
>
<a
  href="classbinding.html"
  v-bind:class="{active: menu === 'tiga'}"
  v-on:click.prevent="gantimenu('tiga')"
  >Tombol 3</a
>
```

## Key Modifiers

> Dimana jika berada pada inputan jika di enter maka akan menjalnkan metod submit

- pada script

```js
    submit: function (e) {
        // Mengambil value dari inputan
            let text = event.target.value
        // meng pus atau memasukkan kedalam variabel text kedalam variabel input
            this.input.push(text)
            event.target.value = ''
    }
```

- pengunaan

```html
<input type="text" placeholder="Input 1" v-on:keyup.enter="submit" />
```

# [Class and Style Bindings](https://vuejs.org/v2/guide/class-and-style.html)

- Cara pengunaan

  ```html
  <div
    class="static"
    v-bind:class="{ active: isActive, 'text-danger': hasError }"
  ></div>
  ```

- Data

  ```js
    data: {
    isActive: true,
    hasError: false
    }
  ```

> Maka yang akan terjadi pada script diatas : dimana pada data isActive berisi true maka otomatis akan menjalankan active.

> Script menjadi

```html
<div class="static active"></div>
```

# [Form Input Binding](https://vuejs.org/v2/guide/forms.html)

> yaitu sebuah inputan yang dimana akan langsung di tampung pada data dan langsung dapat di panggil

## Text

> Ada banyak inputan yang dapat di gunakan namun pada latihan kali ini saya mengunakan text
> Dimana mengunkaan v-model yang didalamya berupa variabel data, nantinya text yang di inputkan langsung di tampung oleh data.

    ```html
    <input v-model="message" placeholder="edit me" />
    <p>Message is: {{ message }}</p>
    ```

- Contoh ke dua

  > dimana dengan contoh dibawah kita tidak perlu lagi mengakses value pada inputan namun hanya menambhkan v-model dan nama variabel maka apa yang di inputkan akan di simpan pada variabel

  ```js
    data: {
        'input': [],
        'kelas': ''
    }
    metod: {
        submit: function (e) {
                    this.input.unshift(this.kelas)
                    this.kelas = ''
                }
    }
  ```

  ```html
  <h3 v-text="kelas"></h3>
  <input
    type="text"
    placeholder="Input 2"
    v-on:keyup.enter="submit"
    v-model="kelas"
  />
  ```

# [Components Basics](https://vuejs.org/v2/guide/components.html)

- Cara pembuatan component

  ```js
  Vue.component("atas", {
    title: ['title'],
    template: `
            <header class="card">
                <img src="https://vuejs.org/images/logo.svg" width="200px">
                <h1>{{ title }}</h1>
            </header>
            `,
    data: function () {
      return {
        <!-- isi data -->
      };
    },
    methods: {
                <!-- Metod -->
            }
  });
  ```

- cara pemanggilan

  ```html
  <atas title="latihan - latihan ke 2 Vuejs"></atas>
  ```

  - Cara component mengunakan data pada induk

  - data pada induk

  ```js
  const isi = {
    kelas: [],
    kelasbaru: [],
  };
  ```

  > Sebelum mengunakan data pada induk buat props nantinya begagai properti pada component

  ```js
  Vue.component("kelas", {
    props: ["title", "kelas", "kelasbaru"],
    template: `
            <div>
                <input type="text" class="input-text" placeholder=" Input Kelas" v-on:keyup.enter="submit" v-model="kelasbaru">
                <h3>{{ title }}</h3>
                <ul >
                    <template v-if="kelas.length >= 1">
                        <li v-for="(k, index) in kelas" :key="index">
                            <h4 v-text="k"></h4>
                            <a href="" v-on:click.prevent="$emit('hapuskelas')">Hapus</a>
                        </li>
                    </template>
                    <li v-else>Kelas kosong</li>
                </ul>
            <div>
            `,
    data: function () {
      return {};
    },
    methods: {
      submit: function () {
        this.kelas.unshift(this.kelasbaru);
        this.kelasbaru = "";
      },
    },
  });
  ```

  - pemanggilan
    > Dimana mengunakan properti yang sudah di buat dan disi dengan nama variabel pada induk

  ```html
  <kelas
    title="Daftar Kelas :"
    v-bind:kelas="kelas"
    v-on:hapuskelas="hapuskelas"
  ></kelas>
  ```

# [Listening to Child Components Events](https://vuejs.org/v2/guide/components.html#Listening-to-Child-Components-Events)

> yaitu komunikasi induk dengan component anak dengan cara mengcustum component

```html
<a href="" v-on:click.prevent="$emit('hapuskelas')">Hapus</a>
```

> metods pada Induk

```js
methods: {
                hapuskelas: function(e) {
                    // data kelas yang dimana mempunyai index yang di pilih lalu hapus 1 data
                    this.kelas.splice(e, 1)
                }
            },
```

# Mengunakan [History](https://vuejs.org/v2/guide/migration-vue-router.html#history-true-replaced)

```js
const router = new VueRouter({
  mode: "history",
  routes,
});
```

[Terakhir tutorial 50](https://www.youtube.com/playlist?list=PL9At9z2rvOC-Z6Gt8uO1XMp4oyMlE3gml)
