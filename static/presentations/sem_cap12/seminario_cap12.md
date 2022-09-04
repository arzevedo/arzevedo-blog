<!DOCTYPE html>
<html lang="en"><head>
<script src="seminario_cap12_files/libs/clipboard/clipboard.min.js"></script>
<script src="seminario_cap12_files/libs/quarto-html/tabby.min.js"></script>
<script src="seminario_cap12_files/libs/quarto-html/popper.min.js"></script>
<script src="seminario_cap12_files/libs/quarto-html/tippy.umd.min.js"></script>
<link href="seminario_cap12_files/libs/quarto-html/tippy.css" rel="stylesheet">
<link href="seminario_cap12_files/libs/quarto-html/quarto-html.min.css" rel="stylesheet" data-mode="light">
<link href="seminario_cap12_files/libs/quarto-html/quarto-syntax-highlighting.css" rel="stylesheet" id="quarto-text-highlighting-styles"><meta charset="utf-8">
  <meta name="generator" content="quarto-1.0.36">

  <meta name="author" content="Arthur R. Azevedo ">
  <meta name="dcterms.date" content="2022-06-09">
  <title>Ponderação por probabilidade inversa  e  modelos estruturais marginais</title>
  <meta name="apple-mobile-web-app-capable" content="yes">
  <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, minimal-ui">
  <link rel="stylesheet" href="seminario_cap12_files/libs/revealjs/dist/reset.css">
  <link rel="stylesheet" href="seminario_cap12_files/libs/revealjs/dist/reveal.css">
  <style>
    code{white-space: pre-wrap;}
    span.smallcaps{font-variant: small-caps;}
    span.underline{text-decoration: underline;}
    div.column{display: inline-block; vertical-align: top; width: 50%;}
    div.hanging-indent{margin-left: 1.5em; text-indent: -1.5em;}
    ul.task-list{list-style: none;}
  </style>
  <link rel="stylesheet" href="seminario_cap12_files/libs/revealjs/dist/theme/quarto.css" id="theme">
  <link href="seminario_cap12_files/libs/revealjs/plugin/quarto-line-highlight/line-highlight.css" rel="stylesheet">
  <link href="seminario_cap12_files/libs/revealjs/plugin/reveal-menu/menu.css" rel="stylesheet">
  <link href="seminario_cap12_files/libs/revealjs/plugin/reveal-menu/quarto-menu.css" rel="stylesheet">
  <link href="seminario_cap12_files/libs/revealjs/plugin/reveal-chalkboard/font-awesome/css/all.css" rel="stylesheet">
  <link href="seminario_cap12_files/libs/revealjs/plugin/reveal-chalkboard/style.css" rel="stylesheet">
  <link href="seminario_cap12_files/libs/revealjs/plugin/quarto-support/footer.css" rel="stylesheet">
  <style type="text/css">

  .callout {
    margin-top: 1em;
    margin-bottom: 1em;  
    border-radius: .25rem;
  }

  .callout.callout-style-simple { 
    padding: 0em 0.5em;
    border-left: solid #acacac .3rem;
    border-right: solid 1px silver;
    border-top: solid 1px silver;
    border-bottom: solid 1px silver;
    display: flex;
  }

  .callout.callout-style-default {
    border-left: solid #acacac .3rem;
    border-right: solid 1px silver;
    border-top: solid 1px silver;
    border-bottom: solid 1px silver;
  }

  .callout .callout-body-container {
    flex-grow: 1;
  }

  .callout.callout-style-simple .callout-body {
    font-size: 1rem;
    font-weight: 400;
  }

  .callout.callout-style-default .callout-body {
    font-size: 0.9rem;
    font-weight: 400;
  }

  .callout.callout-captioned.callout-style-simple .callout-body {
    margin-top: 0.2em;
  }

  .callout:not(.callout-captioned) .callout-body {
      display: flex;
  }

  .callout:not(.no-icon).callout-captioned.callout-style-simple .callout-content {
    padding-left: 1.6em;
  }

  .callout.callout-captioned .callout-header {
    padding-top: 0.2em;
    margin-bottom: -0.2em;
  }

  .callout.callout-captioned .callout-caption  p {
    margin-top: 0.5em;
    margin-bottom: 0.5em;
  }
    
  .callout.callout-captioned.callout-style-simple .callout-content  p {
    margin-top: 0;
  }

  .callout.callout-captioned.callout-style-default .callout-content  p {
    margin-top: 0.7em;
  }

  .callout.callout-style-simple div.callout-caption {
    border-bottom: none;
    font-size: .9rem;
    font-weight: 600;
    opacity: 75%;
  }

  .callout.callout-style-default  div.callout-caption {
    border-bottom: none;
    font-weight: 600;
    opacity: 85%;
    font-size: 0.9rem;
    padding-left: 0.5em;
    padding-right: 0.5em;
  }

  .callout.callout-style-default div.callout-content {
    padding-left: 0.5em;
    padding-right: 0.5em;
  }

  .callout.callout-style-simple .callout-icon::before {
    height: 1rem;
    width: 1rem;
    display: inline-block;
    content: "";
    background-repeat: no-repeat;
    background-size: 1rem 1rem;
  }

  .callout.callout-style-default .callout-icon::before {
    height: 0.9rem;
    width: 0.9rem;
    display: inline-block;
    content: "";
    background-repeat: no-repeat;
    background-size: 0.9rem 0.9rem;
  }

  .callout-caption {
    display: flex
  }
    
  .callout-icon::before {
    margin-top: 1rem;
    padding-right: .5rem;
  }

  .callout.no-icon::before {
    display: none !important;
  }

  .callout.callout-captioned .callout-body > .callout-content > :last-child {
    margin-bottom: 0.5rem;
  }

  .callout.callout-captioned .callout-icon::before {
    margin-top: .5rem;
    padding-right: .5rem;
  }

  .callout:not(.callout-captioned) .callout-icon::before {
    margin-top: 1rem;
    padding-right: .5rem;
  }

  /* Callout Types */

  div.callout-note {
    border-left-color: #4582ec !important;
  }

  div.callout-note .callout-icon::before {
    background-image: url('data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAYAAABzenr0AAAAAXNSR0IArs4c6QAAAERlWElmTU0AKgAAAAgAAYdpAAQAAAABAAAAGgAAAAAAA6ABAAMAAAABAAEAAKACAAQAAAABAAAAIKADAAQAAAABAAAAIAAAAACshmLzAAAEU0lEQVRYCcVXTWhcVRQ+586kSUMMxkyaElstCto2SIhitS5Ek8xUKV2poatCcVHtUlFQk8mbaaziwpWgglJwVaquitBOfhQXFlqlzSJpFSpIYyXNjBNiTCck7x2/8/LeNDOZxDuEkgOXe++553zfefee+/OYLOXFk3+1LLrRdiO81yNqZ6K9cG0P3MeFaMIQjXssE8Z1JzLO9ls20MBZX7oG8w9GxB0goaPrW5aNMp1yOZIa7Wv6o2ykpLtmAPs/vrG14Z+6d4jpbSKuhdcSyq9wGMPXjonwmESXrriLzFGOdDBLB8Y6MNYBu0dRokSygMA/mrun8MGFN3behm6VVAwg4WR3i6FvYK1T7MHo9BK7ydH+1uurECoouk5MPRyVSBrBHMYwVobG2aOXM07sWrn5qgB60rc6mcwIDJtQrnrEr44kmy+UO9r0u9O5/YbkS9juQckLed3DyW2XV/qWBBB3ptvI8EUY3I9p/67OW+g967TNr3Sotn3IuVlfMLVnsBwH4fsnebJvyGm5GeIUA3jljERmrv49SizPYuq+z7c2H/jlGC+Ghhupn/hcapqmcudB9jwJ/3jvnvu6vu5lVzF1fXyZuZZ7U8nRmVzytvT+H3kilYvH09mLWrQdwFSsFEsxFVs5fK7A0g8gMZjbif4ACpKbjv7gNGaD8bUrlk8x+KRflttr22JEMRUbTUwwDQScyzPgedQHZT0xnx7ujw2jfVfExwYHwOsDTjLdJ2ebmeQIlJ7neo41s/DrsL3kl+W2lWvAga0tR3zueGr6GL78M3ifH0rGXrBC2aAR8uYcIA5gwV8zIE8onoh8u0Fca/ciF7j1uOzEnqcIm59sEXoGc0+z6+H45V1CvAvHcD7THztu669cnp+L0okAeIc6zjbM/24LgGM1gZk7jnRu1aQWoU9sfUOuhrmtaPIO3YY1KLLWZaEO5TKUbMY5zx8W9UJ6elpLwKXbsaZ4EFl7B4bMtDv0iRipKoDQT2sNQI9b1utXFdYisi+wzZ/ri/1m7QfDgEuvgUUEIJPq3DhX/5DWNqIXDOweC2wvIR90Oq3lDpdMIgD2r0dXvGdsEW5H6x6HLRJYU7C69VefO1x8Gde1ZFSJLfWS1jbCnhtOPxmpfv2LXOA2Xk2tvnwKKPFuZ/oRmwBwqRQDcKNeVQkYcOjtWVBuM/JuYw5b6isojIkYxyYAFn5K7ZBF10fea52y8QltAg6jnMqNHFBmGkQ1j+U43HMi2xMar1Nv0zGsf1s8nUsmUtPOOrbFIR8bHFDMB5zL13Gmr/kGlCkUzedTzzmzsaJXhYawnA3UmARpiYj5ooJZiUoxFRtK3X6pgNPv+IZVPcnwbOl6f+aBaO1CNvPW9n9LmCp01nuSaTRF2YxHqZ8DYQT6WsXT+RD6eUztwYLZ8rM+rcPxamv1VQzFUkzFXvkiVrySGQgJNvXHJAxiU3/NwiC03rSf05VBaPtu/Z7/B8Yn/w7eguloAAAAAElFTkSuQmCC');
  }

  div.callout-note.callout-style-default .callout-caption {
    background-color: #dae6fb
  }

  div.callout-important {
    border-left-color: #d9534f !important;
  }

  div.callout-important .callout-icon::before {
    background-image: url('data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAYAAABzenr0AAAAAXNSR0IArs4c6QAAAERlWElmTU0AKgAAAAgAAYdpAAQAAAABAAAAGgAAAAAAA6ABAAMAAAABAAEAAKACAAQAAAABAAAAIKADAAQAAAABAAAAIAAAAACshmLzAAAEKklEQVRYCcVXTWhcVRS+575MJym48A+hSRFr00ySRQhURRfd2HYjk2SSTokuBCkU2o0LoSKKraKIBTcuFCoidGFD08nkBzdREbpQ1EDNIv8qSGMFUboImMSZd4/f9zJv8ibJMC8xJQfO3HPPPef7zrvvvnvviIkpC9nsw0UttFunbUhpFzFtarSd6WJkStVMw5xyVqYTvkwfzuf/5FgtkVoB0729j1rjXwThS7Vio+Mo6DNnvLfahoZ+i/o32lULuJ3NNiz7q6+pyAUkJaFF6JwaM2lUJlV0MlnQn5aTRbEu0SEqHUa0A4AdiGuB1kFXRfVyg5d87+Dg4DL6m2TLAub60ilj7A1Ec4odSAc8X95sHh7+ZRPCFo6Fnp7HfU/fBng/hi10CjCnWnJjsxvDNxWw0NfV6Rv5GgP3I3jGWXumdTD/3cbEOP2ZbOZp69yniG3FQ9z1jD7bnBu9Fc2tKGC2q+uAJOQHBDRiZX1x36o7fWBs7J9ownbtO+n0/qWkvW7UPIfc37WgT6ZGR++EOJyeQDSb9UB+DZ1G6DdLDzyS+b/kBCYGsYgJbSQHuThGKRcw5xdeQf8YdNHsc6ePXrlSYMBuSIAFTGAtQo+VuALo4BX83N190NWZWbynBjhOHsmNfFWLeL6v+ynsA58zDvvAC8j5PkbOcXCMg2PZFk3q8MjI7WAG/Dp9AwP7jdGBOOQkAvlFUB+irtm16I1Zw9YBcpGTGXYmk3kQIC/Cds55l+iMI3jqhjAuaoe+am2Jw5GT3Nbz3CkE12NavmzN5+erJW7046n/CH1RO/RVa8lBLozXk9uqykkGAyRXLWlLv5jyp4RFsG5vGVzpDLnIjTWgnRy2Rr+tDKvRc7Y8AyZq10jj8DqXdnIRNtFZb+t/ZRtXcDiVnzpqx8mPcDWxgARUqx0W1QB9MeUZiNrV4qP+Ehc+BpNgATsTX8ozYKL2NtFYAHc84fG7ndxUPr+AR/iQSns7uSUufAymwDOb2+NjK27lEFocm/EE2WpyIy/Hi66MWuMKJn8RvxIcj87IM5Vh9663ziW36kR0HNenXuxmfaD8JC7tfKbrhFr7LiZCrMjrzTeGx+PmkosrkNzW94ObzwocJ7A1HokLolY+AvkTiD/q1H0cN48c5EL8Crkttsa/AXQVDmutfyku0E7jShx49XqV3MFK8IryDhYVbj7Sj2P2eBxwcXoe8T8idsKKPRcnZw1b+slFTubwUwhktrfnAt7J++jwQtLZcm3sr9LQrjRzz6cfMv9aLvgmnAGvpoaGLxM4mAEaLV7iAzQ3oU0IvD5x9ix3yF2RAAuYAOO2f7PEFWCXZ4C9Pb2UsgDeVnFSpbFK7/IWu7TPTvBqzbGdCHOJQSxiEjt6IyZmxQyEJHv6xyQsYk//moVFsN2zP6fRImjfq7/n/wFDguUQFNEwugAAAABJRU5ErkJggg==');
  }

  div.callout-important.callout-style-default .callout-caption {
    background-color: #f7dddc
  }

  div.callout-warning {
    border-left-color: #f0ad4e !important;
  }

  div.callout-warning .callout-icon::before {
    background-image: url('data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAYAAABzenr0AAAAAXNSR0IArs4c6QAAAERlWElmTU0AKgAAAAgAAYdpAAQAAAABAAAAGgAAAAAAA6ABAAMAAAABAAEAAKACAAQAAAABAAAAIKADAAQAAAABAAAAIAAAAACshmLzAAAETklEQVRYCeVWW2gcVRg+58yaTUnizqbipZeX4uWhBEniBaoUX1Ioze52t7sRq6APio9V9MEaoWlVsFasRq0gltaAPuxms8lu0gcviE/FFOstVbSIxgcv6SU7EZqmdc7v9+9mJtNks51NTUH84ed889/PP+cmxP+d5FIbMJmNbpREu4WUkiTtCicKny0l1pIKmBzovF2S+hIJHX8iEu3hZJ5lNZGqyRrGSIQpq15AzF28jgpeY6yk6GVdrfFqdrD6Iw+QlB8g0YS2g7dyQmXM/IDhBhT0UCiRf59lfqmmDvzRt6kByV/m4JjtzuaujMUM2c5Z2d6JdKrRb3K2q6mA+oYVz8JnDdKPmmNthzkAk/lN63sYPgevrguc72aZX/L9C6x09GYyxBgCX4NlvyGUHOKELlm5rXeR1kchuChJt4SSwyddZRXgvwMGvYo4QSlk3/zkHD8UHxwVJA6zjZZqP8v8kK8OWLnIZtLyCAJagYC4rTGW/9Pqj92N/c+LUaAj27movwbi19tk/whRCIE7Q9vyI6yvRpftAKVTdUjOW40X3h5OXsKCdmFcx0xlLJoSuQngnrJe7Kcjm4OMq9FlC7CMmScQANuNvjfP3PjGXDBaUQmbp296S5L4DrpbrHN1T87ZVEZVCzg1FF0Ft+dKrlLukI+/c9ENo+TvlTDbYFvuKPtQ9+l052rXrgKoWkDAFnvh0wTOmYn8R5f4k/jN/fZiCM1tQx9jQQ4ANhqG4hiL0qIFTGViG9DKB7GYzgubnpofgYRwO+DFjh0Zin2m4b/97EDkXkc+f6xYAPX0KK2I/7fUQuwzuwo/L3AkcjugPNixC8cHf0FyPjWlItmLxWw4Ou9YsQCr5fijMGoD/zpdRy95HRysyXA74MWOnscpO4j2y3HAVisw85hX5+AFBRSHt4ShfLFkIMXTqyKFc46xdzQM6XbAi702a7sy04J0+feReMFKp5q9esYLCqAZYw/k14E/xcLLsFElaornTuJB0svMuJINy8xkIYuL+xPAlWRceH6+HX7THJ0djLUom46zREu7tTkxwmf/FdOZ/sh6Q8qvEAiHpm4PJ4a/doJe0gH1t+aHRgCzOvBvJedEK5OFE5jpm4AGP2a8Dxe3gGJ/pAutug9Gp6he92CsSsWBaEcxGx0FHytmIpuqGkOpldqNYQK8cSoXvd+xLxXADw0kf6UkJNFtdo5MOgaLjiQOQHcn+A6h5NuL2s0qsC2LOM75PcF3yr5STuBSAcGG+meA14K/CI21HcS4LBT6tv0QAh8Dr5l93AhZzG5ZJ4VxAqdZUEl9z7WJ4aN+svMvwHHL21UKTd1mqvChH7/Za5xzXBBKrUcB0TQ+Ulgkfbi/H/YT5EptrGzsEK7tR1B7ln9BBwckYfMiuSqklSznIuoIIOM42MQO+QnduCoFCI0bpkzjCjddHPN/F+2Yu+sd9bKNpVwHhbS3LluK/0zgfwD0xYI5dXuzlQAAAABJRU5ErkJggg==');
  }

  div.callout-warning.callout-style-default .callout-caption {
    background-color: #fcefdc
  }

  div.callout-tip {
    border-left-color: #02b875 !important;
  }

  div.callout-tip .callout-icon::before {
    background-image: url('data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAYAAABzenr0AAAAAXNSR0IArs4c6QAAAERlWElmTU0AKgAAAAgAAYdpAAQAAAABAAAAGgAAAAAAA6ABAAMAAAABAAEAAKACAAQAAAABAAAAIKADAAQAAAABAAAAIAAAAACshmLzAAADr0lEQVRYCe1XTWgTQRj9ZjZV8a9SPIkKgj8I1bMHsUWrqYLVg4Ue6v9BwZOxSYsIerFao7UiUryIqJcqgtpimhbBXoSCVxUFe9CTiogUrUp2Pt+3aUI2u5vdNh4dmMzOzHvvezuz8xNFM0mjnbXaNu1MvFWRXkXEyE6aYOYJpdW4IXuA4r0fo8qqSMDBU0v1HJUgVieAXxzCsdE/YJTdFcVIZQNMyhruOMJKXYFoLfIfIvVIMWdsrd+Rpd86ZmyzzjJmLStqRn0v8lzkb4rVIXvnpScOJuAn2ACC65FkPzEdEy4TPWRLJ2h7z4cArXzzaOdKlbOvKKX25Wl00jSnrwVxAg3o4dRxhO13RBSdNvH0xSARv3adTXbBdTf64IWO2vH0LT+cv4GR1DJt+DUItaQogeBX/chhbTBxEiZ6gftlDNXTrvT7co4ub5A6gp9HIcHvzTa46OS5fBeP87Qm0fQkr4FsYgVQ7Qg+ZayaDg9jhg1GkWj8RG6lkeSacrrHgDaxdoBiZPg+NXV/KifMuB6//JmYH4CntVEHy/keA6x4h4CU5oFy8GzrBS18cLJMXcljAKB6INjWsRcuZBWVaS3GDrqB7rdapVIeA+isQ57Eev9eCqzqOa81CY05VLd6SamW2wA2H3SiTbnbSxmzfp7WtKZkqy4mdyAlGx7ennghYf8voqp9cLSgKdqNfa6RdRsAAkPwRuJZNbpByn+RrJi1RXTwdi8RQF6ymDwGMAtZ6TVE+4uoKh+MYkcLsT0Hk8eAienbiGdjJHZTpmNjlbFJNKDVAp2fJlYju6IreQxQ08UJDNYdoLSl6AadO+fFuCQqVMB1NJwPm69T04Wv5WhfcWyfXQB+wXRs1pt+nCknRa0LVzSA/2B+a9+zQJadb7IyyV24YAxKp2Jqs3emZTuNnKxsah+uabKbMk7CbTgJx/zIgQYErIeTKRQ9yD9wxVof5YolPHqaWo7TD6tJlh7jQnK5z2n3+fGdggIOx2kaa2YI9QWarc5Ce1ipNWMKeSG4DysFF52KBmTNMmn5HqCFkwy34rDg05gDwgH3bBi+sgFhN/e8QvRn8kbamCOhgrZ9GJhFDgfcMHzFb6BAtjKpFhzTjwv1KCVuxHvCbsSiEz4CANnj84cwHdFXAbAOJ4LTSAawGWFn5tDhLMYz6nWeU2wJfIhmIJBefcd/A5FWQWGgrWzyORZ3Q6HuV+Jf0Bj+BTX69fm1zWgK7By1YTXchFDORywnfQ7GpzOo6S+qECrsx2ifVQAAAABJRU5ErkJggg==');
  }

  div.callout-tip.callout-style-default .callout-caption {
    background-color: #ccf1e3
  }

  div.callout-caution {
    border-left-color: #fd7e14 !important;
  }

  div.callout-caution .callout-icon::before {
    background-image: url('data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAYAAABzenr0AAAAAXNSR0IArs4c6QAAAERlWElmTU0AKgAAAAgAAYdpAAQAAAABAAAAGgAAAAAAA6ABAAMAAAABAAEAAKACAAQAAAABAAAAIKADAAQAAAABAAAAIAAAAACshmLzAAACV0lEQVRYCdVWzWoUQRCuqp2ICBLJXgITZL1EfQDBW/bkzUMUD7klD+ATSHBEfAIfQO+iXsWDxJsHL96EHAwhgzlkg8nBg25XWb0zIb0zs9muYYWkoKeru+vn664fBqElyZNuyh167NXJ8Ut8McjbmEraKHkd7uAnAFku+VWdb3reSmRV8PKSLfZ0Gjn3a6Xlcq9YGb6tADjn+lUfTXtVmaZ1KwBIvFI11rRXlWlatwIAAv2asaa9mlB9wwygiDX26qaw1yYPzFXg2N1GgG0FMF8Oj+VIx7E/03lHx8UhvYyNZLN7BwSPgekXXLribw7w5/c8EF+DBK5idvDVYtEEwMeYefjjLAdEyQ3M9nfOkgnPTEkYU+sxMq0BxNR6jExrAI31H1rzvLEfRIdgcv1XEdj6QTQAS2wtstEALLG1yEZ3QhH6oDX7ExBSFEkFINXH98NTrme5IOaaA7kIfiu2L8A3qhH9zRbukdCqdsA98TdElyeMe5BI8Rs2xHRIsoTSSVFfCFCWGPn9XHb4cdobRIWABNf0add9jakDjQJpJ1bTXOJXnnRXHRf+dNL1ZV1MBRCXhMbaHqGI1JkKIL7+i8uffuP6wVQAzO7+qVEbF6NbS0LJureYcWXUUhH66nLR5rYmva+2tjRFtojkM2aD76HEGAD3tPtKM309FJg5j/K682ywcWJ3PASCcycH/22u+Bh7Aa0ehM2Fu4z0SAE81HF9RkB21c5bEn4Dzw+/qNOyXr3DCTQDMBOdhi4nAgiFDGCinIa2owCEChUwD8qzd03PG+qdW/4fDzjUMcE1ZpIAAAAASUVORK5CYII=');
  }

  div.callout-caution.callout-style-default .callout-caption {
    background-color: #ffe5d0
  }

  </style>
  <style type="text/css">
    .reveal div.sourceCode {
      margin: 0;
      overflow: auto;
    }
    .reveal div.hanging-indent {
      margin-left: 1em;
      text-indent: -1em;
    }
    .reveal .slide:not(.center) {
      height: 100%;
    }
    .reveal .slide.scrollable {
      overflow-y: auto;
    }
    .reveal .footnotes {
      height: 100%;
      overflow-y: auto;
    }
    .reveal .slide .absolute {
      position: absolute;
      display: block;
    }
    .reveal .footnotes ol {
      counter-reset: ol;
      list-style-type: none; 
      margin-left: 0;
    }
    .reveal .footnotes ol li:before {
      counter-increment: ol;
      content: counter(ol) ". "; 
    }
    .reveal .footnotes ol li > p:first-child {
      display: inline-block;
    }
    .reveal .slide ul,
    .reveal .slide ol {
      margin-bottom: 0.5em;
    }
    .reveal .slide ul li,
    .reveal .slide ol li {
      margin-top: 0.4em;
      margin-bottom: 0.2em;
    }
    .reveal .slide ul[role="tablist"] li {
      margin-bottom: 0;
    }
    .reveal .slide ul li > *:first-child,
    .reveal .slide ol li > *:first-child {
      margin-block-start: 0;
    }
    .reveal .slide ul li > *:last-child,
    .reveal .slide ol li > *:last-child {
      margin-block-end: 0;
    }
    .reveal .slide .columns:nth-child(3) {
      margin-block-start: 0.8em;
    }
    .reveal blockquote {
      box-shadow: none;
    }
    .reveal .tippy-content>* {
      margin-top: 0.2em;
      margin-bottom: 0.7em;
    }
    .reveal .tippy-content>*:last-child {
      margin-bottom: 0.2em;
    }
    .reveal .slide > img.stretch.quarto-figure-center,
    .reveal .slide > img.r-stretch.quarto-figure-center {
      display: block;
      margin-left: auto;
      margin-right: auto; 
    }
    .reveal .slide > img.stretch.quarto-figure-left,
    .reveal .slide > img.r-stretch.quarto-figure-left  {
      display: block;
      margin-left: 0;
      margin-right: auto; 
    }
    .reveal .slide > img.stretch.quarto-figure-right,
    .reveal .slide > img.r-stretch.quarto-figure-right  {
      display: block;
      margin-left: auto;
      margin-right: 0; 
    }
  </style>
