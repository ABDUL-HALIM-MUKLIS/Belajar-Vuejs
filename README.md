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
        new Vue()
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
            el: '#app'
        })
    ```

# [Options / Data](https://vuejs.org/v2/api/#Options-Data) 
## Data
> Data merupakan sebuah properti pada vue yang berisi variabel yang dapat di isikan sebuah data

* Menambhkan properti data
    ```js
        new Vue({
                    el: '#app',
                    data: {
                        name: 'abdul',
                        jurusan: 'Informatika'
                    }
                })
    ``` 
* Pemangilan
    ```html
        <h2>{{ name }}</h2>
        <h2>{{ jurusan }}</2>
    ```

## Method
> Metod merupakan sebuah properti yang akan di tambahkan dimana value nya berisi sebuah fungsi-fungsi yang nantinya dapat di pergunakan dan dapat di panggil pada halaman html

* menambhkan properti methods
    ```js
        new Vue({
                    el: '#app',
                    data: {
                        name: 'abdul'
                    },
                    methods: {
                        // metod tanpa parameter
                        getname: function () {
                            return 'Abdul ' + this.name
                        },
                        // metod dengan parameter
                        updateName: function (newName) {
                            return this.name = newName
                        }
                    }
                })
    ``` 
* Pemangilan
    ```html
        <h2>{{ getname() }}</h2>
    ```

## Computed Property
> Menambhkan sebuah properti sendiri, yang nantinya di simpan pada properti compted.
* Menambah properti computed
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
* pemangilan 
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

* Contoh data
```js
    data: {
            judul: '<h1> Coba v-html </h1>',
    },
```
* pemangilan
```html
    <!-- Mengunakan v-text -->
    <div v-html="html"></div>
```

# [Events](https://vuejs.org/v2/api/#vm-on)
## vm.$on

```html
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
```html
     <button v-on:click="bil++">Click</button>
```


# [Class and Style Bindings](https://vuejs.org/v2/guide/class-and-style.html)
* Cara pengunaan
```html
    <div
    class="static"
    v-bind:class="{ active: isActive, 'text-danger': hasError }"
    ></div>
```

* Data
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

> Ada banyak inputan yang dapat di gunakan namun pada latihan kali ini saya mengunakan text
> Dimana mengunkaan v-model yang didalamya berupa variabel data, nantinya text yang di inputkan langsung di tampung oleh data.
```html
    <input v-model="message" placeholder="edit me">
    <p>Message is: {{ message }}</p>
```


[Terakhir tutorial 22](https://www.youtube.com/playlist?list=PL9At9z2rvOC-Z6Gt8uO1XMp4oyMlE3gml)

