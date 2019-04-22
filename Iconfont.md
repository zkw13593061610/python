## Iconfont

### 使用：

- 在线使用

  - 打开icon font官网，把他添加到自己的库中，然后生成代码，复制，并且link进去   给他起iconfont类名，然后应用

- 下载使用

  - ```py
    @font-face {font-family: "iconfont";
      src: url('iconfont.eot?t=1539658117484'); /* IE9*/
      src: url('iconfont.eot?t=1539658117484#iefix') format('embedded-opentype'), /* IE6-IE8 */
      url('data:application/x-font-woff;charset=utf-8;base64,d09GRgABAAAAAAQ0AAsAAAAABrQAAQAAAAAAAAAAAAAAAAAAAAAAAAAAAABHU1VCAAABCAAAADMAAABCsP6z7U9TLzIAAAE8AAAARAAAAFY8uEg0Y21hcAAAAYAAAABLAAABcOdqtnBnbHlmAAABzAAAAIYAAAC826zy6GhlYWQAAAJUAAAAKwAAADYS9SkHaGhlYQAAAoAAAAAcAAAAJAfeA4NobXR4AAACnAAAAAgAAAAICAAAAGxvY2EAAAKkAAAABgAAAAYAXgAAbWF4cAAAAqwAAAAgAAAAIAEZAEtuYW1lAAACzAAAAUUAAAJtPlT+fXBvc3QAAAQUAAAAIAAAADHN9dBweJxjYGRgYOBikGPQYWB0cfMJYeBgYGGAAJAMY05meiJQDMoDyrGAaQ4gZoOIAgCKIwNPAHicY2BkYWCcwMDKwMHUyXSGgYGhH0IzvmYwYuRgYGBiYGVmwAoC0lxTGByeOT1zYm7438AQw9zA0AAUZgTJAQDndQxneJxjYGBgZWBgYAZiHSBmYWBgDGFgZAABP6AoI1icmYELLM7CoARWwwISf+b0/z+MBPJZwCQDIxvDKOABkzJQHjisIJiBEQDKTgpxAHicY+BlAALmBmYgwcDOwM3AzyDMIM4gzSDPoMygzqDNYM1gx8BgrmxqbIqGGRUFFYWxiJubqCkrKrGJCoqIGSsamZkyqzJ/84UDxo//fBk3ZyIEDIR4/9rxCgnxMh3iFXr07yFTlq+2rxYQa/v+PcoU9HcfnOsFUgVRy5i38t9mBgBMYylGAAB4nGNgZGBgAOLZNW9E4/ltvjJwszCAwPXXRa3INAsDM4jiYGACUQAotQlMAHicY2BkYGBu+N/AEMPCAAJAkpEBFTABAEcIAmsEAAAABAAAAAAAAAAAXgAAAAEAAAACAD8ADQAAAAAAAgAAAAoACgAAAP8AAAAAAAB4nGWPTU7DMBCFX/oHpBKqqGCH5AViASj9EatuWFRq911036ZOmyqJI8et1ANwHo7ACTgC3IA78EgnmzaWx9+8eWNPANzgBx6O3y33kT1cMjtyDRe4F65TfxBukF+Em2jjVbhF/U3YxzOmwm10YXmD17hi9oR3YQ8dfAjXcI1P4Tr1L+EG+Vu4iTv8CrfQ8erCPuZeV7iNRy/2x1YvnF6p5UHFockikzm/gple75KFrdLqnGtbxCZTg6BfSVOdaVvdU+zXQ+ciFVmTqgmrOkmMyq3Z6tAFG+fyUa8XiR6EJuVYY/62xgKOcQWFJQ6MMUIYZIjK6Og7VWb0r7FDwl57Vj3N53RbFNT/c4UBAvTPXFO6stJ5Ok+BPV8bUnV0K27LnpQ0kV7NSRKyQl7WtlRC6gE2ZVeOEXpc0Yk/KGdI/wAJWm7IAAAAeJxjYGKAAC4G7ICJkYmRmYE9JT8vPaM0kYEBABRKAwM=') format('woff'),
      url('iconfont.ttf?t=1539658117484') format('truetype'), /* chrome, firefox, opera, Safari, Android, iOS 4.2+*/
      url('iconfont.svg?t=1539658117484#iconfont') format('svg'); /* iOS 4.1- */
    }    上面的东西是用来做兼容的，
    .iconfont {
      font-family:"iconfont" !important;
      font-size:16px;
      font-style:normal;
      -webkit-font-smoothing: antialiased;
      -moz-osx-font-smoothing: grayscale;
    }
    
    .icon-donghua:before { content: "\e642"; }
    
    ```

  - 

用  v-for   一般给key    加快运行i侠侣