</head>
<body class="quarto-light">
  <div class="reveal">
    <div class="slides">

<section id="title-slide" class="center">
  <h1 class="title">Ponderação por probabilidade inversa <br>e<br> modelos estruturais marginais</h1>
  <p class="author">Arthur R. Azevedo<br></p>
  <p class="date">06/09/22</p>
</section>

<section id="uma-revisão-do-capítulo-12-do-livro-causal-inference-what-if-por-miguel-hernán" class="title-slide slide level1 center">
<h1>Uma revisão do capítulo 12 do livro <em>Causal Inference: What If</em> por Miguel Hernán</h1>

</section>

<section>
<section id="a-pergunta-causal" class="title-slide slide level1 center">
<h1>A pergunta causal</h1>

</section>
<section id="a-pergunta-causal---12.1" class="slide level2">
<h2>A pergunta causal - 12.1</h2>
<ul>
<li>O exemplo do capítulo é sobre o ganho de peso em Kg em pessoas que pararam de fumar.</li>
<li>Queremos estimar o efeito causal médio.</li>
</ul>
<p>Seja <span class="math inline">\(A = 1\)</span> se o indivíduo parar de fumar. Definimos o efeito causal médio (ATE) como:</p>
<p><span class="math display">\[
\begin{equation}
\tag{*}
E[Y^{a = 1}] - E[Y^{a = 0}]
\end{equation}
\]</span></p>
<ul>
<li>Precisamos lidar com os confundidores como por exemplo a idade, pessoas mais velhas pararam mais de fumar do as mais novas nesse estudo (<em>surrogate effect</em>).</li>
</ul>
</section>
<section id="a-pergunta-causal-1" class="slide level2">
<h2>A pergunta causal</h2>
<p>Por isso,</p>
<p><span class="math display">\[\hat E[Y|A=1] - \hat E[Y|A=0]\]</span></p>
<p>é uma estimativa viesada de <span class="math inline">\((*)\)</span></p>
</section></section>
<section>
<section id="estimando-os-pesos-da-probabilidade-inversa" class="title-slide slide level1 center">
<h1>Estimando os pesos da probabilidade inversa</h1>

