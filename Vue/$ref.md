# $ref, $refs 로 DOM(Document Object Model) 점근

- Vue를 사용하는 중 DOM 요소에 직접 접근하여야 하는 경우에 `$ref` 사용

- JavaScript의 querySelector와 같은 역할

```vue
<template>
    <div>
        <input type="text" ref="something">
    </div>
</template>

<script>
export default {
    mounted(){
        console.log(this.$refs.something);
    }
}
</script>
```

- 접근하고 싶은 태그에 ref 속성명 지정

- ref는 중복 불가능

- $refs 로 해당 태그 접근 가능

- $refs는 component가 렌더링된 이후에 접근 가능