# Leetcode PHP
Solution of Leetcode on PHP

# Easy level

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
