```
//数组拆解origin
// function flat(arr, res) {
//     var i = 0, cur;
//     var len = arr.length;
//     for (; i < len; i++) {
//       cur = arr[i];
//       Array.isArray(cur) ? flat(cur, res) : res.push(cur);
//     }
//     return res;
//   }
//   let res = f(['a', ['b', ['c']], 'd', ['e']],[]);
//   console.log(res);
//数组拆解my
//   function f(arr,res){
//     for(let i = 0;i<arr.length;i++){
//         Array.isArray(arr[i])?f(arr[i],res):res.push(arr[i])
//     }
//     return res
//   }
//数组去重origin
//   function dedupe (client, hasher) {
//     hasher = hasher || JSON.stringify

//     const clone = []
//     const lookup = {}

//     for (let i = 0; i < client.length; i++) {
//         let elem = client[i]
//         let hashed = hasher(elem)

//         if (!lookup[hashed]) {
//             clone.push(elem)
//             lookup[hashed] = true
//         }
//     }

//     return clone
// }
// var a = [1, 2, 2, 3]
// var b = dedupe(a)
// console.log(b)
//数组去重my
// function de(arr){
//     let res = []
//     let obj = {}
//     for(let i = 0;i<arr.length;i++){
//         if(!obj[arr[i]]){
//             res.push(arr[i])
//             obj[arr[i]] = true
//         }
//     }
//     return res
// }
// var a = [1, 2, 2, 3]
// var b = de(a)
// console.log(b)

//diff origin
// function diff(arr/*, arrays*/) {

//   var len = arguments.length;
//   var idx = 0;
//   while (++idx < len) {
//     arr = diffArray(arr, arguments[idx]);
//   }
//   return arr;
// };

// function diffArray(one, two) {
//   if (!Array.isArray(two)) {
//     return one.slice();
//   }

//   var tlen = two.length
//   var olen = one.length;
//   var idx = -1;
//   var arr = [];

//   while (++idx < olen) {
//     var ele = one[idx];

//     var hasEle = false;
//     for (var i = 0; i < tlen; i++) {
//       var val = two[i];

//       if (ele === val) {
//         hasEle = true;
//         break;
//       }
//     }

//     if (hasEle === false) {
//       arr.push(ele);
//     }
//   }
//   return arr;
// }
//diff my
// function diff(one,two){
//     let res = []
//     let hasEle = false;
//     for(let i = 0;i<one.length;i++){
//         for(let j = 0;j<two.length;j++){
//             if(one[i]=two[j]){
//                res.push(one[i])
//                hasEle = true;
//                break 
//             }
//         }
//     }
// }
// var a = ['a', 'b', 'c', 'd'];
// var b = ['b', 'c'];
// let res = diff(a,b)
// console.log(res); //['a', 'd']
//inarry origin
// function inArray (arr, val) {
//     arr = arr || [];
//     var len = arr.length;
//     var i;
  
//     for (i = 0; i < len; i++) {
//       if (arr[i] === val) {
//         return true;
//       }
//     }
//     return false;
//   };
//inArray my
// function inArray(arr,val){
//     arr = arr || [];
//     for(let i = 0;i<arr.length;i++){
//         if(arr[i] === val){
//             return true
//         }
//     }
//     return false
// }
// console.log(inArray([1,2,3,],7));
```
