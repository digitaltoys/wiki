array

### 깊은 복사
```
var arr1 = [1, 2, 3, 4];  
var arr2 = arr1.slice();
```

### 얕은 복사
```
var arr2 = arr1;
```

### 마지막 요소 제거
```
arr1.slice(0, -1);
```

### json group by
```javascript
var cars = [{ make: 'audi', model: 'r8', year: '2012' }, { make: 'audi', model: 'rs5', year: '2013' }, { make: 'ford', model: 'mustang', year: '2012' }, { make: 'ford', model: 'fusion', year: '2015' }, { make: 'kia', model: 'optima', year: '2012' }],
    result = cars.reduce(function (r, a) {
        r[a.make] = r[a.make] || [];
        r[a.make].push(a);
        return r;
    }, Object.create(null));

console.log(result);
```
