# IIFE

## IIFE nedir ?
JavaScriptte yalnızca bir kez kullanacağımız ve sonrasında tekrar ihtiyacımız olmayacak fonksiyonlar kullanmak zorunda kalabiliriz. 
Bu tarz durumlarda tercih ettiğimiz fonksiyonlara  "Immediately Invoked Function Expression" (IIEF) adı  verilir. 
Bu fonksiyonlar tanımlandıkları yerde hemen çağrılarak çalıştırılır.    

## Kullanım örnekleri nelerdir ?
Normalde bir fonksiyona ihtiyacımız olduğunda "Function Declaration" ya da "Function Expression" kullanırız ve bu fonksiyonları ihtiyacımız olduğu her an çağırıp yeniden kullanabiliriz. 

Function Declaration:                                       

function calc (p1, p2) {
    return p1 * p2;
}
alert(calc (4, 3));
//12

Function Expression:

let calc = function(p1, p2){
    return p1 * p2;
}
alert(calc (4,3));
//12


Fakat IIEF kullanmayı tercih ettiğimiz durumlarda daha farklı bir yol izleriz. 
Alttaki örnek kullanımda görüldüğü gibi fonksiyonumuzu parantez içine aldıktan hemen sonra () kullanarak fonksiyonu tanımlandığı yerde çağırmak istediğimizi belirtiriz. 

* Genel kullanım ;

(function() {

  let message = "Hello";

  alert(message); // Hello

})();

* İsimlendirilerek kullanım;

(function doSomething() {

  // do something
  
})();

* "Arrow Function" biçiminde kullanım;

( () => {

    // do something
    
})();


## Syntax Hataları

Fonksiyonu saracak parantezleri kullanmadığımız takdirde JavaScript kod akışında "function" görüp bunu fonksiyon tanımı olarak algılar.
Fakat fonksiyona karşılık gelen bir isim bulamadığı için alttaki hatayı verecektir.

// Error: Unexpected token (


function () {                        // <-- JavaScript fonksiyon ismini bulamadı. ('i gördü ve hemen hata verdi.

  let mesaj = "Merhaba";

  alert(mesaj); // Merhaba

}();

İlk durumda karşılaştığımız hatanın sebebi fonksiyonun isimsiz olmasıydı fakat bu problemi fonksiyonu isim ile tanımlayarak da çözemeyiz. 
Çünkü JavaScript, fonksiyon tanımlamalarının anında çalışmasına izin vermez ve yine hata verir.

                              // Bu defa aşağıdaki parantez hata verecektir.
function message () {

  let mesaj = "Merhaba";

  alert(mesaj); // Merhaba
  
}();                          // <-- Fonskyion Tanımı anında çalıştırılamaz.


Bu hataları almamak için fonksiyonumuzu () ile sarmamız gerekir.


## IIFE kullanım amacı ve faydaları nelerdir ?

IIFE'nin temel kullanım amacı, fonksiyon içinde yer alan değerlere dışarıdan erişimi engelleyerek izole bir kapsam oluşturmaktır. 
Alttaki örnekten de anlaşılacağı üzere, fonksiyonu saran parantezler sayesinde fonksiyon içindeki değerler sadece bu fonksiyon çağrıldığında kullanılabilecek durumdadır ve dışarıdan erişmek mümkün değildir.  
Bu sayede fonksiyon içindeki değerlerin yanlışlıkla değiştirilmesi gibi istenmeyen durumların önüne geçilmiş olur.

(function() {
   let firstName = "Steve";
}
)();

console.log(firstName);

//  Uncaught ReferenceError: firstName is not defined
