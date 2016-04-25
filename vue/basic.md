# Basic

## 一個 component 的基本

### 宣告一個 plan component
```
components: {
    plan: {
        template: '#plan-template'
        
        props: ['plan', 'active']
        
        created() {
            this.list = ....
        }
    }
}
```

### 宣告 template
```
<template id="plan-template">
</template>
```

### 使用 plan component
```
<div v-for="plan in plans">
    <plan :plan="plan" :active.sync="active"></plan>
</div>
```

## 常見的 compoenets 內屬性

- data
- computed
- watch
- methods
- components
- props
- template
- created

## 常見的 directive

- v-model
- v-show
- v-if
- v-for
- v-else

## 其他元素修飾

* @submit="function"
* @click="function"
