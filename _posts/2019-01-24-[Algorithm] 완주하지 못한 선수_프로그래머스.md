---
title: "[Algorithm] 완주하지 못한 선수_ 프로그래머스"
categories:
  - Algorithm

---
Learn Algorithms :)


 [▶ 문제 바로가기](https://programmers.co.kr/learn/courses/30/lessons/42576?language=java
)


#### 문제 설명  
>수많은 마라톤 선수들이 마라톤에 참여하였습니다.  
단 한 명의 선수를 제외하고는 모든 선수가 마라톤을 완주하였습니다.  
마라톤에 참여한 선수들의 이름이 담긴 배열 participant와  
완주한 선수들의 이름이 담긴 배열 completion이 주어질 때,  
완주하지 못한 선수의 이름을 return 하도록 solution 함수를 작성해주세요.  


```java
import java.util.*;
class Solution {
    public String solution(String[] participant, String[] completion) {
        Arrays.sort(participant);
        Arrays.sort(completion);
        int i;
        for ( i=0; i<completion.length; i++){

            if (!participant[i].equals(completion[i])){
                return participant[i];
            }
        }
        return participant[i];
    }
}
```

