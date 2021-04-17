# Leetcode PHP
Solution of Leetcode on PHP

## EASY LEVEL

#### 1. Two Sum
<details>
  <summary>show solution</summary>
  
```php
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
</details><br/>


#### 7. Reverse Integer
<details>
  <summary>show solution</summary>
  
```php
function reverse($x) {
    if (is_int($x) === false || $x === null || $x === 0) return 0;
    $res = $x < 0 ? -abs(strrev($x)) : (int)strrev($x);
    if ($res < -2147483648 || $res >  2147483647) return 0;
    return $res;
}
```
</details><br/>


#### 9. Palindrome Number
<details>
  <summary>show solution</summary>
  
```php
function isPalindrome($x) {
    return $x == strrev($x);
}
```
</details><br/>


#### 13. Roman to Integer
<details>
  <summary>show solution</summary>
  
```php
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
</details><br/>


#### 14. Longest Common Prefix
<details>
  <summary>show solution</summary>
  
```php
function longestCommonPrefix($strs) {
    $first = array_shift($strs);
    $first = str_split($first);
    $length = count($first);
    $prefix = '';
    for($i=0;$i<=$length;$i++){
        foreach($strs as $str){
            if(!isset($str[$i])){
                break 2;
            }
            if($str[$i] != $first[$i]){
                break 2;
            }
        }
        
        $prefix .=$first[$i];
    }
    return $prefix;
}
```
</details><br/>

#### 20. Valid Parentheses
<details>
  <summary>show solution</summary>
  
```php
function isValid($s) {
    $s = trim($s);
    if (!$s) {
      return true;
    }
    if (strlen($s) === 1) {
      return false;
    }

    $brackets = [
      '[' => ']',
      '(' => ')',
      '{' => '}',
    ];

    for ($stack = [], $length = strlen($s), $i = 0; $i < $length; $i++) {
      $symbol = $s[$i];
      if (array_key_exists($symbol, $brackets)) {
        $stack[] = $symbol;
      } else {
        $lastInStack = array_pop($stack);
        if (!isset($brackets[$lastInStack]) || $symbol !== $brackets[$lastInStack]) {
          return false;
        }
      }
    }
    return (count($stack) === 0) ? true : false;
}
```
</details><br/>


#### 21. Merge Two Sorted Lists
<details>
  <summary>show solution</summary>
  
```php
class Solution {

    private $vals = [];
    
    /**
     * @param ListNode $l1
     * @param ListNode $l2
     * @return ListNode
     */
    function mergeTwoLists($l1, $l2) {
       $this->iterate($l1, $l2);
        $root = $node = NULL;
        if($this->vals){
            $root = $node = new ListNode(array_pop($this->vals));
        }
        while(!empty($this->vals)){
            $node->next = new ListNode(array_pop($this->vals));
            $node = $node->next;
        }
        return $root;
    }
    
    function iterate($l1, $l2){
        if(!is_null($l1) && !is_null($l2)){
            if($l1->val<=$l2->val){
                array_unshift($this->vals, $l1->val);
                $l1 = $l1->next;
            }
            else{
                array_unshift($this->vals, $l2->val);
                $l2 = $l2->next;
            }
        }
        else if(!is_null($l1)){
            array_unshift($this->vals,$l1->val);
            $l1 = $l1->next;
        }
        else if(!is_null($l2)){
            array_unshift($this->vals,$l2->val);
            $l2 = $l2->next;
        }
        else if (is_null($l1) && is_null($l2)){
            return;
        }
        $this->iterate($l1, $l2);
    }
    
}
```
</details><br/>


#### 26. Remove Duplicates from Sorted Array
<details>
  <summary>show solution</summary>
  
