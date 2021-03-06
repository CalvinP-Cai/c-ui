# c-ui

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

### Eslint+Prettier校验说明
```text
"off"或者0      //关闭规则关闭
"warn"或者1     //在打开的规则作为警告（不影响退出代码）
"error"或者2    //把规则作为一个错误（退出代码触发时为1）
```
#### eslint和prettier的冲突
```text
    错误日志
        15:7   warning  Delete `·`                                 prettier/prettier
        19:24  error    Missing space before function parentheses  space-before-function-paren
    
    eslint配置
      'space-before-function-paren': ['error', 'always'],    // 冲突

    解决：
      npm uninstall prettier
```
**eslint和prettier基本配置**
```text
eslint：
    'indent': [2, 2],                     // 强制使用一致的缩进
    'eqeqeq': [2, "always"],              // 要求使用 === 和 !==
    'semi': [2, "never"],                 // 语句强制分号结尾 'always' 、 语句不要分号结尾 'never'
    'quotes': [2, "single"],              // 强制使用一致的反勾号、双引号或单引号
    'no-trailing-spaces': 'error',        // 禁用行尾空格
    'no-spaced-func': 'error',            // 函数调用时 禁止 function 标识符和圆括号之间有空格
    'comma-dangle': [2, 'never'],         // 要求或禁止使用尾随逗号；最后一个属性是不需要逗号 错误：{ a: 1, b: 1, }
    'arrow-spacing': ["error", { 'before': true, 'after': true }],         // =>的前/后括号
    'space-before-function-paren': ['error', 'always'],                    // (默认) 要求在参数的 ( 前面有一个空格。
    'lines-around-comment': ['error', { 'beforeBlockComment': true }],     // 强制注释周围有空行

prettier：
      'tabWidth': 2,                // 缩进字节数
      'useTabs': false,             // 缩进不使用tab，使用空格
      'semi': false,                // 句尾添加分号
      'singleQuote': true           // 使用单引号代替双引号
      'endOfLine': 'auto',          // 结尾是 \n \r \n\r auto
      'trailingComma': 'none',      // 在对象或数组最后一个元素后面是否加逗号（在ES5中加尾逗号）
```

## Description
本项目利用业余时间一点一点积累，希望可以写出一套基于Vue2.x的移动端ui组件库

## Develop Rules
1、方法名 与圆括号 和 花括号之间必须加空格

正确【✔】
```JS
    function func () {
        // TODO...
    }
```
错误【❌】
```js
    function func() {
    //    TODO
    }

    function func(){
    //    TODO
    }
```
2、任何语句的结束不允许出现空格

正确【✔】
```js
    var count = 0
```

错误【❌】
```js
    var count = 0 
```

3、注释一定要写，组件一定要有注释说明该租价的作用, 入参、出参一定要有注释，晦涩难懂的方法名、变量一定要加注释
```js
    /**
     * 该方法的作用，入参
     * @param target | [Array, String] | 含义
     */
    function func (target) {
    //    TODO
    }
    // 一定要说明作用
```

4、语句后不加分号，特殊必须加分号
```js
    (function () {
    //    TODO
    }());
```
5、命名规范

1）组件名应该始终是多个单词组成（大于等于 2），且命名规范为KebabCase格式。
这样做可以避免跟现有的以及未来的 HTML 元素相冲突，因为所有的 HTML 元素名称都是单个单词的。

正确【✔】
```vue
    export default {
        name: 'TodoItem'
    }
```

错误【❌】
```vue
    export default {
        name: 'Todo'
    }
    export default {
        name: 'todo-item'
    }
```
2） 组件文件名为 pascal-case 格式

正确【✔】
```text
    components/
    |- my-component.vue
```

错误【❌】
```text
    components/
    |- myComponent.vue
    |- MyComponent.vue
```
3） 基础组件文件名为 base 开头，使用完整单词而不是缩写。

正确【✔】
```text
    components/
    |- base-button.vue
    |- base-table.vue
    |- base-icon.vue
```

错误【❌】
```text
    components/
    |- MyButton.vue
    |- VueTable.vue
    |- Icon.vue
```

4） 和父组件紧密耦合的子组件应该以父组件名作为前缀命名

正确【✔】
```text
    components/
    |- todo-list.vue
    |- todo-list-item.vue
    |- todo-list-item-button.vue
    |- user-profile-options.vue （完整单词）
```

