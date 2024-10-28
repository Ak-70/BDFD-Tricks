# Eval in eval
```php
$eval[$replaceText[$message;$$c[]eval[;$$c[]var[eval_i\;$$c[]sum[0$$c[]var[eval_i\]\;1\]\]$$c[]var[eval_$$c[]var[eval_i\]\;]]
$if[$var[eval_i]!=] $eval[$replaceText[$sub[1e$min[$var[eval_i];38];1];9;$$c[]var[eval_j\;$$c[]sum[0$$c[]var[eval_j\]\;1\]\]$$c[]var[eval_$$c[]var[eval_j\]\]\]] $endif
```
This works by evaluating the code in a separate eval. If you use this code, you can only use eval in eval 38 times, and the other ones will just be ignored.

# Need a higher limit?
This code does not have the limit of 38. This was achieved by changing the [`$sum` loop](../../../Loops-in-BDFD/blob/main/Run%20X%20Times/%24sum.md) to an [advanced loop](../../../Loops-in-BDFD/blob/main/Run%20X%20Times/Advanced%20method.md).
```php
$eval[$replaceText[$message;$$c[]eval[;$$c[]var[eval_i\;$$c[]sum[0$$c[]var[eval_i\]\;1\]\]$$c[]var[eval_$$c[]var[eval_i\]\;]]
$if[$var[eval_i]!=] $eval[$replaceText[$sub[1e$min[$var[eval_i];38];1];9;$$c[]var[eval_j\;$$c[]sum[0$$c[]var[eval_j\]\;1\]\]$$c[]var[eval_$$c[]var[eval_j\]\]\]] $endif

$if[$eval[eval_i]!=]
    $var[eval_c;$$c[]var[eval_j\;$$c[]sum[0$$c[]var[eval_j\]\;1\]\]$$c[]var[eval_$$c[]var[eval_j\]\]]
    $var[eval_x;$sum[1e$calculate[$var[eval_i]**0.125+1];-1]]
    $eval[$repeatMessage[3;$$c[]var[eval_x\;$$c[]replaceText[$$c[]var[eval_x\]\;9\;$$c[]var[eval_x\]\]\]]]
    $eval[$replaceText[$cropText[$var[eval_x];$var[eval_i];];9;$var[eval_c]]]
$endif
```

# Actual usage example
```php
!eval
$textSplit[$userRoles[$authorID];$url[decode;%0A]]
$eval[$$c[]roleGrant[$$c[]authorID\;-$$c[]roleID[$joinSplitText[\]\;-$$c[]roleID[]\]\]]
```
This should in theory remove all of the roles of the person that uses it.
