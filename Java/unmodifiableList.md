# List 의 unmodifiableList

- 자바 컬렉션에서 리스트에 데이터 추가한 뒤 더 이상의 데이터 추가, 삭제를 막기 위해서 Collection 에서 제공하는 unmodifiableList 사용

- 해당 리스트를 Read Only 로 변경해주는 메서드

- unmodifiableList 메서드 사용 후 해당 리스트에 add나 remove 메서드 사용 시 오류 발생 (UnsupportedOperationException)

```
Collections.unmodifiableList(list);
```

- List 값을 getter 로 return 해주는 경우 List 원본 그대로 return 해주기보다 unmodifiableList 적용하여 final 과 같은 배열로 변경하여 return 하는 것이 더 좋을 듯