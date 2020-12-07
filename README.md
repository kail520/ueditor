百度UEditor
===========

### 安装
Either run

```
$ php composer.phar require kail520/ueditor "*"
```

or add

```
"kail520/ueditor": "*"
```

to the ```require``` section of your `composer.json` file.

### 应用

controller:  

```
public function actions()
{
    return [
        'upload' => [
            'class' => 'kail520\\ueditor\UEditorAction',
        ]
    ];
}
```

view:  

```
echo \kail520\\ueditor\UEditor::widget([]);
```

或者：

```
echo $form->field($model,'colum')->widget('kail520\ueditor\UEditor',[]);
```
### 说明
 `ueditor`只支持2种语言，`en-us`和`zh-cn`,默认跟随系统语言 `Yii::$app->language`,可以通过2种方式设置，1.修改系统语言，在`main.php`(高级版) 或者`web.php`(基础版)添加`'language' => 'zh-CN',`。2.实例化的时候配置语言选项，见下边配置
 
### 配置相关

##### 编辑器相关配置，请在`view` 中配置，参数为`clientOptions`，比如定制菜单，编辑器大小等等，具体参数请查看[UEditor官网文档](http://fex-team.github.io/ueditor/)。

简单实例:  
```php
use \kail520\ueditor\UEditor;
echo UEditor::widget([
    'clientOptions' => [
        //编辑区域大小
        'initialFrameHeight' => '200',
        //设置语言
        'lang' =>'en', //中文为 zh-cn
        //定制菜单
        'toolbars' => [
            [
                'fullscreen', 'source', 'undo', 'redo', '|',
                'fontsize',
                'bold', 'italic', 'underline', 'fontborder', 'strikethrough', 'removeformat',
                'formatmatch', 'autotypeset', 'blockquote', 'pasteplain', '|',
                'forecolor', 'backcolor', '|',
                'lineheight', '|',
                'indent', '|'
            ],
        ]
]);
```

简单实例:  
```php
public function actions()
{
    return [
        'upload' => [
            'class' => 'kail520\ueditor\UEditorAction',
            'config' => [
                "imageUrlPrefix"  => "http://www.baidu.com",//图片访问路径前缀
                "imagePathFormat" => "/upload/image/{yyyy}{mm}{dd}/{time}{rand:6}" //上传保存路径
                "imageRoot" => Yii::getAlias("@webroot"),
            ],
        ]
    ];
}
```
