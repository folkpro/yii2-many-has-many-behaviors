Yii2 ManyHasManyBehavior
===========================

Installation
------------
The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

Either run

```
composer require folkpro/yii2-many-has-many-behaviors
```
or add

```json
"folkpro/yii2-many-has-many-behaviors" : "*"
```

to the require section of your application's `composer.json` file.

Usage
-----

1. In your model, add the behavior and configure it
```
public function behaviors()
{
    return [
        [
            'class' => \folkpro\manyhasmanybehaviors\ManyHasManyBehavior::className(),
            'relations' => [
                 'tags' => 'tag_items',                  
             ],
        ],
    ];
}
```

2. In your model, add the relation, for example:
```
public function getTags()
{
    return $this->hasMany(Tag::className(), ['id' => 'tag_id'])->viaTable('post_has_tag', ['post_id' => 'id']);
}
```

3. In your model, add validation rules for the attributes created by the behavior, for example:
```
public function rules()
{
    return [
        [['tag_list'], 'safe']
    ];
}
```

4. In your view, create form fields for the attributes

***

<i>Web development here:</i>  
[ManyHasManyBehavior](http://fancode.ru/post/yii2-behaviors-many-to-many)