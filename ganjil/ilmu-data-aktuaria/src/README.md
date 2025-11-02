# Panduan Sumber Daya Terpisah

Halo.

> Ini apa?

Ini adalah direktori untuk sumber daya terpisah. Mereka memuat modul-modul atau informasi yang tidak sekali pakai. Bisa digunakan berkali-kali tergantung dengan kebutuhan.

> Bagaimana cara menggunakannya?

Kita akan memanfaatkan [includes content](https://quarto.org/docs/authoring/includes.html) berdasarkan dokumentasi quarto ini. Untuk include sebuah file code singkat `{{< include >}}` di lokasi dokumennya tepat diletakan dibagian yang ingin disisipkan.

```
{{< include _content.qmd >}}
```

## Content 

Contoh konkret jika kamu punya banyak artikel tentang topik yang ingin dibagikan di pengenalan umumnya. 

````
---
title: "Revealjs Presentations"
---

## Overview

Revealjs Presentations are a great way to
present your ideas to others!

{{< include _basics.qmd >}}

## Revealjs Options

More content here...

## Do it yourself with R

```r 
{{< include _demo.R >}}
```

Copy the R code above in your session.

## Do it yourself with Python

```python
{{< include _demo.py >}}
```

Copy the Python code above and run it.

````

## Batasan

Kalian dapat juga menyisipkan file dengan cell komputasi di dalamnya. Contoh kita punya sisipan sebuah `.qmd` yang berisi *preprocessing data* yang kita ingin bagikan lintas dokumen:

````
---
title: "My Document"
---

{{< include _data.qmd >}}


Use the data...
````

dimana konten seharusnya berisi

````{.qmd filename='_data.qmd'}

Load the `sp500` from [`great_tables`](https://posit-dev.github.io/great-tables/)

```{python}
import great_tables as gt
from great_tables.data import sp500
sp500.head()
```
````

Beberapa hal penting yang harus diingat ketikan menyisipkan komputasi:

1. Semua komputasi share engine tunggal (e.g. knitr or jupyter)
2. Sisipan komputasi hanya bekerja di `.qmd` file (mereka tidak bekerja di `.ipynb` file notebooks)

Perhatikan bahwa kamu tidak dapat menyisipkan (`inclue`) dengan block komputasi di sendiri di dalamnya - pada contoh di atas. Code blocks executable harus di dalam dokumen yang disisipkan.

