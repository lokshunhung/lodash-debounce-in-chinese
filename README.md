# 底橫的去抖動

註：在生產環境中請使用[這個依賴](https://www.lodashjs.com/docs/lodash.debounce)

```ts
type 任何 = any;
type 空虛 = void;
type 未定義 = undefined;
type 數組<類> = Array<類>;
type 數字 = number;
type 布林 = boolean;
let 如果 = (條件: 任何, 然後: () => 空虛, 否則: () => 空虛) => (條件 ? 然後() : 否則());
let 真 = true;
let 假 = false;
let 設置定時 = setTimeout as (<類 extends 數組<任何>>(函數: (...參數: 類) => 空虛, 延遲: 數字, ...參數: 類) => 數字);
let 取消定時 = clearTimeout as ((定時器編號: 數字) => 空虛);
let 打印 = console.log;

let 底橫 = {
    去抖動<類 extends 數組<任何>>(函數: (...參數: 類) => 空虛, 延遲: 數字 = 0) {
        let 定時器編號: 數字;
        return (...參數: 類): 空虛 => {
            取消定時(定時器編號);
            定時器編號 = 設置定時(函數, 延遲, ...參數);
        };
    },
};
```

## 使用方法

```ts
你好 = 底橫.去抖動(() => 打印("你好世界"), 300);

你好();
你好();
你好();
```