```php
function removeDuplicates(&$nums) {
    $lenght = count($nums);
    if ( $lenght === 0 ) return 0;
    $i = 0;
    for ( $j = 1; $j < $lenght ; $j ++ ) {
        if ( $nums[$j] != $nums[$i] ) {
            $i ++;
            $nums[$i] = $nums[$j];
        }
    }
    return $i + 1;
}
```
</details><br/>


#### 27. Remove Element
<details>
  <summary>show solution</summary>
  
```php
function removeElement(&$nums, $val) {
    foreach ($nums as $k => $v) {
        if ( $v === $val ) {
            unset($nums[$k]);
        }
    }
    return count($nums);
}
```
</details><br/>


#### 28. Implement strStr()
<details>
  <summary>show solution</summary>
  
```php
function strStr($haystack, $needle) {
            
    if(strlen($needle) == 0) return 0;
    if(strlen($haystack) == 0) return -1;
    
    if(strlen($haystack) == 1 && strlen($needle) == 1){
        if($haystack[0] == $needle[0]){
            return 0;
        }
    }
    
    for($i = 0; $i < strlen($haystack) - strlen($needle) + 1; $i++){
        if($needle === substr($haystack, $i, strlen($needle))){
            return $i;
        }
    }
    return -1; 
    
}
```
</details><br/>


#### 35. Search Insert Position
<details>
  <summary>show solution</summary>
  
```php
function searchInsert($nums, $target) {
    for($i = 0; $i < count($nums) && $nums[$i] <= $target; $i++) {
        if ($nums[$i] == $target) {
            return $i;
        }
    }
    return $i; 
}
```
</details><br/>


#### 53. Maximum Subarray
<details>
  <summary>show solution</summary>
  
```php
function maxSubArray($nums) {
    $sum = $nums[0];
    $max = $sum;
    for($i = 1, $n = count($nums); $i < $n; $i ++){
        $sum = $nums[$i] > $nums[$i]+$sum ? $nums[$i] : $nums[$i]+$sum;
        $max = $max > $sum ? $max : $sum;
    }
    return $max;
}
```
</details><br/>


#### 58. Length of Last Word
<details>
  <summary>show solution</summary>
  
```php
function lengthOfLastWord($s) {
    $length = 0;
    $first = false;
    for ($i = strlen($s) - 1; $i >= 0; $i--) {
        if ($s[$i] == ' ' && $first) {
            return $length;
        } else if ($s[$i] != ' ') {
            $first = true;
            $length++;
        }
    }
    return $length;
}
```
</details><br/>
    

#### 66. Plus One
<details>
  <summary>show solution</summary>
  
```php
function plusOne($digits) {
    $carry=1;
    for($i = count($digits)-1; $i>=0; $i--){
        $temp = ($digits[$i]+$carry)%10;
        $carry = intval(($digits[$i]+$carry)/10);
        $digits[$i] = $temp;
    }
    if($carry == 0) return $digits;
    else{
        $res = array_fill(0, count($digits) + 1, 0);
        $res[0] = $carry;
        for($i=0; $i<count($digits); $i++){
            $res[$i+1] = $digits[$i];
        }
        return $res;
    }
}
```
</details><br/>


#### 67. Add Binary
<details>
  <summary>show solution</summary>
  
```php
function addBinary($a, $b) {
    $sb = "";
    $i = strlen($a) - 1;
    $j = strlen($b) - 1;
    $carry = 0;
    while($i >= 0 || $j >= 0 || $carry > 0)
    {
        $sum = $carry;
        if($i >= 0) $sum += ord($a[$i--]) - ord('0');
        if($j >= 0) $sum += ord($b[$j--]) - ord('0');
        $sb .= chr($sum % 2 + ord('0'));
        $carry = intval($sum / 2);
    }
    return strrev($sb);
}
```
</details><br/>

#### 69. Sqrt(x)
<details>
  <summary>show solution</summary>
  
```php
function mySqrt($x) {
    return (int)sqrt($x);
}
```
</details><br/>


#### 70. Climbing Stairs
<details>
  <summary>show solution</summary>
  
