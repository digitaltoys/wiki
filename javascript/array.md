array

### 깊은 복사
```javascript
var arr1 = [1, 2, 3, 4];  
var arr2 = arr1.slice();
```

### 얕은 복사
```javascript
var arr2 = arr1;
```

### 마지막 요소 제거
```javascript
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

### filter
```javascript
const ages = [32, 33, 16, 40];

const result = ages.filter((age) {
  return age >= 18;
});
```

### 배열의 교집합 구하기
```javascript
const filteredArray = array1.filter(value => array2.includes(value));
```
