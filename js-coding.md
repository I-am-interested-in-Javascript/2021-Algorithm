# JavaScript 코딩 테스트 준비자료

<!--
https://www.youtube.com/watch?v=miiM5JJgrQo&list=PLkBfv4fGBau-q9tGBUgVoGClRsSBiiZm8&ab_channel=whatsdev -->

1. let, const로 쓰기
2. `===`사용하기
3. 원본 객체를 건드리지 않는 방향으로 할것
4. 삼항 연산자는 간략하게만 사용할 것
5. if-else보다는 switch문

<!-- JavaScript 알고리즘 문제풀이: https://www.inflearn.com/course/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%EB%AC%B8%EC%A0%9C%ED%92%80%EC%9D%B4#curriculum -->

6. 정렬

7. 문자열 처리

- string.reverse()
- str.split("");

8. 큐
<!-- https://ryusm.tistory.com/48 -->

- pop(): Remove an item from the end of an array.
- push(): Add items to the end of an array.
- shift(): Remove an item from the beginning of an array.
- unshift(): Add items to the beginning of an array.

9. 배열

   - 일반 객체와 가장 큰 차이점은 값의 순서와 length property
   - 희소 배열임, 일반적인 배열의 동작을 흉내낸 특수한 객체
   - JavaScript 배열은 해쉬테이블로 만들어져서 인덱스로 접근할때 보통의 배열보다 느릴수밖에 없지만, 삽입 삭제할때는 빠를수있다.
   - 삭제할때 희소배열을 만들지 않으려면 splice(`원본을 직접 변경함`)

   ```javascript
   const arr = [1, 2, 3];
   // Array.prototype.splice(삭제 시작 인덱스, 삭제할 요소 수, optional 해당 위치에 넣을값)
   arr.splice(1, 1);

   // 삭제할 요소수를 0으로 하고 optional 해당 위치에 넣을값만 주면 해당 위치에 값을 삽입한다.
   arr.splice(1, 0, 100); // 1, 100, 2, 3

   // 첫번째 값만 주면 거기부터 다 지움
   arr.splice(1); // 인덱스 1 부터 다지움, [1]
   ```

   - slice: 복사해서 배열로 반환, `splice랑은 다르게 원본을 변경안함`, shallow카피다
     - 얘로 유사배열 객체를 배열로 쉽게 변환가능하다

   ```javascript
   const arr = [1, 2, 3];
   arr.slice(); // 전체다 복사

   arr.slice(1); // 인덱스 1부터 복사
   ```

   - 배열메서드는 원본을 바꾸는것과 안바꾸는것이 있어서 주의해야함
   - isArray: 전달된 인수가 배열인지 아닌지
   - indexOf(값): 해당값의 인덱스를 구하거나, 없으면 -1
   - includes(값): 해당값이 있는지 없는지 true, false
   - concat: 배열에 값을 더 붙이거나 배열을 해체해서 붙임. `원본은 변경 x`
   - filter
   - join: 내부에 있는값을 문자로 만들어서 구분자(기본은 콤마)로연결해서 문자열을 반환
   - reverse: 뒤집음 `원본이 변경`
   - array.fill: 해당값으로 채운다 `원본이 변경`

   ```javascript
   const arr = new Array(4);
   console.log(arr); // 희소배열이 만들어짐
   const result = arr.fill(1); // 1로 다 채워짐

   // from을 통해서도 가능하다
   const sequences = (length = 0) => Array.from({ length }, (_, i) => i);
   ```

   - flat: 중첩배열을 평탄화, 기본적으론 1

   - 고차 함수
     - sort: 원본을 바꾸고 반환한다, reverse
       - sort, reverse둘다 기본적으로 숫자를 문자로 변환한뒤에 비교하기때문에숫자가제대로 정렬이 안된다
         ```javascript
         const a = [1, 3, 4, 10, 11];
         a.sort(); // [1, 10, 11, 3, 4]
         a.reverse(); // [4, 3, 11, 10, 1]
         ```
         정렬순서를 비교하는 함수를 전달해야함
         - 오름차순:(a, b) => a - b , 0보다 작으면 a를 앞으로
         - 내림차순:(a, b) => b - a, 0보다 작으면 b를 앞으로
       - forEach: 각 값에 callback적용, 언제나 undefiend반환)
       - map: 콜백을 적용해서 만든 새로운 배열을 반환한다, 언제나 반환값들로 구성된 새로운 배열을 반환
       - filter: 원본을 변경하지 않고, 해당 조건에 해당되는 것들로 배열을 새로 구성해서 반환
       - reduce: 각 콜백함수의 반환값을 다음 콜백한수의 인자로 넘겨서 하나의 결과값을 만들어서 반환

10. number
11. Math
12. RegExp
13. String
