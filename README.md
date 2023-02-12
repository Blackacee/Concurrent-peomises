# Concurrent-peomises
 
// wait "millis" ms, then resolve with "value"
function resolve(value, milliseconds) {
 return new Promise(resolve => setTimeout(() => resolve(value), milliseconds));
}
// wait "millis" ms, then reject with "reason"
function reject(reason, milliseconds) {
 return new Promise((_, reject) => setTimeout(() => reject(reason), milliseconds));
}
Promise.all([
 resolve(1, 5000),
 resolve(2, 6000),
 resolve(3, 7000) 
]).then(values => console.log(values)); // outputs "[1, 2, 3]" after 7 seconds.
Promise.all([
 resolve(1, 5000),
 reject('Error!', 6000),
 resolve(2, 7000)
]).then(values => console.log(values)) // does not output anything
