# 3. [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/#/description)

## Description

Given a string, find the length of the **longest substring** without repeating characters.

**Examples:**

Given `"abcabcbb"`, the answer is `"abc"`, which the length is 3.

Given `"bbbbb"`, the answer is `"b"`, with the length of 1.

Given `"pwwkew"`, the answer is `"wke"`, with the length of 3. Note that the answer must be a **substring**, `"pwke"` is a subsequence and not a substring.

## My Solution

```javascript
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLongestSubstring = function(s) {
  var N = s.length, head = 0, i = 0;
  var obj = {};
  var longest = 0;
  
  while (i < N) {
    var c = s.charAt(i);
    if (obj.hasOwnProperty(c)) {
      var m = obj[c];
      if (m >= head) {
        if (i - head > longest) {
          longest = i - head;
        }
      
        head = m + 1;
      }
    }
    
    obj[c] = i;
    
    i++;
  }
  
  if (i - head > longest) {
    longest = i - head;
  }
  
  return longest;
};
```

Runtime: **248 ms**

## Sample 136 ms submission

```javascript
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLongestSubstring = function(s) {
  var sLen = s.length;
  var subLen = 0, subMaxLen = 0;
  var subMinIndex = 0;
  var subString = '', longestSubString = '';
  var rptPos = 0;

  if (sLen === 0) {
    return 0;
  }

  subString = s[0];
  subLen = 1;
  for (var i = 1; i < sLen; i++) {
    rptPos = subString.indexOf(s[i]);
    if (rptPos === -1) { //当前字串没有遇到重复字符
      subString += s[i];
      subLen++;
    } else { //字串遇到第一个重复字符
      if (subLen > subMaxLen) {
        subMaxLen = subLen;
        longestSubString =  subString;
      }

      if (i === sLen) { // i = sLen
        return subMaxLen;
      }

      subMinIndex +=  rptPos + 1;
      subLen = i + 1 - subMinIndex;
      subString = s.substr(subMinIndex, subLen);
    }
  }

  if (subLen > subMaxLen) {
    subMaxLen = subLen;
    longestSubString =  subString;
  }

  return subMaxLen;
};
```