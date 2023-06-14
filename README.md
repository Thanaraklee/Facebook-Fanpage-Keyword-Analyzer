# Facebook Fanpage Keyword Analyzer 👍 [UPDATE 06/15/2023]
This script allows you to analyze the posts on a Facebook fanpage and determine the percentage of posts containing a specific keyword.

Usage
- Open the Facebook fanpage in your browser.
- Right-click and select "Inspect" to open the Developer Tools.
- Click on the "Console" tab.
- Copy and paste the following code into the console:

## Warning This is Demo! 

`Please scroll down to load all posts before analyzing.`


## Features

- Analyzing Posts: The script reads the body text of each post on a Facebook fanpage.
- Keyword Count: It counts the number of occurrences of a specified keyword within each post.
- Total Posts Count: It calculates the total number of posts on the fanpage.
- Total Keyword Count: It calculates the total number of posts that contain the specified keyword.
- Keyword Percentage: It calculates the percentage of posts that contain the keyword, relative to the total number of posts.
- Result Analysis: It provides an analysis of the keyword percentage and determines whether it exceeds 70% or not.
- Console Output: The script logs the post text, keyword count, total posts count, total keyword count, keyword percentage, and the result analysis in the console.


## Running Tests

To run tests, run the following command

```javascript
var posts = document.querySelectorAll('div.x1yztbdb.x1n2onr6.xh8yej3.x1ja2u2z div.x1iorvi4.x1pi30zi.x1l90r2v.x1swvt13');
var postsCount = document.querySelectorAll('div.x1yztbdb.x1n2onr6.xh8yej3.x1ja2u2z');
var keyword = "ข้าวหน้าบะเต็ง"; // Specify the keyword you want to search
var totalPosts = postsCount.length;
var keywordCount = 0;

var x1htElements = document.querySelectorAll('div.xdj266r.x11i5rnm.xat24cr.x1mh8g0r.x1vvkbs.x126k92a div[role="button"]');

x1htElements.forEach(function(element) {
    element.click();
});

posts.forEach(function(post) {
    var postText = post.textContent.trim();
    var count = countKeywordOccurrences(postText, keyword);
    if (count > 0) {
        keywordCount += 1;
        console.log("Post text:", postText);
        console.log("Keyword count:", count);
    }
});

console.log("Total posts:", totalPosts);
console.log("Total keyword count:", keywordCount);

var keywordPercentage = (keywordCount / totalPosts) * 100;
console.log("Keyword percentage:", keywordPercentage.toFixed(2) + "%");

if (keywordPercentage > 70) {
    console.log("The keyword appears in more than 70% of the total posts. 🎉");
} else {
    console.log("The keyword does not appear in more than 70% of the total posts. 😔");
}

function countKeywordOccurrences(text, keyword) {
    var regex = new RegExp(keyword, "gi");
    var matches = text.match(regex);
    return matches ? matches.length : 0;
}
```



##

Press Enter to execute the code.
The script will analyze the posts and display the results in the console.
Enjoy analyzing your Facebook fanpage! 🚀🔎

Make sure to replace the keyword variable with the specific keyword you want to search for.

Note: This script assumes a specific HTML structure for the Facebook fanpage. If the structure changes, the script may not work as expected.

Feel free to reach out if you have any questions! 🤗
