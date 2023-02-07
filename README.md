### webpack 使用 unocss-preset-scalpel

1.  安装依赖

    ```bash
    npm install -D  unocss @unocss/webpack unocss-preset-scalpel
    ```

2.  配置 webpack 插件

    ```javascript
    // webpack.config.js
    const UnoCSS = require("@unocss/webpack").default;

    module.exports = {
      plugins: [UnoCSS()],
      // for Webpack 4
      css: {
        extract: {
          filename: "[name].[hash:9].css",
        },
      },
      // for Webpack 5
      optimization: {
        realContentHash: true,
      },
    };

    // vue.config.js
    module.exports = {
      configureWebpack: {
        plugins: [UnoCSS()],
      },
    };

    // vue.config.js use chainWebpack
    module.exports = {
      chainWebpack: (config) => {
        config.plugin("unocss").use(UnoCSS);
      },
    };
    ```

3.  添加配置文件

    ```bash
      touch uno.config.js
    ```

    ```javascript
    /* eslint-disable import/no-extraneous-dependencies */
    import { defineConfig } from "unocss";
    import { presetScalpel } from "unocss-preset-scalpel";

    export default defineConfig({
      presets: [presetScalpel({})],
    });
    ```

4.  主入口引入 css
    ```ts
    import "uno.css";
    ```