</section>
<section id="estimando-os-pesos-da-probabilidade-inversa---12.2" class="slide level2">
<h2>Estimando os pesos da probabilidade inversa - 12.2</h2>
<ul>
<li><p>A ponderação por probabilidade inversa (IPw) cria uma pseudo população tal que remove o efeito dos confundidores no tratamento <span class="math inline">\(A\)</span>.</p></li>
<li><p>De forma a tornar <span class="math inline">\(A\)</span> e <span class="math inline">\(L\)</span> (conjunto de confundidores) independentes na pseudo população.</p></li>
<li><p>Isso ocorre porque estamos ponderando cada indivíduo pelo inverso da probabilidade dele receber o tratamento.</p></li>
</ul>
</section>
<section id="estimando-os-pesos-da-probabilidade-inversa---12.2-1" class="slide level2">
<h2>Estimando os pesos da probabilidade inversa - 12.2</h2>
<p>De forma que podemos escrever a média padronizada da pseudo população como</p>
<p><span class="math display">\[E_{\text{ps}}[Y|A=a] = \sum_l E[Y|A=a,L=l]P(L=l)\]</span></p>
<p>Onde, sob permutação condicional.</p>
<p><span class="math display">\[E[Y^a] = E_{ps}[Y|A=a]\]</span></p>
</section>
<section id="estimando-os-pesos-da-probabilidade-inversa---12.2-2" class="slide level2">
<h2>Estimando os pesos da probabilidade inversa - 12.2</h2>
<p>Definimos o peso <span class="math inline">\(W\)</span> como</p>
<p><span class="math display">\[W^A = \frac{1}{f(A|L)}\]</span></p>
<p>Onde, para tratamentos dicotômicos</p>
<p><span class="math display">\[
f(A|L) =
\begin{cases}
    P(A=1|L), &amp; \text{se tratado} \\
    P(A=0|L) = 1- P(A=1|L), &amp; \text{c.c.}
\end{cases}
\]</span></p>
<ul>
<li>Estimar <span class="math inline">\(W\)</span> como feito no Cap. 2 se torna inviável.</li>
<li><span class="math inline">\(P(A=1|L)\)</span> é o <strong>escore de propensão</strong></li>
</ul>
</section>
<section id="pausa-para-lembrar-do-objetivo" class="slide level2">
<h2>Pausa para lembrar do objetivo</h2>
<p>Nosso objetivo é chegar em</p>
<p><span class="math display">\[\hat E_{\text{ps}}[Y|A=1] - \hat E_\text{ps}[Y|A=0]\]</span></p>
<p>que é a estimativa para</p>
<p><span class="math display">\[E[Y|A=1]-E[Y|A=0] \]</span></p>
<p>onde, se não houver confundimento para o efeito do tratamento <span class="math inline">\(A\)</span> é uma estimativa não viesada para</p>
<p><span class="math display">\[E[Y^{a=1}]-E[Y^{a=0}]\]</span></p>
</section>
<section id="estimando-os-pesos-da-probabilidade-inversa---12.2-3" class="slide level2">
<h2>Estimando os pesos da probabilidade inversa - 12.2</h2>
<p>Podemos estimar <span class="math inline">\(W\)</span></p>
<p><span class="math display">\[ \hat W = \begin{cases} \frac{1}{\hat P(A=1|L)}, &amp; \text{se tratado} \\ \frac{1}{1- \hat P(A=1|L)}, &amp; \text{c.c.} \end{cases}\]</span></p>
<p>Usando regressão logística !</p>
<p>E enfim podemos estimar o efeito causal ao ajustar equações de estimação generalizadas (GEE) com o fator de ponderação o <span class="math inline">\(\hat W\)</span>, de forma que</p>
<p><span class="math display">\[E[Y|A]=\theta_0 + \theta_1 A \]</span></p>
</section></section>
<section>
<section id="probabilidade-inversa-ponderada-estabilizada" class="title-slide slide level1 center">
<h1>Probabilidade inversa ponderada estabilizada</h1>

