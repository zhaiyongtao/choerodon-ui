---
order: 5
title: Customize Theme
---

Ant Design allows you to customize some basic design aspects in order to meet the needs of UI diversity from business and brand, including primary color, border radius, border color, etc.

![](https://zos.alipayobjects.com/rmsportal/zTFoszBtDODhXfLAazfSpYbSLSEeytoG.png)

## Less variables

We are using [Less](http://lesscss.org/) as the development language for styling. A set of less variables are defined for each design aspect that can be customized to your needs.

- [Default Variables](https://github.com/ant-design/ant-design/blob/master/components/style/themes/default.less)

Please report an issue if the existing list of variables is not enough for you.

## How to do it

We recommend [modifyVars](http://lesscss.org/usage/#using-less-in-the-browser-modify-variables) to override the default values of the variables. There are two ways to achieve it in practice.

### 1) Using `theme` property (recommended way)

Specify the `theme` property in the `package.json` or `.webpackrc` file, whose value can be either an object or the path to a JS file that contains the custom values of specific variables:
- example of directly specifying the custom values as an object:
```js
"theme": {
  "primary-color": "#1DA57A",
},
```

Note:

- Importing styles from less files is necessary.
  - If you import styles by specifying the `style` option of [babel-plugin-import](https://github.com/ant-design/babel-plugin-import), change it from `'css'` to `true`, which will import the `less` version of choerodon-ui.
  - If you import styles from `'choerodon-ui/dist/choerodon-ui.css'`, change it to `choerodon-ui/dist/choerodon-ui.less`.
- When using `dva-cli@0.7.0+`, you should add the `theme` block to [.roadhogrc](https://github.com/dvajs/dva-example-user-dashboard/commit/d6da33b3a6e18eb7f003752a4b00b5a660747c31) instead of `package.json`.
- If you want to override `@icon-url`, the value must be contained in quotes like `"@icon-url": "'your-icon-font-path'"` ([A fix sample](https://github.com/visvadw/dvajs-user-dashboard/pull/2)).

### 2) Overriding Less variables (alternative way)

Override variables via less definition files.

Create a standalone less file like the one below, and import it in your project.

   ```css
   @import "~choerodon-ui/dist/choerodon-ui.less";   // import official less entry file
   @import "your-theme-file.less";   // override variables here
   ```

Note: This way will load the styles of all components, regardless of your demand, which cause `style` option of `babel-plugin-import` not working.

## Related Articles

- [How to Customize Ant Design with React & Webpack… the Missing Guide](https://medium.com/@GeoffMiller/how-to-customize-ant-design-with-react-webpack-the-missing-guide-c6430f2db10f)
- [Theming Ant Design with Sass and Webpack](https://gist.github.com/Kruemelkatze/057f01b8e15216ae707dc7e6c9061ef7)
