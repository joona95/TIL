# Utility Types

## Partial\<Type\>

```ts
type Todo = {
    title: string;
    description: string;
}

const todo1: Todo = {
    title: "todo1",
    description: "abcdefg",
}; //ok

const todo2: Partial<Todo> = {
    title: "todo2",
}; //ok
```

- 특정한 type의 속성들(properties)을 optional 하게 설정한 타입 정의 가능

- updateTodo(todo: Todo) 였다면 type error 가 떠야 하지만 Partial\<Todo\>로 optional이라 모든 속성을 가지고 있지 않아도 괜찮음

## Required\<Type\>

```ts
type Todo = {
    title?: string;
    description?: string;
}

const todo1: Todo = {
    title: "todo1",
}; // ok

const todo2: Required<Todo> = {
    title: "todo2",
}; // x
```

- Partial\<Type\>과 반대로 Required\<Type\>은 모든 속성들(properties)을 필수(required)로 설정한 타입 정의 가능

## Pick\<Type, Keys\>

```ts
type Todo = {
    title: string;
    description: string;
    completed: boolean;
}

type TodoPreview = Pick<Todo, "title" | "completed">;

const todo1: TodoPreview = {
    title: "todo1",
    completed: false,
}; // ok
```

- 특정한 타입에서 특정 key 값들만 포함해서 새로운 타입 정의가 가능

## Omit\<Type, Keys\>

```ts
type Todo = {
    title: string;
    description: string;
    completed: boolean;
}

type TodoTitle = Omit<Todo, "description" | "completed">;

const todo1: TodoTitle = {
    title: "todo1",
}; // ok
```

- 특정한 타입에서 특정 key 값들만 생략한 새로운 타입 정의가 가능