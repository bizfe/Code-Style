# Reactjs代码规范

## 说明
此规范根据[eslint](http://eslint.org/), 和[eslint-plugin-react](https://github.com/yannickcr/eslint-plugin-react)提供的rules进行检查。
具体配置见[eslintrc](https://github.com/bizfe/Code-Style/blob/master/react/eslintrc)。

可以将此配置与业务项目的eslintrc进行merge，已达到Reactjs代码检查的目的。

**Demo:** [reactjs-boilerplate](https://github.com/bizfe/reactjs-boilerplate)

注：若jsx代码文件后缀不是.js，在配置eslint时，需要指明: eslint --ext=js,jsx your-folder

-

## 1. jsx语法必须使用tab缩进，父子标签缩进一个tab
**Rule:** [jsx-indent](https://github.com/yannickcr/eslint-plugin-react/blob/master/docs/rules/jsx-indent.md)

**备注:** 一个tab对应4个空格

### Wrong
```jsx
// 2 spaces indentation
<App>
		<Hello />
</App>

// no indentation
<App>
<Hello />
</App>
```
### Right
```jsx 
<App>
	<Hello />
</App>	
```

## 2. jsx标签存在子标签的情况使用闭合标签，否则应该自闭合

**Rule:** [self-closing-comp](https://github.com/yannickcr/eslint-plugin-react/blob/master/docs/rules/self-closing-comp.md)

### Wrong
```jsx
//多余的闭合标签
<Hello name="John"></Hello>;
```

### Right
```jsx 
//html原生标签按着html规范书写
<div className="content"></div>	

//right
<Hello name="John" />;

//right
<Hello name="John"><img src="picture.png" /></Hello>;
```

## 3. jsx自定义标签上的属性一行不应该超过3个
**Rule:** [jsx-max-props-per-line](https://github.com/yannickcr/eslint-plugin-react/blob/master/docs/rules/jsx-max-props-per-line.md)

### Wrong
```jsx

//超过3个
<Hello {...this.props} firstName="John" lastName="Smith"  tel={5555555} />;

//不超过3个不应换行
<Hello
  firstName="John" lastName="Smith"
  tel={5555555}
/>;
```

### Right
```jsx 
<Hello firstName="John" lastName="Smith" />;

<Hello firstName="John" lastName="Smith" tel={5555555} />;

<Hello  {...this.props}  firstName="John" lastName="Smith" 
	tel={5555555} />;
```
## 4. jsx自定义标签属性的大括号之间两边不应存在空格
**Rule:** [jsx-curly-spacing](https://github.com/yannickcr/eslint-plugin-react/blob/master/docs/rules/jsx-curly-spacing.md)

### Wrong
```jsx
<Hello name={ firstname } />;
<Hello name={ firstname} />;
<Hello name={firstname } />;
```

### Right
```jsx 
<Hello name={firstname} />;
<Hello name={{ firstname: 'John', lastname: 'Doe' }} />;
```
## 5. jsx标签属性值，使用双引号作为属性值的界定符

**Rule:** [jsx-quotes](http://eslint.org/docs/rules/jsx-quotes)

**描述:** jsx标签属性值，可以使用双引号或单引号作为属性值的界定符。但是当要使用`"`或`'`作为属性值时你必须使用如下方式
```jsx
<a b="'" />
<a b='"' />
```
为了和html标签属性保持统一，此规范默认使用双引号作为属性值的界定符。

### Wrong
```jsx
<a b='c' />

```

### Right
```jsx 
<a b="c" />
<a b='"' />
```

## 6. jsx标签属性与属性值之间不应存在空格

**Rule:** [jsx-equals-spacing](https://github.com/yannickcr/eslint-plugin-react/blob/master/docs/rules/jsx-equals-spacing.md)

### Wrong
```jsx
<Hello name = {firstname} />;
<Hello name ={firstname} />;
<Hello name= {firstname} />;
```

### Right
```jsx 
<Hello name={firstname} />;
<Hello name />;
<Hello {...props} />;
```

## 7. jsx标签属性换行后需缩进一个tab

**Rule:** [jsx-indent-props](https://github.com/yannickcr/eslint-plugin-react/blob/master/docs/rules/jsx-indent-props.md)

### Wrong
```jsx
// 2 spaces indentation
<Hello
  firstName="John"
/>

// no indentation
<Hello
firstName="John"
/>

```

### Right
```jsx 
// 1 tab indentation
<Hello
  firstName="John"
/>
```

## 8. 循环中的标签必须加上key属性

**Rule:** [jsx-key](https://github.com/yannickcr/eslint-plugin-react/blob/master/docs/rules/jsx-key.md)

### Wrong
```jsx
let data = [<Hello />, <Hello />, <Hello />];

data.map(x => <Hello>x</Hello>);

```

### Right
```jsx 
let data = [<Hello />, <Hello />, <Hello />];

data.map((x, i) => <Hello  key={i}>x</Hello>);
```