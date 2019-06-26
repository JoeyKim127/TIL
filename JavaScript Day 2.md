## JavaScript Day 2

- for loop 연습



- Question 1

  : 10 ~ 25의 합

```html
<script>
    //Question 1
    // 10 ~ 25의 합

let sum1 = 0;
for (let i = 10; i<26; i++) {
    document.write(i,",");
    sum1 = sum1 + i;
}

document.write("<br>");
document.write(sum1,"<br>");
    
</script>
```



- Question 2

  : 10 13 16 ...100까지의 합

```html
<script></script>
let sum2 = 10;
    for (let a = 10; a < 101; a = a + 3) {
        document.write(a,",");
        sum2 += a;
    }

    document.write("<br>");
    document.write(sum2);
    document.write("<br>");
</script>                             
```



- Question 3

```html
<script>
    let num = 3;
let sum3 = 0;
for (let i = 1 ; i < 10; i++) {
    sum3 = num*i;
    document.write("<br>",num," x ",i, " = ", sum3,"<br>");
}

document.write("<br>");
document.write("<br>");
</script>
```



- Question 4

  :0단부터 구구단 표현

```html
<script>
for(let i=0; i<9; i++) {
document.write("<h1>")
    
document.write("<h1> ",i," 단 </h1>  <br>" )
document.write("<br>");

    for(let j=1; j<10; j++){

        document.write(i*j, "<br>" )
    }

    document.write("<br>");

}

</script>
```



- Question 5

  :직사각형 표현

```html
<script>
    let num4 = 10;

for(let i = 0; i<num4; i++) {

    for(let j = 0; j < num4; j++ ) {
        
        document.write('*');
    }
    document.write("<br>");
}

document.write("<br>");
document.write("<br>");
</script>
```



- Question 6

  :직각삼각형 표현하기

```html
<script>
    let num5 = 10;

for(let i = 0; i<num5; i++) {

    for(let j = 0; j < i+1; j++ ) {
        
        document.write('*');
    }
    document.write("<br>");
}

document.write("<br>");
document.write("<br>");

</script>
```



- Question 7

  : 피라미드 표현 - 삼각형3개 이용

```html
<script>
    let num6 = 10;

for(let i = 0; i < num6; i++) {

    for(let a= num6; a > i; a-- ){

        document.write("&nbsp")
    }
    
    for(let j= 0; j< i+1; j++) {

        document.write('*');
    }

 for(let b=0; b < i; b++) {

    document.write("*");
 }
    document.write("<br>");
}
</script>
```



- Question 8

  :피라미드 표현 - 삼각형2개 이용

```html
<script>
    let num7 = 10;

for(let i = 0; i <11; i++){

    for(let j=9; j>i; j--) {
        
        document.write("&nbsp");
    }

    for(let a=0; a < i*2+1 ;a++) {

        document.write("*");
    }
    document.write("<br>");
}
</script>
```



- Array

~~~ html
 <script> 
        
        var months = [1,2,3,4,5,6,7,8,9,10,11,12];
        var days = ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"];
        var seasons = ["Spring", "Summer", "Fall", "Winter"];

        document.write("Months: "   + months + "<br>");
        document.write("days: "   + days + "<br>");
        document.write("<hr> "   + seasons.length + " types of seasons: ");
        
        for (i=0; i<seasons.length; i++) {
            document.write(seasons[i] + ' ');
        }

        document.write("<br>");
        document.write("<hr>" + seasons.length + " types of seasons : ");
        seasons.forEach(function(value) {
            document.write(value, ' ');
        })

        document.write("<br>");
        document.write("<hr>" + seasons.length + " types of seasons : ");
        for (var i in seasons) {
           document.write(seasons[i] + " ");

        }

      </script>
~~~

