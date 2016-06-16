#js 原型
定义一个Person对象
包含name age gender 三个属性
function Persin(name,age,gender){this.name  = name; this.age =age; this.gender = gender;}

Person的原型///prototype关键字 '原型'
Personprototype={
<!--传入function.-->
<!--睡觉不需要参数-->
sleep:funtion(){ console.log(this.name +'每天睡觉八小时')},
<!--吃饭传入参数 food-->
eat:function(food){ console.log(this.name+'特别爱吃'+food)},
<!--不需要参数-->
deting:function(){ console.log('单身狗')}

birthday:function(){ var birthYear =(new Date()).getFullYear()-this.age; console.log(this.name+'的出生在'+birthYear+'年')}

}
<!--////强化.-->
<!--Student(name,age,gender,school)四个参数-->
<!--apply-->fun.apply(thisArg[, argsArray])  ----语法... apply
<!--参数-->

<!--thisArg-->
<!--    在 fun 函数运行时指定的 this 值。需要注意的是，指定的 this 值并不一定是该函数执行时真正的 this 值，如果这个函数处于非严格模式下，则指定为 null 或 undefined 时会自动指向全局对象（浏览器中就是window对象），同时值为原始值（数字，字符串，布尔值）的 this 会指向该原始值的自动包装对象。-->
<!--argsArray-->
<!--    一个数组或者类数组对象，其中的数组元素将作为单独的参数传给 fun 函数。如果该参数的值为null 或 undefined，则表示不需要传入任何参数。从ECMAScript 5 开始可以使用类数组对象。浏览器兼容性请参阅本文底部内容。 -->
function Student(name,age,gender,school){this.shcool =school; Person.apply(this.[name,age,gender]);}
function EmptyFun(){} ///设置空独显的原型为Person的原型 Emptyfun.prototype = person.prototype;
// var tem EmptyFun = new EmptyFun()//实例化的一个空对象// Student.prototype = temEmptyFun; ///设置学生的原型为实例化的空对象
// Student.prototype.constructor = Person
Student.prototype = Object.create(Person.prototype);
Student.prototype.constructor =Student

为学生原型定义一个方法goSchool = function(){ console.log(this.name + '每天早上八点准时去' +this.school);}


为学生创建一个dating方法
Student.prototype.dating = function(){ console.log('请勿在教师啪啪啪啪!');}





#HTML代码..... 简写 嵌入至HTML...在控制台内输出.
 <script> var person = new person ('jack',18'男');
 person.sleep();
 person.dating();
 person.eat('蛋炒饭');
 person.birthday();
 
 
 var student = new Student('小明',15,'男','县一中');
 console.dir(student);
 student.sleep();
 student.dating();
 student.eat('蛋炒饭');
 student.birthday();
 student.goSchool();
 </script>
<!--student实例化对象  实例化后的对象在查找属性或者方法的时候 首先在this自己内部查找 如果没有炸到 就会找到原型中查找 如果原型中没有 那么就回去u原型的原型继续查找. 直到找到位置 如果没有找到那么返回undefined或者报错-->

