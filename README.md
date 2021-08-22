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