# Leetcode PHP
Solution of Leetcode on PHP

## Easy level

#### 1. Two Sum
<details>
  <summary>show solution</summary>
  
```
function twoSum($nums, $target) {
  foreach ($nums as $key => $val) {
    unset($nums[$key]);
    $nextKey = array_search(($target - $val), $nums);
    if ($nextKey) {
      return [$key, $nextKey];
    }
  }
  return [];
}
```
</details>

#### 7. Reverse Integer
<details>
  <summary>show solution</summary>
  
```
function reverse($x) {
	if (is_int($x) === false || $x === null || $x === 0) return 0;
	$res = $x < 0 ? -abs(strrev($x)) : (int)strrev($x);
	if ($res < -2147483648 || $res >  2147483647) return 0;
	return $res;
}
```
</details>

#### 9. Palindrome Number
<details>
  <summary>show solution</summary>
  
```
function isPalindrome($x) {
	return $x == strrev($x);
}
```
</details>

#### 13. Roman to Integer
<details>
  <summary>show solution</summary>
  
```
function romanToInt($s) {
   $map = [
		'I' => 1,
		'V' => 5,
		'X' => 10,
		'L' => 50,
		'C' => 100,
		'D' => 500,
		'M' => 1000,

		// special for diy
		'v' => 4,
		'x' => 9,
		'l' => 40,
		'c' => 90,
		'd' => 400,
		'm' => 900,
	];

	$special = [
		'IV' => 'v',
		'IX' => 'x',
		'XL' => 'l',
		'XC' => 'c',
		'CD' => 'd',
		'CM' => 'm',
	];

	foreach ($special as $k => $v) {
		$s = str_replace($k, $v, $s);
	}

	$number = 0;
	$s = str_split($s);
	foreach ($s as $item) {
		$number += $map[$item];
	}

	return $number;
}
```
</details>
