---
title: "[Algorithm] 가장 큰 수_ 프로그래머스"
categories:
  - Algorithm

---
Learn Algorithms :)


 [▶ 문제 바로가기](https://programmers.co.kr/learn/courses/30/lessons/42746)
)


### 문제 설명  
>0 또는 양의 정수가 주어졌을 때, 정수를 이어 붙여 만들 수 있는 가장 큰 수를 알아내 주세요.  

예를 들어, 주어진 정수가 [6, 10, 2]라면 [6102, 6210, 1062, 1026, 2610, 2106]를 만들 수 있고, 이중 가장 큰 수는 6210입니다.  

0 또는 양의 정수가 담긴 배열 numbers가 매개변수로 주어질 때, 순서를 재배치하여 만들 수 있는 가장 큰 수를 문자열로 바꾸어 return 하도록 solution 함수를 작성해주세요.  

### 제한 사항  
numbers의 길이는 1 이상 100,000 이하입니다.  
numbers의 원소는 0 이상 1,000 이하입니다.  
정답이 너무 클 수 있으니 문자열로 바꾸어 return 합니다.  


### 

```java
import java.util.*;
class Solution {
    public String solution(int[] numbers) {
      String answer ="";
            List<String> list = new ArrayList<>();
            int length = numbers.length;
 
            for(int i=0; i<length; i++){
                list.add(Integer.toString(numbers[i]));
            }
 
            int size = list.size();
            Collections.sort(list, (num1, num2) -> (num2+num1).compareTo(num1+num2));
            /*Collections.sort(list, new Comparator<String>(){
                @Override
                public int compare(String num1,String num2){
                    return (num2+num1).compareTo(num1+num2);
                }
            });
            이렇게 작성했으나 지원하지 않는다고 IDE가 람다식으로 바꿔줌*/
            if(list.get(0).equals("0")){
                return "0";
            }
 
            for(int i=0; i<size; i++){
                answer = answer + list.get(i);
            }
            return answer;
    }
}
```

---
참고
https://n1tjrgns.tistory.com/139  
https://developerdk.tistory.com/24

다리
https://dreamhollic.tistory.com/entry/%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%EB%AC%B8%EC%A0%9C%ED%92%80%EC%9D%B4-11-%EB%8B%A4%EB%A6%AC%EB%A5%BC-%EC%A7%80%EB%82%98%EB%8A%94-%ED%8A%B8%EB%9F%AD-JAVA  
https://developerdk.tistory.com/16

라면
https://dreamhollic.tistory.com/entry/Programmers-19-%EB%9D%BC%EB%A9%B4%EA%B3%B5%EC%9E%A5-JAVA  