错误【❌】
```text
    components/
    |- TodoList.vue
    |- TodoItem.vue
    |- TodoButton.vue
    |- UProfOpts.vue （使用了缩写）
```
5） 在 Template 模版中使用组件，应使用 PascalCase 模式，并且使用自闭合组件。

正确【✔】
```text
    <!-- 在单文件组件、字符串模板和 JSX 中 -->
    <MyComponent />
    <Row><table :column="data"/></Row>
```

错误【❌】
```text
    <my-component /> <row><table :column="data"/></row>
```

6） 如果特性元素较多，应该主动换行。

正确【✔】
```text
    <MyComponent foo="a" bar="b" baz="c"
        foo="a" bar="b" baz="c"
        foo="a" bar="b" baz="c"
     />
```

错误【❌】
```text
    <MyComponent foo="a" bar="b" baz="c" foo="a" bar="b" baz="c" foo="a" bar="b" baz="c" foo="a" bar="b" baz="c"/>
```

7） 采用小写驼峰命名 lowerCamelCase，代码中的命名均不能以下划线，也不能以下划线或美元符号结束

错误【❌】
```text
     _name / name_ / name$
```

8） 方法名、参数名、成员变量、局部变量都统一使用 lowerCamelCase 风格，必须遵从驼峰形式。

正确【✔】
 ```text
    localValue / getHttpMessage() / inputUserId
```

*其中 method 方法命名必须是 动词 或者 动词+名词 形式*

正确【✔】 
```text
    saveShopCarData /openShopCarInfoDialog
```

错误【❌】
```text
    save / open / show / go
```

*特此说明，增删查改，详情统一使用如下 5 个单词，不得使用其他（目的是为了统一各个端）*

```text
    add / update / delete / detail / get
```
*附： 函数方法常用的动词:*

```text
    get 获取/set 设置,
    add 增加/remove 删除
    create 创建/destory 移除
    start 启动/stop 停止
    open 打开/close 关闭,
    read 读取/write 写入
    load 载入/save 保存,
    create 创建/destroy 销毁
    begin 开始/end 结束,
    backup 备份/restore 恢复
    import 导入/export 导出,
    split 分割/merge 合并
    inject 注入/extract 提取,
    attach 附着/detach 脱离
    bind 绑定/separate 分离,
    view 查看/browse 浏览
    edit 编辑/modify 修改,
    select 选取/mark 标记
    copy 复制/paste 粘贴,
    undo 撤销/redo 重做
    insert 插入/delete 移除,
    add 加入/append 添加
    clean 清理/clear 清除,
    index 索引/sort 排序
    find 查找/search 搜索,
    increase 增加/decrease 减少
    play 播放/pause 暂停,
    launch 启动/run 运行
    compile 编译/execute 执行,
    debug 调试/trace 跟踪
    observe 观察/listen 监听,
    build 构建/publish 发布
    input 输入/output 输出,
    encode 编码/decode 解码
    encrypt 加密/decrypt 解密,
    compress 压缩/decompress 解压缩
    pack 打包/unpack 解包,
    parse 解析/emit 生成
    connect 连接/disconnect 断开,
    send 发送/receive 接收
    download 下载/upload 上传,
    refresh 刷新/synchronize 同步
    update 更新/revert 复原,
    lock 锁定/unlock 解锁
    check out 签出/check in 签入,
    submit 提交/commit 交付
    push 推/pull 拉,
    expand 展开/collapse 折叠
    begin 起始/end 结束,
    start 开始/finish 完成
    enter 进入/exit 退出,
    abort 放弃/quit 离开
    obsolete 废弃/depreciate 废旧,
    collect 收集/aggregate 聚集
```

9） 常量命名全部大写，单词间用下划线隔开，力求语义表达完整清楚，不要嫌名字长。

正确【✔】 
```text
     MAX_STOCK_COUNT
```

错误【❌】
```text
    MAX_COUNT
```

6、javaScript中只允许使用单引号，标签中统一使用双引号，标签模板必须使用字符串模板

```html
<script>
  let el = `<div class="dom"></div>`
  let str = ''
</script>
```


7、标签的 Props 应该有统一的顺序，依次为指令、属性和事件，如果写内联样式，放在最后

```vue
    <my-component
      v-if="if"
      v-show="show"
      v-model="value"
      ref="ref"
      :key="key"
      :text="text"
      @input="onInput"
      @change="onChange"
      style="font-size: 14px;"
    />
```

8、所有的事件以on-开始，事件的方法以handle-开始

