# Unlimited $replyIn
Set the variable `duration` to a positive integer. Keep in mind that node restarts can break this, so for things like a reminder command or a giveaway command, it’s better to use an [`$onMessageDelete` loop](../../../Loops-in-BDFD/blob/main/%24onMessageDelete%20Loop.md) that does something specific for specified timestamps.
```js
$var[duration;123456]

$if[$var[duration]>2400] $eval[$replaceText[$calculate[10**($var[duration]/2400)-1];9;$$c[]replyIn[40m\]]] $endif
$replyIn[$calculate[$var[duration]%2400+1]s]
```
