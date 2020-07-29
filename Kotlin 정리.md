# Kotlin 정리

## 흐름제어

- break : 반복 종료 및 다음 구문으로 넘어가기
- continue : 다음 반복 조건으로 넘어가기

```
fun main() {
	for(i in 0..9) { //0에서 9까지
		if(i == 3) break //i가 3이면 break
		print(i)  // i 출력
	}
}
```

```
12
```

```
fun main(){
	for(i in 0..9){  // 0부터 9까지
		if(i==3) continue  // i가 3이면 print실행하지 않고 다음으로 넘어가기
		print(i)  // i 출력
	}
}
```

```
12356789
```



- label: 다중 반복문에서 break 혹은 continue가 적용되는 반복문 지정

<label 미적용>

```
fun main(){
    for(i in 1..4){
        for(j in 1..4){
            if(i == 1 && j == 2) break
            print("i == $i, j == $j \n")
        }
    }
}
```

```
i == 1, j == 1 
i == 2, j == 1 
i == 2, j == 2 
i == 2, j == 3 
i == 2, j == 4 
i == 3, j == 1 
i == 3, j == 2 
i == 3, j == 3 
i == 3, j == 4 
i == 4, j == 1 
i == 4, j == 2 
i == 4, j == 3 
i == 4, j == 4 

Process finished with exit code 0
```

<label 적용>

```
fun main(){
    loop@for(i in 1..4){  // loop시작구간: 1부터 4까지 반복
        for(j in 1..4){   // 1부터 4까지 반복
            if(i == 1 && j == 2) break@loop  //loop끝구간:i가 1, j가 2일경우 break
            print("i == $i, j == $j \n")  // 결과값 출력
        }
    }
}
```

loop@와 @loop로 break를 실행할 범위를 지정한다. 

```
i == 1, j == 1 

Process finished with exit code 0
```



## 논리연산자

- && : 앞 뒤의 논리값이 모두 true일 경우, true값 반환 
- || : 앞 뒤 중 하나만이라도 true일 경우, true값 반환
- ! : 뒤의 논리값의 반대값 반환

```
fun main(){
    println(true && false) //and 연산자
    println(true || false) //or 연산자
    println(!true) //not 연산자
    println(!false)  //not 연산자
}
```

```
false
true
false
true

Process finished with exit code 0
```



 