```php
function climbStairs($n) {
    if ($n == 2) 
        return 2;
    else if ($n == 1)
        return 1;
    
    $a = 0;
    $b = 1;
    $c = 0;
    for ($i = 0; $i < $n; $i++)
    {
        $c = $a + $b;
        $a = $b;
        $b = $c;
    }
    return $c;  
}
```
</details><br/>

#### 83. Remove Duplicates from Sorted List
<details>
  <summary>show solution</summary>
  
```php
function deleteDuplicates($head) {
    if($head==null || $head->next == null) return $head;
    $prev = $head;
    $node = $head->next;
    while( $node!= null){
        if($node->val != $prev->val){
            $prev = $node;
            $node = $node->next;
        }else{
            $prev->next = $node->next;
            $node = $node->next;
        }
    }
    return $head;
}
```
</details><br/>


#### 88. Merge Sorted Array
<details>
  <summary>show solution</summary>
  
```php
function merge(&$nums1, $m, $nums2, $n) {
    $i = $m-1; $j = $n-1; $x = count($nums1);
    for($c = count($nums1) - 1; $c >= 0; $c--) {
        if ($i>=0 && $j>=0 && $nums1[$i] >= $nums2[$j]) {
            $nums1[$c] = $nums1[$i];
            --$i;
        } else if ($i>=0 && $j>=0 && $nums2[$j] > $nums1[$i]) {
            $nums1[$c] = $nums2[$j];
            --$j;
        } else if($i<0 && $j>=0) {
            $nums1[$c] = $nums2[$j];
            --$j;
        } else {
            $nums1[$c] = $nums1[$i];
            --$i;
        }
    }
}
```
</details><br/>


#### 100. Same Tree
<details>
  <summary>show solution</summary>
  
```php
function isSameTree($p, $q) {
    if($p == null && $q == null)
        return true;
    
    if($p == null || $q == null)
        return false;
    
    return ($p->val == $q->val) && self::isSameTree($p->left, $q->left) && self::isSameTree($p->right,$q->right);   
}
```
</details><br/>

#### 101. Symmetric Tree
<details>
  <summary>show solution</summary>
  
```php
class Solution {

    /**
     * @param TreeNode $root
     * @return Boolean
     */
    function isSymmetric($root) {
        //1. Top empty, return symmetric!
        if($root == null) return true;
        
        //2. Recursion method: Single null always symm, so just put kids in.
        return self::helper($root->left, $root->right);
    }
    
    function helper($left, $right){
        //3. Both must be null, or false
        if($left==null || $right==null)
            return $left==$right;
        
        //4. Check values and next level of children
        return $left->val==$right->val && self::helper($left->left, $right->right) && self::helper($left->right, $right->left);
    }
}
```
</details><br/>

#### 104. Maximum Depth of Binary Tree
<details>
  <summary>show solution</summary>
  
```php
function maxDepth($root) {
    if($root == null) return 0;
    return 1 + max(self::maxDepth($root->left), self::maxDepth($root->right) );   
}
```
</details><br/><br/>


## MEDIUM LEVEL

#### 2. Add Two Numbers
<details>
  <summary>show solution</summary>
  
```php
function addTwoNumbers($l1, $l2) {
    $node = new ListNode($this->res + $l1->val + $l2->val);
    if( $this->res = intval($node->val > 9) ) { 
        $node->val -=10;
    }
    $node->next = (!$this->res && is_null($l1->next) && is_null($l2->next) ) ?
        null : $this->addTwoNumbers($l1->next,$l2->next);
        
    return $node;
}
```
</details><br/><br/>


## HARD LEVEL

    
#### 65. Valid Number 
<details>
  <summary>show solution</summary>
  
```php
function isNumber($s) {
    return $s === '' || (count($s) === 1 && !is_numeric($s)) ? false : true;
}
```
</details><br/>
