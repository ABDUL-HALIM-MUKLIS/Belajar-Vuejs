<p align="center"><a href="https://vuejs.org/" target="_blank"><img src="https://vuejs.org/images/logo.svg" width="200"></a></p>

# Belajar-Vuejs
1. Mendownload Extensen pada browser yaitu extensi Vuejs
2. Menaruh [CDN](https://vuejs.org/v2/guide/installation.html#CDN) dari Vuejs ke program
    > CDN dapat didwonload dan sebagai asset dan juga bisa di akses secara online

    ```js
        <script src="https://cdn.jsdelivr.net/npm/vue@2.6.14"></script>
    ```
2. Menginisialisasi objek Vue
    ```js
        new Vue()
    ```
3. Bungkus content dari HTMl atau halaman web yang nantinya bisa di akses oleh Vuejs
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

# Data
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

# Method
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

# Computed Property
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