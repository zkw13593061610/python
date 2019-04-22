## ckeditor：

步骤：

```py
1.创建一个文件夹：用pycharm打开
2.npm init 创建一个包说明文件   package.json
3.把编辑器功能的组件 放到 package。json作为以来安装
		
 安装 webpack 以及webpack的依赖项
 配置webpack的选项
 写自己的配置文件
 写自己的入口文件
 运行webpack命令
 修改配置
 按照webpack制定的output 路径和文件名，输入相应的编译好的文件
 按照规范引入js
 动态的添加或删除相应的功能
 删除：把相应的组件和依赖删掉
 添加：到  features  找到相应的路径 按照步骤更改.创建一个文件夹：用pycharm打开
```

步骤：

- 1.创建一个文件夹：用pycharm打开

- 2.npm init 创建一个包说明文件，package.json

- 3.把编辑器功能的组件 放到 package。json作为以来安装

  ```py
  "dependencies": {
      // ...
  
      "@ckeditor/ckeditor5-adapter-ckfinder": "^x.y.z",
      "@ckeditor/ckeditor5-autoformat": "^x.y.z",
      "@ckeditor/ckeditor5-basic-styles": "^x.y.z",
      "@ckeditor/ckeditor5-block-quote": "^x.y.z",
      "@ckeditor/ckeditor5-easy-image": "^x.y.z",
      "@ckeditor/ckeditor5-editor-classic": "^x.y.z",
      "@ckeditor/ckeditor5-essentials": "^x.y.z",
      "@ckeditor/ckeditor5-heading": "^x.y.z",
      "@ckeditor/ckeditor5-image": "^x.y.z",
      "@ckeditor/ckeditor5-link": "^x.y.z",
      "@ckeditor/ckeditor5-list": "^x.y.z",
      "@ckeditor/ckeditor5-paragraph": "^x.y.z",
      "@ckeditor/ckeditor5-theme-lark": "^x.y.z",
      "@ckeditor/ckeditor5-upload": "^x.y.z"
  
      // ...
  }
  ```

- 4.安装 webpack 以及webpack的依赖项

  ```py
  npm install --save \
      @ckeditor/ckeditor5-dev-webpack-plugin \
      @ckeditor/ckeditor5-dev-utils \
      postcss-loader \
      raw-loader \
      style-loader \
      webpack@4 \
      webpack-cli@3 \
  ```

- 5.写webpack的配置项：

  ```py
  const CKEditorWebpackPlugin = require( '@ckeditor/ckeditor5-dev-webpack-plugin' );
  const { styles } = require( '@ckeditor/ckeditor5-dev-utils' );
  const path=require('path')
  module.exports = {
  	entry:'./abc.js'   写入口文件地址
  	output:{
          path: path.resolve(__dirname, 'dist'),
          filename: 'bundle.js'   写出口文件
  	}
      plugins: [
          // ...
  
          new CKEditorWebpackPlugin( {
              // See https://ckeditor.com/docs/ckeditor5/latest/features/ui-language.html
              language: 'pl'
          } )
      ],
  
      module: {
          rules: [
              {
                  // Or /ckeditor5-[^/]+\/theme\/icons\/[^/]+\.svg$/ if you want to limit this loader
                  // to CKEditor 5 icons only.
                  test: /\.svg$/,
  
                  use: [ 'raw-loader' ]
              },
              {
                  // Or /ckeditor5-[^/]+\/theme\/[\w-/]+\.css$/ if you want to limit this loader
                  // to CKEditor 5 theme only.
                  test: /\.css$/,
                  use: [
                      {
                          loader: 'style-loader',
                          options: {
                              singleton: true
                          }
                      },
                      {
                          loader: 'postcss-loader',
                          options: styles.getPostCssConfig( {
                              themeImporter: {
                                  themePath: require.resolve( '@ckeditor/ckeditor5-theme-lark' )
                              },
                              minify: true
                          } )
                      },
                  ]
              }
          ]
      }
  };
  ```

- 6.写自己的配置文件：app.js   可以把配置文件放在一个文件夹里，比如 "src/app.js"

  ```py
  import ClassicEditorBase from '@ckeditor/ckeditor5-editor-classic/src/classiceditor';
  import EssentialsPlugin from '@ckeditor/ckeditor5-essentials/src/essentials';
  import UploadAdapterPlugin from '@ckeditor/ckeditor5-adapter-ckfinder/src/uploadadapter';
  import AutoformatPlugin from '@ckeditor/ckeditor5-autoformat/src/autoformat';
  import BoldPlugin from '@ckeditor/ckeditor5-basic-styles/src/bold';
  import ItalicPlugin from '@ckeditor/ckeditor5-basic-styles/src/italic';
  import BlockQuotePlugin from '@ckeditor/ckeditor5-block-quote/src/blockquote';
  import EasyImagePlugin from '@ckeditor/ckeditor5-easy-image/src/easyimage';
  import HeadingPlugin from '@ckeditor/ckeditor5-heading/src/heading';
  import ImagePlugin from '@ckeditor/ckeditor5-image/src/image';
  import ImageCaptionPlugin from '@ckeditor/ckeditor5-image/src/imagecaption';
  import ImageStylePlugin from '@ckeditor/ckeditor5-image/src/imagestyle';
  import ImageToolbarPlugin from '@ckeditor/ckeditor5-image/src/imagetoolbar';
  import ImageUploadPlugin from '@ckeditor/ckeditor5-image/src/imageupload';
  import LinkPlugin from '@ckeditor/ckeditor5-link/src/link';
  import ListPlugin from '@ckeditor/ckeditor5-list/src/list';
  import ParagraphPlugin from '@ckeditor/ckeditor5-paragraph/src/paragraph';
  
  export default class ClassicEditor extends ClassicEditorBase {}
  
  ClassicEditor.builtinPlugins = [
      EssentialsPlugin,
      UploadAdapterPlugin,
      AutoformatPlugin,
      BoldPlugin,
      ItalicPlugin,
      BlockQuotePlugin,
      EasyImagePlugin,
      HeadingPlugin,
      ImagePlugin,
      ImageCaptionPlugin,
      ImageStylePlugin,
      ImageToolbarPlugin,
      ImageUploadPlugin,
      LinkPlugin,
      ListPlugin,
      ParagraphPlugin
  ];
  
  ClassicEditor.defaultConfig = {
      toolbar: {
          items: [
              'heading',
              '|',
              'bold',
              'italic',
              'link',
              'bulletedList',
              'numberedList',
              'imageUpload',
              'blockQuote',
              'undo',
              'redo'
          ]
      },
      image: {
          toolbar: [
              'imageStyle:full',
              'imageStyle:side',
              '|',
              'imageTextAlternative'
          ]
      },
      language: 'en'
  };
  ```

- 写自己的入口文件：abc.js

  ```py
  import ClassicEditor from './src/app.js';
  
  ClassicEditor
      // Note that you do not have to specify the plugin and toolbar configuration — using defaults from the build.
      .create( document.querySelector( '#editor' ) )
      .then( editor => {
          console.log( 'Editor was initialized', editor );
      } )
      .catch( error => {
          console.error( error.stack );
      } );
  ```

- 修改package.json  的script

  ```py
  "scripts": {
      "build": "webpack --mode development"
    },
  ```

- 运行命令  npm run build  生成一个dist文件夹   里面有个 bundle.js  在创建一个页面，引入即可