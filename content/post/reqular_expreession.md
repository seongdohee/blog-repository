---
type: "post"
draft: false
author: "author"
description: "정규표현식(reqular expreession)이란 문자들의 패턴을 표현하는 형식을 말한다. 문자열 처리에 있어서 정규표현5식을 사용하지 않아도 대부분 해결할 수 있지만, 필요 이상으로 코드가 길어지게 된다. 정규표현식을 이용하면 매우 간단하게 해결할 수 있다. (간단하게 사용할수 없다는게 함정..)"
keywords: ["javascript", "reqular expreession"]
topics: ["topic 1"]
tags: ["programming", "reqular expreession"]
title: "정규표현식"
---

`정규표현식(reqular expreession)`이란 문자들의 패턴을 표현하는 형식을 말한다.
문자열 처리에 있어서 정규표현5식을 사용하지 않아도 대부분 해결할 수 있지만, 필요 이상으로 코드가 길어지게 된다.
정규표현식을 이용하면 매우 간단하게 해결할 수 있다. (간단하게 사용할수 없다는게 함정..)

예로, 숫자 천단위마다 콤마를 찍어서 치환하는 경우를 코딩해보았다.
<pre>
<code class="javascript">
function groupByCommas(n) {
    var str = n.toString();
    var result = []; 
    for(var i = str.length-1, count = 1; i>=0;i--,count++) {
        result.push(str[i]);
        if(i != 0 && count%3 == 0) result.push(',');
    }
    return result.reverse().join('');
}
</code>
</pre>

천단위 콤마를 찍기 위해서 수행된 행동은 다음과 같다.  

1. 천 단위로 숫자를 잘라서 배열로 만든다.
+  배열 사이에 ','를 삽입한다. 
*  배열을 다시 문자열로 치환한다.



정규 표현식을 이용하면 어떻게 될까?
<pre>
<code class="javascript">
function groupByCommas(n) {
    return n.toString().replace(/(\d)(?=(?:\d\d\d)+(?!\d))/g, '$1,');
}
</code>
</pre>

....

코드가 한결 간결해졌을 뿐만 아니라 디버깅도 쉬워졌다. 처음 코드의 경우 행동에 따라 디버깅 포인트가 3가지나 있지만 아래 코드는 표현식 부분만 확인해주면 되기 때문이다.

그렇다면 정규표현식은 어떻게 쓸 수 있을까? 언뜻보기엔 쉬워보이지만 표현하고자 하는 문자열의 패턴이 복잡할수록 정규표현식도 복잡해진다. 
또, 하나의 문자열 패턴에서 수가지의 표현식이 나올 수 있기때문에 효율적으로 사용하려면 먼저 탄탄히 기본기를 잡는 것이 중요하다.

작성중...

