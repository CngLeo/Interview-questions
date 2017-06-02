```javascript
/**
 * Created by Undefined on 2017/5/24.
 */
function isMatch(str1, str2){
    return !str1.split('').sort().join('').replace( str2.split('').sort().join(''), '');
}

function isMatch1(str1, str2){
    return str1.split('').sort().join('') === str2.split('').sort().join('');
}

/*console.time( 'isMatch' );
 for(var i=0; i<1000; i++){
 isMatch('hello', 'hlloe')
 }
 console.timeEnd('isMatch');
 console.time( 'isMatch1' );
 for(var i=0; i<1000; i++){
 isMatch1('hello', 'hlloe')
 }
 console.timeEnd( 'isMatch1' );*/

/*
 *
 * isMatch: 8.305ms
 * isMatch1: 2.624ms     //isMatch1() 经测试该方法更好
 *
 * */

// isMatch('hello', 'olleh'); true

// isMatch('aaa', 'aa'); false

// isMatch('abb', 'baa'); false


/* 使用ES6实现该方法 */

const obj = {a:1, b:2, c:3}
const arr = ['a', 'c'];

function foo(obj, arr){
    let obj1 = {};
    arr.map((i) => obj1[i] = obj[i]);
    return obj1;
}

// foo(obj, arr); {a:1, c:3}

// console.log( foo(obj, arr) );

function foo1(obj, arr){
    var obj1 = {};
    arr.forEach( (i)=>obj1[i]=obj[i] );
    return obj1;
}

// console.log( foo1(obj, arr) );

/*
 console.time(1);
 for(let i=0; i<100000; i++){
 foo(obj, arr)
 }
 console.timeEnd(1);
 console.time(2);
 for(let i=0; i<100000; i++){
 foo1(obj, arr)
 }
 console.timeEnd(2);
 */

/*
 *
 * 1: 39.198ms
 * 2: 15.062ms   //推荐使用forEach()
 *
 * */

/*
 arr.forEach(function(i){
 console.log(i);
 });
 arr.forEach((i)=>console.log(i));*/

/*for (var i = 0; i < 5; i++) {
 (function(i) {
 setTimeout(function() {
 console.log(i);
 }, i * 1000);
 })(i);
 }*/

/*
 for (var i = 0; i < 5; i++) {
 (function() {
 setTimeout(function() {
 console.log(i);
 }, i * 1000);
 })(i);
 }*/

/*for (var i = 0; i < 5; i++) {
 setTimeout((function(i) {
 console.log(i);
 })(i), i * 1000);
 }*/

var a = 1;

function fn(){
    var a;
    console.log(a);
    var a = 5;
    console.log(a);
    a++;
    fn3();
    fn2();
    console.log(a);

    function fn2(){
        a = 20;
    }
}

function fn3(){
    console.log(a)
    a = 200;
}

// fn();
// console.log(a);

/* ~的作用是什么? ~4的结果是多少？为什么? */
/*
 console.log( ~44 );
 console.log( ~~4);
 console.log(~(-6));
 */

/* 写一个函数 isEmptyObject，判断一个对象是不是空对象 */

function isEmptyObject(obj){
    if( arguments[0] && typeof arguments[0] === 'object' ){
        for(let key in obj){
            return false;
        }
        return true;
    }
    throw 'obj need to an object'
}


{
    let obj = {
        name: 'cnu',
        age: 23
    }

    //for(let key in obj){
    //    console.log( key );
    //}

    function isEmptyObject1(obj){
        if( !(arguments[0] && arguments[0].constructor === Object) ) throw 'obj need an object';
        return Object.keys(obj).length === 0 && obj.constructor === Object
    }

    // console.log( isEmptyObject1({}) );
}
/*
 {
 let arr1 = [1,2,3];
 let arr2 = [4,5,6];
 console.log( arr1.concat(arr2) );
 }*/

{
    let obj = {a:1,b:2}

    for(let key in obj){
        // console.log( obj.hasOwnProperty(key) );
    }
}

/*
 *   json转字符串
 * */
var json = {a:1, b:2,c:3};

// console.log( typeof JSON.stringify(json));


/* json字符串转json */
var str = '{"a":1, "b":2,"c":3}';

// console.log( typeof eval('('+str+')') ); // 古老的json字符串解析成json的方式

// console.log( typeof JSON.parse(str) );

// console.log( typeof new Function("return"+str)() );


let result = (2..valueOf() + ({a:10, b:40}).a);
// console.log( result );

/*
 * 原因：
 * 1.2..valueOf()中用到两个点是因为JS对数字后面的第一个点识别为小数点，第二个点识别为运算符，2..valueOf()得出的结果是数字2；
 * 2.({a:10, b:40}).a中相当于求对象{a:10, b:40}中a的值，a值为10，所以({a:10, b:40}).a结果是10；
 * 3.得出(2..valueOf() + ({a:10, b:40}).a)等于2+10为12；
 * */

//var str = new String("Hello");
//var result = typeof(str instanceof String);
//console.log(result);
//result = typeof typeof(str instanceof String);
//console.log(result);
//result = typeof typeof typeof(str instanceof String);
//console.log(result);

//var str1 = 'hahaha';
//var result1 = typeof( str1 instanceof String );
//console.log( result1 );
//result1 = typeof typeof(str1 instanceof String);
//console.log( result1 );
//result1 = typeof typeof typeof(str1 instanceof String);
//console.log( result1 );

//var object1 = {
//    valueOf: function () {
//        return 10;
//    },
//    toString: function () {
//        return "object1";
//    }
//};
//
//var object2 = {
//    valueOf: function () {
//        return 20;
//    },
//    toString: function () {
//        return "object2";
//    }
//};
//
//var object3 = {
//    valueOf: function () {
//        return 30;
//    },
//    toString: function () {
//        return "object3";
//    }
//};
//
//var result = (object2, object1, object3) + object1 +-- object1;
//console.log(result);

/*
 * 逗号运算符,的作用是对每个表达式求值,并返回最后一个表达式的值
 * (a,b)//b
 所以 (object2, object1, object3) + object1 +-- object1;.
 可以简化为object3 + object1 +--object1
 即object3 + object1 + (-- object1)
 从右向左计算.第一个运算符是--自减运算符.
 需要讲其转换成数值.
 如果运算子是对象，先执行该对象的valueOf方法.
 式子变为
 30+10+9
 结果是49
 * */

var object1 = {
    valueOf: function () {
        return 1;
    },
    toString: function () {
        return "object1";
    }
};

var object2 = {
    valueOf: function () {
        return 2;
    },
    toString: function () {
        return "object2";
    }
};

// console.log((object2 > object1 + --object1) + true);

/*
 * (object2 > object1 +-- object1) + true)
 object1和object2 都是对象，所以运算的时候会调用valueOf方法，所以得到：
 (2 > 1 + --1) + true)
 --1为前递减所以为0，2 > 1为true 得到：
 (true + 0) + true)
 布尔值在运算时会自动转为数字 true -> 1 false -> 0
 得到：
 (1+ 0) + 1)
 所以结果是2
 *
 * */

/* 数组去重 */
{
    let arr = ['a','f','c','s','g','s','t','s','a','a','f','g','s','g','s','t','s','t','b','n','v','b','c','f'];

    function uniq(arr){
        let temp = [];
        for(let i=0; i<arr.length; i++){
            if(temp.indexOf(arr[i]) == -1){
                temp.push(arr[i]);
            }
        }
        return temp;
    }

    // console.log( uniq(arr) );
}


/* es6解法 */
{
    let arr = ['a','f','c','s','g','s','t','s','a','a','f','g','s','g','s','t','s','t','b','n','v','b','c','f'];

    let uniq = (arr) =>Array.from( new Set(arr) );

    // console.log( uniq(arr) );
}

/* 双重循环解法 */
{
    let arr = ['a','f','c','s','g','s','t','s','a','a','f','g','s','g','s','t','s','t','b','n','v','b','c','f'];

    function uniq(arr){
        for(let i=0; i<arr.length; i++){
            for(let j=i+1; j<arr.length; j++){
                if(arr[i] === arr[j]){
                    arr.splice(j, 1);
                    j--;
                }
            }
        }
        return arr;
    }
    // console.log( uniq(arr) );
}

// 1.数组中奇数在前，偶数在后
{
    let arr = [1,2,3,4,5,6,7,8,9,10];

    function sort(arr){
        let left = [],
            right = [];
        for(let i=0; i<arr.length; i++){
            if(arr[i]%2 != 0){
                left.push(arr[i]);
            }else{
                right.push(arr[i]);
            }
        }
        let result = left.concat(right);
        return result;
    }

    // console.log( sort(arr) );

}

//4.计算数组中奇数和偶数的个数
{
    let arr = [1,2,3,4,5,6,7,8,9,10, 2, 8, 9];

    function countNum(arr){
        let even = 0;
        let odd = 0;
        for(let i=0; i<arr.length; i++){
            arr[i]%2 == 0? even++ : odd++;
        }
        console.log( '奇数为：'+ odd + ',偶数为：'+ even );
    }

    // countNum(arr);

}

// 数组去重
{
    let arr = [1,2,3,4,1,2,3,4];

    function uniq(arr){
        let result = [];
        for(let i=0; i<arr.length; i++){
            if( result.indexOf(arr[i]) === -1 ){
                result.push(arr[i]);
            }
        }
        return result;
    }

    // console.log( uniq(arr) );

    function uniq1(arr){
        return Array.from( new Set(arr) );
    }
    // console.log( uniq1(arr) );

}

//5.随机选取10到100之间的10个数字，并排序

{
    var random = (startNum, endNum) => {
        let result = [];
        function getRandom(startNum, endNum){
            let iChoice = endNum - startNum;
            let randomNum = Math.floor( Math.random()*iChoice+10 );
            return randomNum;
        }

        for(let i=0; i<10; i++){
            result.push( getRandom(startNum, endNum) );
        }
        return result.sort();
    }

    // console.log( random(10, 100) );
}

//6.首字母大写
{
    let str = 'HELLO, WORLD';

    let firstUpper = (str) => {
        let new_arr = str.toLowerCase().split(' ');
        for(let i=0; i<new_arr.length; i++){
            new_arr[i] = new_arr[i].charAt(0).toUpperCase() + new_arr[i].substring(1);
        }
        let result = new_arr.join('');
        return result;
    }

    // console.log( firstUpper(str) );

}

// 方法二：利用replace()
{
    let str = 'HELLO, CNU';

    let firstUpperCase = (str) => {
        var new_arr = str.toLowerCase().split(' ');
        for(let i=0; i<new_arr.length; i++){
            let firstStr = new_arr[i].charAt(0);
            new_arr[i] = new_arr[i].replace(firstStr, function(firstStr){
                return firstStr.toUpperCase();
            });
        }
        return new_arr.join('');
    };

    // console.log( firstUpperCase(str) );

}

// 7.判断字符串中出现最多次的字符,统计次数
{
    var str="lalwayssssswanttolearnmoreknowlledde";
    let statistics = (str) => {
        let json = {},
            maxNum = 0,
            maxWord = null;
        for(let i=0; i<str.length; i++){
            let word = str.charAt(i);
            if(json[word]){
                json[word]++;
            }else{
                json[word]=1;
            }
        }

        for(let key in json){
            if(maxNum < json[key]){
                maxNum = json[key];
            }
            if(json[key] == maxNum){
                maxWord = key;
                console.log("次数最多的字符是:"+maxWord+"次数为:"+maxNum);
            }
        }
    }
    // statistics(str);
}

// 8判断第一个偶数的位置
{
    let arr=[1,5,7,5,8,7,11,33,4];
    let firstEven = (arr) => {
        let firstEvenValue = '';
        let firstEvent = 0;
        for(let i=0; i<arr.length; i++){
            if(arr[i]%2 === 0){
                firstEvenValue = arr[i];
                firstEvent = ++i;
                break;
            }
        }
        return `第一个偶数是${firstEvenValue}, 位置在${firstEvent}号位`;
    }

    console.log( firstEven(arr) );

}
```
