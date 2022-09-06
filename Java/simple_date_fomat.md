# 자바 날짜 포맷 (SimpleDateFormat)

## 사용 방법

1. Date를 String 으로 포맷

```java
Date today = new Date();
SimpleDateFormat simpleDateFormat = new SimpleDateFormat("yyyy-MM-dd");
System.out.println(simpleDateFormat.format(today));
```

2. String을 Date 로 파싱

```java
try {
    String strDate = "2022-09-06";
    SimpleDateFormat simpleDateFormat = new SimpleDateFormat("yyyy-MM-dd");
    Date date = simpleDateFormat.parse(strDate);
} catch (ParseException e) {
    e.printStackTrace();
}
```

- 파싱하는 경우 파싱 오류 발생 가능


## 포맷 형식

문자 | 의미 | 타입 | 예시
-|-|-|-
G|연대(BC, AD)|Text|AD
Y|주 년|Year|2022;22
y|년도(주로 사용)|Year|2022;22
M|월(1~12)|Month|July;Jul;07
w|해당 년도의 몇 번째 주(1~53)|Number|53
W|해당 월의 몇 번째 주(1~5)|Number|5
D|해당 연도의 몇 번째 일(1~366)|Number|365
d|해당 월의 몇 번째 일(1~31)|Number31
F|해당 월의 몇 번째 요일(1~5)|Number|5
E|요일(월~일)|Text|Tuesday;Tue
u|1=월, ..., 7=일|Number|1
a|오전/오후(AM, PM)|Text|PM
H|시간(0~23)|Number|23
h|시간(1~12)|Number|12
K|시간(0~11)|Number|11
k|시간(1~24)|Number|24
m|분(0~59)|Number|59
s|초(0~59)|Number|59
S|1/1000초(0~999)|Number|999
X|타임존|ISO 8601 time zone|-08;-0800;-08:00
Z|타임존|RFC 822 time zone|+0900
z|타임존|General time zone|KST

## 예제

텍스트|결과
-|-
"yyyy.MM.dd G 'at' HH:mm:ss z"|2001.07.04 AD at 12:08:56 PDT
"EEE, MMM d, ''yy"|Wed, Jul 4, '01
"h:mm a"|12:08 PM
"hh 'o''clock' a, zzzz"|12 o'colock PM, Pacific Daylight Time
"K:mm a, z"|0:08 PM, PDT
"yyyyy.MMMMM.dd GGG hh:mm aaa"|02001.July.04 AD 12:08 PM
"EEE, d MMM yyyyy HH:mm:ss Z"|Wed, 4 Jul 2001 12:08:56 -0700
"yyMMddHHmmssZ"|010704120856-0700
"yyyy-MM-dd'T'HH:mm:ss.SSSZ"|2001-07-04T12:08:56.235-0700
"yyyy-MM-dd'T'HH:mm:ss.SSSXXX"|2001-07-04T12:08:56.235-07:00
"YYYY-'W'ww-u"|2001-W27-3