</section>
<section id="probabilidade-inversa-ponderada-estabilizada-12.3" class="slide level2">
<h2>Probabilidade inversa ponderada estabilizada 12.3</h2>
<p>Antes a IPw era definida com probabilidades iguais para todas as unidades.</p>
<p>Nessa seção exploramos a ponderação de forma a estabelecer diferentes probabilidades para cada unidade em receber o tratamento (<strong>sem depender de <span class="math inline">\(L\)</span></strong>).</p>
</section>
<section id="probabilidade-inversa-ponderada-estabilizada-12.3-1" class="slide level2">
<h2>Probabilidade inversa ponderada estabilizada 12.3</h2>
<p>É comum determinar a probabilidade de seleção para tratamento na pseudo população igual a proporção de indivíduos tratados na amostra. De forma que o IPw seja tal que</p>
<p><span class="math display">\[\text{IPw}^I = \begin{cases} \frac{P(A=1)}{f(A|L)}, &amp; \text{se tratado} \\ \frac{P(A=0)}{f(A|L)}, &amp; \text{c.c.} \end{cases} \\ = \frac{f(A)}{f(A|L)} \;\;\;\;\;\;\;\;\;\;\;\;\]</span></p>
</section>
<section id="probabilidade-inversa-ponderada-estabilizada-12.3-2" class="slide level2">
<h2>Probabilidade inversa ponderada estabilizada 12.3</h2>
<p>Onde <span class="math inline">\(f(A)\)</span> é chamado de fator estabilizador e é responsávelpor estreitar o alcance dos pesos padronizados:</p>
<p><span class="math display">\[\text{SW}^A = \frac{f(A)}{f(A|L)}\]</span></p>
<ul>
<li>Esperamos que a média do SW seja 1</li>
</ul>
<p>Isso ocorre porque o tamanho da pseudo população é igual à população de estudo.</p>
</section>
<section id="probabilidade-inversa-ponderada-estabilizada-12.3-3" class="slide level2">
<h2>Probabilidade inversa ponderada estabilizada 12.3</h2>
<p>Para estimar o SW:</p>
<ul>
<li>O denominador é estimado da mesma forma que em 12.2</li>
<li>O numerador é estimado com uma regressão log desconsiderando os confundidores (<span class="math inline">\(L\)</span>).</li>
</ul>
<p><span class="math display">\[ \hat{SW} = \begin{cases} \frac{\hat P(A=1)}{\hat P(A=1|L)}, &amp; \text{se tratado} \\ \frac{1-\hat P(A=1)}{1-\hat P(A=1|L)}, &amp; \text{c.c.} \end{cases}\]</span></p>
</section>
<section id="probabilidade-inversa-ponderada-estabilizada-12.3-4" class="slide level2">
<h2>Probabilidade inversa ponderada estabilizada 12.3</h2>
<ul>
<li><p>O efeito causal também é estimado com a mesma GEE de 12.2</p></li>
<li><p>A vantagem do SW no exemplo do capítulo foi um intervalo de confiança para o efeito causal <span class="math inline">\(\theta_1\)</span> menor.</p></li>
<li><p>Segundo Hernán em problemas com a variação no tempo ou tratamentos contínuos SW torna-se mais efetivo.</p></li>
</ul>
</section></section>
<section>
<section id="verificando-a-positividade" class="title-slide slide level1 center">
<h1>Verificando a positividade</h1>

