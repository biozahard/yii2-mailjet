# Mailjet Client supporting v3.1

## Create Mailjet Account

mailjet.com

## Install

```
composer require biozahard/yii2-mailjet
```
or add it to your composer.json in the require section
```
"biozahard/yii2-mailjet": "*",
```

## Setup
add/replace this in your config under the components key.
```
'components' => [
  'mailer' => [
    'class' => 'biozahard\mailjet\Mailer',
    'apikey' => 'yourApiKey',
    'secret' => 'yourSecret',
  ],
],
```


## Example

```
Yii::$app->mailer->compose('signup', ['user' => $user])
->setTo($user->email)
->setFrom([Yii::$app->params['noReplyMailAddress'] => Yii::$app->name])
->setSubject('Signup success')
->send();
```

## Setup Event Tracking
Write the tracking item to the mailer config.
```
'components' => [
  'mailer' => [
    'class' => 'biozahard\mailjet\Mailer',
    'apikey' => 'yourApiKey',
    'secret' => 'yourSecret',
    'tracking' => [
      'bounce' => 'http://yoururl.com/tracking?event=bounce',
    ],
  ],
],
```
To activate this url you must run this command at one time.
```
Yii::$app->mailer->activateTracking();
```