</section>
<section id="verificando-a-positividade---t.p.-12.1" class="slide level2">
<h2>Verificando a positividade - T.P. 12.1</h2>
<ul>
<li>No exemplo do Cap. existem 4 mulheres de 66 anos (no baseline) e nenhuma delas parou de fumar.</li>
</ul>
<p>Isso viola uma das condições para usarmos o IPw. Existem 2 maneiras da positividade ser violada.</p>
<ul>
<li><p>Estrutural: Alguns valores não são possíveis de serem tratados.</p></li>
<li><p>Aleatório: Amostras são finitas, se estratificamos por muitos confundidores alguns 0s podem surgir.</p></li>
</ul>
</section></section>
<section>
<section id="modelos-estruturais-marginais" class="title-slide slide level1 center">
<h1>Modelos estruturais marginais</h1>

</section>
<section id="modelos-estruturais-marginais-12.4" class="slide level2">
<h2>Modelos estruturais marginais 12.4</h2>
<p>Agora vamos considerar nosso tratamento contínuo, no exemplo do livro é a intensidade de fumo, medido pela quantidade de cigarros consumidos.</p>
<p>Onde podemos ter interesse em estimar a diferença média na mudança de peso de acordo com a intensidade de cigarros consumidos.</p>
<p>Para este método, consideramos a própria resposta contrafactual como a variável resposta.</p>
<p><span class="math display">\[E[Y^a] = \beta_0 + \beta_1 a\]</span></p>
</section>
<section id="modelos-estruturais-marginais-12.4-1" class="slide level2">
<h2>Modelos estruturais marginais 12.4 ()</h2>
<p>Se considerarmos <span class="math inline">\(A\)</span> como dicotômico como anteriormente, <span class="math inline">\(\beta_1\)</span> pode ser escrito como</p>
<p><span class="math display">\[\beta_1 = E[Y^{a=1}] - E[Y^{a=0}]\]</span></p>
<p>devido a</p>
<p><span class="math display">\[\beta_0 = E[Y^{a}], \text{ sob a=0 e }\\ \beta_0 +\beta_1 = E[Y^{a}], \text{ sob a=1 e }\]</span></p>
</section>
<section id="modelos-estruturais-marginais-12.4-2" class="slide level2">
<h2>Modelos estruturais marginais 12.4</h2>
<p>Mais uma vez, queremos estimar a diferença média na mudança de peso de acordo com os diferentes tratamentos (quantidade de cigarro consumido)</p>
<p><span class="math display">\[E[Y^a] - E[Y^{a'}]\]</span></p>
<p>Para quaisquer valores de <span class="math inline">\(a\)</span> e <span class="math inline">\(a'\)</span></p>
<p>O modelo proposto no cap. foi</p>
<p><span class="math display">\[E[Y^a] = \beta_0 + \beta_1 a + \beta_2a^2\]</span></p>
<p>Onde <span class="math inline">\(E[Y^{a=0}] = \beta_0\)</span> representa a média de peso ganho sem mudança alguma na intensidade de fumar.</p>
</section>
<section id="modelos-estruturais-marginais-12.4-3" class="slide level2">
<h2>Modelos estruturais marginais 12.4</h2>
<p>Para estimar o SW<span class="math inline">\(^A\)</span> para um tratamento contínuo preciso estimar o denominador <span class="math inline">\(f(A|L)\)</span> que agora torna-se uma f.d.p.</p>
<p>No exemplo, Hernán assume que <span class="math display">\[f(A|L) \sim\text{Normal}(\hat \phi, \sigma^2),\]</span> onde <span class="math inline">\(\hat \phi\)</span> é o valor predito pela regressão linear do modelo incluindo confundidores e intensidade<span class="math inline">\(^2\)</span>.</p>
<p>E <span class="math inline">\(\sigma^2\)</span> é a variância do modelo linear.</p>
</section>
<section id="modelos-estruturais-marginais-12.4-4" class="slide level2">
<h2>Modelos estruturais marginais 12.4</h2>
<blockquote>
<p>One should be careful when using IPw for continuous treatments.</p>
</blockquote>
<p>Também é possível usar modelos estruturais marginais (MSM) para respostas binárias. Por exemplo, estudar o efeito causal em parar de fumar e o risco de morte até o ano X.</p>
<p>Esse modelo tem forma</p>
<p><span class="math display">\[\text{logit} P(D^a) = \alpha_0+\alpha_1 a\]</span></p>
<p>onde <span class="math inline">\(\exp(\alpha_1)\)</span> é o OR causal da morte de quem parou de fumar vs.&nbsp;quem não parou de fumar.</p>
</section></section>
<section>
<section id="modificação-de-efeito-e-msm" class="title-slide slide level1 center">
<h1>Modificação de efeito e MSM</h1>

</section>
<section id="modificação-de-efeito-e-msm-12.5" class="slide level2">
<h2>Modificação de efeito e MSM 12.5</h2>
<ul>
<li>Podemos adicionar covariáveis que não são confundidores mas que acreditamos que modifiquem o efeito do tratamento numa resposta.</li>
</ul>
<p>Por exemplo, sexo (<span class="math inline">\(V\)</span>) altera o efeito de parar de fumar no ganho de peso.</p>
<p><span class="math display">\[E[Y^a|V] = \beta_0 + \beta_1 a + \beta_2 V a + \beta_3 V\]</span></p>
</section>
<section id="modificação-de-efeito-e-msm-12.5-1" class="slide level2">
<h2>Modificação de efeito e MSM 12.5</h2>
<p>Podemos estimar os parâmetros ajustando uma regressão linear</p>
<p><span class="math display">\[E[Y|A,V] = \theta_0 + \theta_1 A + \theta_2 VA + \theta_3 V\]</span></p>
<p>por Minimos quadrados ponderados via SW<span class="math inline">\(^A\)</span>.</p>
<p>A diferença é que no numerador ajustamos a regressão logística usando a covariável <span class="math inline">\(V\)</span>.</p>
</section></section>
<section>
<section id="censura-e-dados-faltantes" class="title-slide slide level1 center">
<h1>Censura e dados faltantes</h1>

</section>
<section id="censura-e-dados-faltantes-12.6" class="slide level2">
<h2>Censura e dados faltantes 12.6</h2>
<ul>
<li><p>Selecionar apenas indivíduos que não tem informação faltante na resposta pode introduzir <strong>viés de seleção</strong>.</p></li>
<li><p>No proprio exemplo do cap. existe censura de 63 pessoas, as quais não apresentam informação do peso no ano 1982.</p></li>
</ul>
<p>Vamos formalizar para levar a censura em conta</p>
<p><span class="math display">\[ C = \begin{cases} 1, &amp; \text{se o peso não foi aferido} \\ 0, &amp; \text{c.c.} \end{cases}\]</span></p>
</section>
<section id="censura-e-dados-faltantes-12.6-1" class="slide level2">
<h2>Censura e dados faltantes 12.6</h2>
<p>Construímos um modelo restrito a indivíduos com <span class="math inline">\(C=0\)</span></p>
<p><span class="math display">\[E[Y|A,C=0] = \theta_0 +\theta_1A\]</span></p>
<p>Mas isso pode levar ao viés de seleção, mudamos nossos objetivos de estimação de forma que o contrafactual comporte a censura.</p>
<p>Em outras palavras, modelamos o que aconteceria <em>se</em> tivéssemos toda informação</p>
<p><span class="math display">\[E[Y^{a,c}]\]</span></p>
</section>
<section id="censura-e-dados-faltantes-12.6-2" class="slide level2">
<h2>Censura e dados faltantes 12.6</h2>
<p>Para isso, estimamos o ATE</p>
<p><span class="math display">\[E[Y^{a=1,\;c=0}] - E[Y^{a=0,\;c=0}]\]</span></p>
<div class="columns">
<div class="column" style="width:50%;">
<p>Média de peso ganho <strong>se</strong> todos parassem de fumar <strong>e</strong> ninguem tivesse sido censurado</p>
</div><div class="column" style="width:50%;">
<p>Média de peso ganho <strong>se</strong> ninguem parasse de fumar <strong>e</strong> ninguem tivesse sido censurado</p>
</div>
</div>
</section>
<section id="censura-e-dados-faltantes-12.6-3" class="slide level2">
<h2>Censura e dados faltantes 12.6</h2>
<p>Para calcular os pesos IP (W<span class="math inline">\(^{A,C}\)</span>) é necessário ajustar por confundidores e pelo viés de seleção;</p>
<ul>
<li>Sob permutação para o tratamento conjunto (A,C) condicionado a L</li>
</ul>
<p><span class="math display">\[Y^{a,c=0} \ind (A,C) |L\]</span></p>
<ul>
<li><p>Positividade</p></li>
<li><p>Consistência</p></li>
</ul>
</section>
<section id="censura-e-dados-faltantes-12.6-4" class="slide level2">
<h2>Censura e dados faltantes 12.6</h2>
<p>Escrevemos o IPw como</p>
<p><span class="math display">\[W^{A,C} = \frac{1}{f(A,C=0|L)}\]</span></p>
<p>onde <span class="math display">\[f(A,C=0|L) = f(A|L) P(C=0|L,A)\]</span></p>
<p>Podemos também, calcular o IP estabilizado</p>
<p><span class="math display">\[SW^{A,C} = SW^A SW^C\]</span></p>
</section>
<section id="censura-e-dados-faltantes-12.6-5" class="slide level2">
<h2>Censura e dados faltantes 12.6</h2>
<p>Onde SW<span class="math inline">\(^A\)</span> foi visto anteriormente e</p>
<p><span class="math display">\[SW^C = \frac{P(C=0|A)}{P(C=0|L,A)}\]</span></p>
<p>Que é responsávelpor criar uma pseudo população do mesmo tamanho da população original depois da censura.</p>
<p>u seja, o SW não elimina a censura, ele apenas faz com que a censura seja aleatória com respeito às covariáveis L (“remove” a seta de L para C).</p>
<p>Estimativas de <span class="math inline">\(P(C=0|L,A)\)</span> via regressão logística.</p>
</section></section>
<section>
<section id="mais-em-pesos-estabilizados" class="title-slide slide level1 center">
<h1>Mais em pesos estabilizados</h1>

</section>
<section id="mais-em-pesos-estabilizados---t.p.-12.2" class="slide level2">
<h2>Mais em pesos estabilizados - T.P. 12.2</h2>
<p>Pesos estabilizados <span class="math inline">\(SW^A = \frac{f(A)}{f(A|L)}\)</span> pertencem a uma classe maior de SW.</p>
<p><span class="math display">\[\frac{g(A)}{f(A|L)}\]</span></p>
<p>Onde <span class="math inline">\(g(A)\)</span> é qualquer função de A que não é função de L.</p>
<p>Pesos desse tipo são preferíveis em modelos estruturais marginais não saturados. Já que constroem estimadores mais eficientes.</p>
</section></section>
<section id="obrigado-pela-atenção" class="title-slide slide level1 center">
<h1>Obrigado pela atenção</h1>
<div class="footer footer-default">

</div>
</section>
    </div>
  </div>

  <script>window.backupDefine = window.define; window.define = undefined;</script>
  <script src="seminario_cap12_files/libs/revealjs/dist/reveal.js"></script>
  <!-- reveal.js plugins -->
  <script src="seminario_cap12_files/libs/revealjs/plugin/quarto-line-highlight/line-highlight.js"></script>
  <script src="seminario_cap12_files/libs/revealjs/plugin/pdf-export/pdfexport.js"></script>
  <script src="seminario_cap12_files/libs/revealjs/plugin/reveal-menu/menu.js"></script>
  <script src="seminario_cap12_files/libs/revealjs/plugin/reveal-menu/quarto-menu.js"></script>
  <script src="seminario_cap12_files/libs/revealjs/plugin/reveal-chalkboard/plugin.js"></script>
  <script src="seminario_cap12_files/libs/revealjs/plugin/quarto-support/support.js"></script>
  

  <script src="seminario_cap12_files/libs/revealjs/plugin/notes/notes.js"></script>
  <script src="seminario_cap12_files/libs/revealjs/plugin/search/search.js"></script>
  <script src="seminario_cap12_files/libs/revealjs/plugin/zoom/zoom.js"></script>
  <script src="seminario_cap12_files/libs/revealjs/plugin/math/math.js"></script>
  <script>window.define = window.backupDefine; window.backupDefine = undefined;</script>

  <script>

      // Full list of configuration options available at:
      // https://revealjs.com/config/
      Reveal.initialize({
'controlsAuto': true,
'previewLinksAuto': false,
'smaller': false,
'pdfSeparateFragments': false,
'autoAnimateEasing': "ease",
'autoAnimateDuration': 1,
'autoAnimateUnmatched': true,
'menu': {"side":"left","useTextContentForMissingTitles":true,"markers":false,"loadIcons":false,"custom":[{"title":"Tools","icon":"<i class=\"fas fa-gear\"></i>","content":"<ul class=\"slide-menu-items\">\n<li class=\"slide-tool-item active\" data-item=\"0\"><a href=\"#\" onclick=\"RevealMenuToolHandlers.fullscreen(event)\"><kbd>f</kbd> Fullscreen</a></li>\n<li class=\"slide-tool-item\" data-item=\"1\"><a href=\"#\" onclick=\"RevealMenuToolHandlers.speakerMode(event)\"><kbd>s</kbd> Speaker View</a></li>\n<li class=\"slide-tool-item\" data-item=\"2\"><a href=\"#\" onclick=\"RevealMenuToolHandlers.overview(event)\"><kbd>o</kbd> Slide Overview</a></li>\n<li class=\"slide-tool-item\" data-item=\"3\"><a href=\"#\" onclick=\"RevealMenuToolHandlers.overview(event)\"><kbd>e</kbd> PDF Export Mode</a></li>\n<li class=\"slide-tool-item\" data-item=\"4\"><a href=\"#\" onclick=\"RevealMenuToolHandlers.toggleChalkboard(event)\"><kbd>b</kbd> Toggle Chalkboard</a></li>\n<li class=\"slide-tool-item\" data-item=\"5\"><a href=\"#\" onclick=\"RevealMenuToolHandlers.toggleNotesCanvas(event)\"><kbd>c</kbd> Toggle Notes Canvas</a></li>\n<li class=\"slide-tool-item\" data-item=\"6\"><a href=\"#\" onclick=\"RevealMenuToolHandlers.downloadDrawings(event)\"><kbd>d</kbd> Download Drawings</a></li>\n<li class=\"slide-tool-item\" data-item=\"7\"><a href=\"#\" onclick=\"RevealMenuToolHandlers.keyboardHelp(event)\"><kbd>?</kbd> Keyboard Help</a></li>\n</ul>"}],"openButton":true},
'chalkboard': {"buttons":true},
'smaller': false,
 
        // Display controls in the bottom right corner
        controls: false,

        // Help the user learn the controls by providing hints, for example by
        // bouncing the down arrow when they first encounter a vertical slide
        controlsTutorial: false,

        // Determines where controls appear, "edges" or "bottom-right"
        controlsLayout: 'edges',

        // Visibility rule for backwards navigation arrows; "faded", "hidden"
        // or "visible"
        controlsBackArrows: 'faded',

        // Display a presentation progress bar
        progress: true,

        // Display the page number of the current slide
        slideNumber: false,

        // 'all', 'print', or 'speaker'
        showSlideNumber: 'all',

        // Add the current slide number to the URL hash so that reloading the
        // page/copying the URL will return you to the same slide
        hash: true,

        // Start with 1 for the hash rather than 0
        hashOneBasedIndex: false,

        // Flags if we should monitor the hash and change slides accordingly
        respondToHashChanges: true,

        // Push each slide change to the browser history
        history: true,

        // Enable keyboard shortcuts for navigation
        keyboard: true,

        // Enable the slide overview mode
        overview: true,

        // Disables the default reveal.js slide layout (scaling and centering)
        // so that you can use custom CSS layout
        disableLayout: false,

        // Vertical centering of slides
        center: false,

        // Enables touch navigation on devices with touch input
        touch: true,

        // Loop the presentation
        loop: false,

        // Change the presentation direction to be RTL
        rtl: false,

        // see https://revealjs.com/vertical-slides/#navigation-mode
        navigationMode: 'linear',

        // Randomizes the order of slides each time the presentation loads
        shuffle: false,

        // Turns fragments on and off globally
        fragments: true,

        // Flags whether to include the current fragment in the URL,
        // so that reloading brings you to the same fragment position
        fragmentInURL: false,

        // Flags if the presentation is running in an embedded mode,
        // i.e. contained within a limited portion of the screen
        embedded: false,

        // Flags if we should show a help overlay when the questionmark
        // key is pressed
        help: true,

        // Flags if it should be possible to pause the presentation (blackout)
        pause: true,

        // Flags if speaker notes should be visible to all viewers
        showNotes: false,

        // Global override for autoplaying embedded media (null/true/false)
        autoPlayMedia: null,

        // Global override for preloading lazy-loaded iframes (null/true/false)
        preloadIframes: null,

        // Number of milliseconds between automatically proceeding to the
        // next slide, disabled when set to 0, this value can be overwritten
        // by using a data-autoslide attribute on your slides
        autoSlide: 0,

        // Stop auto-sliding after user input
        autoSlideStoppable: true,

        // Use this method for navigation when auto-sliding
        autoSlideMethod: null,

        // Specify the average time in seconds that you think you will spend
        // presenting each slide. This is used to show a pacing timer in the
        // speaker view
        defaultTiming: null,

        // Enable slide navigation via mouse wheel
        mouseWheel: false,

        // The display mode that will be used to show slides
        display: 'block',

        // Hide cursor if inactive
        hideInactiveCursor: true,

        // Time before the cursor is hidden (in ms)
        hideCursorTime: 5000,

        // Opens links in an iframe preview overlay
        previewLinks: false,

        // Transition style (none/fade/slide/convex/concave/zoom)
        transition: 'none',

        // Transition speed (default/fast/slow)
        transitionSpeed: 'default',

        // Transition style for full page slide backgrounds
        // (none/fade/slide/convex/concave/zoom)
        backgroundTransition: 'none',

        // Number of slides away from the current that are visible
        viewDistance: 3,

        // Number of slides away from the current that are visible on mobile
        // devices. It is advisable to set this to a lower number than
        // viewDistance in order to save resources.
        mobileViewDistance: 2,

        // The "normal" size of the presentation, aspect ratio will be preserved
        // when the presentation is scaled to fit different resolutions. Can be
        // specified using percentage units.
        width: 1050,

        height: 700,

        // Factor of the display size that should remain empty around the content
        margin: 0.1,

        math: {
          mathjax: 'https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.0/MathJax.js',
          config: 'TeX-AMS_HTML-full',
          tex2jax: {
            inlineMath: [['\\(','\\)']],
            displayMath: [['\\[','\\]']],
            balanceBraces: true,
            processEscapes: false,
            processRefs: true,
            processEnvironments: true,
            preview: 'TeX',
            skipTags: ['script','noscript','style','textarea','pre','code'],
            ignoreClass: 'tex2jax_ignore',
            processClass: 'tex2jax_process'
          },
        },

        // reveal.js plugins
        plugins: [QuartoLineHighlight, PdfExport, RevealMenu, RevealChalkboard, QuartoSupport,

          RevealMath,
          RevealNotes,
          RevealSearch,
          RevealZoom
        ]
      });
    </script>
    <script id="quarto-html-after-body" type="application/javascript">
    window.document.addEventListener("DOMContentLoaded", function (event) {
      const toggleBodyColorMode = (bsSheetEl) => {
        const mode = bsSheetEl.getAttribute("data-mode");
        const bodyEl = window.document.querySelector("body");
        if (mode === "dark") {
          bodyEl.classList.add("quarto-dark");
          bodyEl.classList.remove("quarto-light");
        } else {
          bodyEl.classList.add("quarto-light");
          bodyEl.classList.remove("quarto-dark");
        }
      }
      const toggleBodyColorPrimary = () => {
        const bsSheetEl = window.document.querySelector("link#quarto-bootstrap");
        if (bsSheetEl) {
          toggleBodyColorMode(bsSheetEl);
        }
      }
      toggleBodyColorPrimary();  
      const tabsets =  window.document.querySelectorAll(".panel-tabset-tabby")
      tabsets.forEach(function(tabset) {
        const tabby = new Tabby('#' + tabset.id);
      });
      const clipboard = new window.ClipboardJS('.code-copy-button', {
        target: function(trigger) {
          return trigger.previousElementSibling;
        }
      });
      clipboard.on('success', function(e) {
        // button target
        const button = e.trigger;
        // don't keep focus
        button.blur();
        // flash "checked"
        button.classList.add('code-copy-button-checked');
        var currentTitle = button.getAttribute("title");
        button.setAttribute("title", "Copied!");
        setTimeout(function() {
          button.setAttribute("title", currentTitle);
          button.classList.remove('code-copy-button-checked');
        }, 1000);
        // clear code selection
        e.clearSelection();
      });
      function tippyHover(el, contentFn) {
        const config = {
          allowHTML: true,
          content: contentFn,
          maxWidth: 500,
          delay: 100,
          arrow: false,
          appendTo: function(el) {
              return el.closest('section.slide') || el.parentElement;
          },
          interactive: true,
          interactiveBorder: 10,
          theme: 'quarto-reveal',
          placement: 'bottom-start'
        };
          config['offset'] = [0,0];
          config['maxWidth'] = 700;
        window.tippy(el, config); 
      }
      const noterefs = window.document.querySelectorAll('a[role="doc-noteref"]');
      for (var i=0; i<noterefs.length; i++) {
        const ref = noterefs[i];
        tippyHover(ref, function() {
          let href = ref.getAttribute('href');
          try { href = new URL(href).hash; } catch {}
          const id = href.replace(/^#\/?/, "");
          const note = window.document.getElementById(id);
          return note.innerHTML;
        });
      }
      var bibliorefs = window.document.querySelectorAll('a[role="doc-biblioref"]');
      for (var i=0; i<bibliorefs.length; i++) {
        const ref = bibliorefs[i];
        const cites = ref.parentNode.getAttribute('data-cites').split(' ');
        tippyHover(ref, function() {
          var popup = window.document.createElement('div');
          cites.forEach(function(cite) {
            var citeDiv = window.document.createElement('div');
            citeDiv.classList.add('hanging-indent');
            citeDiv.classList.add('csl-entry');
            var biblioDiv = window.document.getElementById('ref-' + cite);
            if (biblioDiv) {
              citeDiv.innerHTML = biblioDiv.innerHTML;
            }
            popup.appendChild(citeDiv);
          });
          return popup.innerHTML;
        });
      }
    });
    </script>
    

</body></html>