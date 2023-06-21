# Facebook Fanpage Keyword Analyzer 👍 [UPDATE 06/16/2023]
This script allows you to analyze the posts on a Facebook fanpage and determine the percentage of posts containing a specific keyword.

Usage
- Open the Facebook fanpage in your browser.
- Right-click and select "Inspect" to open the Developer Tools.
- Click on the "Console" tab.
- Copy and paste the following code into the console:

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
// Assume the entered month is "มีนาคม" and the entered day is 15
var enteredMonth = "มีนาคม";
var enteredDay = 18;
var keywords = ["แบงค์", "เงิน", "บัตร"]; // Enter your keywords here

// Function to check the date and scroll down
function checkDateAndScroll() {
  var scrollInterval = 1000; // Adjust the scroll interval (in milliseconds) as needed

  var scrollDown = function() {
    window.scrollBy(0, window.innerHeight);
    setTimeout(checkDate, scrollInterval);
  };

  var checkDate = function() {
    var posts = document.querySelectorAll('div.x1yztbdb.x1n2onr6.xh8yej3.x1ja2u2z');
    var matchFound = false;

    for (var i = 0; i < posts.length; i++) {
      var post = posts[i];
      var dateElement = post.querySelector('a.x1i10hfl.xjbqb8w.x6umtig.x1b1mbwd.xaqea5y.xav7gou.x9f619.x1ypdohk.xt0psk2.xe8uvvx.xdj266r.x11i5rnm.xat24cr.x1mh8g0r.xexx8yu.x4uap5.x18d9i69.xkhd6sd.x16tdsg8.x1hl2dhg.xggy1nq.x1a2a7pz.x1heor9g.xt0b8zv.xo1l8bm span');

      if (dateElement) {
        var dateText = dateElement.textContent.trim();
        var dateParts = dateText.split(' ');
        var day = parseInt(dateParts[0], 10); // Convert day to number
        var month = dateParts[1];

        // console.log("Formatted Date:", day, month);

        // Compare the month and day with the entered month and day
        if (month === enteredMonth && day < enteredDay) {
          // Exact match found, stop scrolling
          console.log(day, month);
          console.log("Exact match found");
          matchFound = true;
          break;
        }
      }
    }

    if (!matchFound) {
      // Scroll down and continue checking
      scrollDown();
    } else {
      // Match found, click on all posts
      clickOnAllPosts();
    }
  };

  // Start scrolling
  scrollDown();
}

// Function to click on all posts
function clickOnAllPosts() {
  var x1htElements = document.querySelectorAll('div.x1a2a7pz div.x78zum5.x1n2onr6.xh8yej3 div.xu06os2.x1ok221b div[role="button"]');

  x1htElements.forEach(function(element) {
    element.click();
  });

  // Wait for the posts to load after clicking
  setTimeout(performKeywordSearch, 2000);
}

// Function to perform keyword search
function performKeywordSearch() {
  var posts = document.querySelectorAll('div.x1yztbdb.x1n2onr6.xh8yej3.x1ja2u2z div.x1iorvi4.x1pi30zi.x1l90r2v.x1swvt13');
  var postsCount = document.querySelectorAll('div.x1yztbdb.x1n2onr6.xh8yej3.x1ja2u2z');
  var totalPosts = postsCount.length;

  keywords.forEach(function(keyword) {
    var keywordCount = 0;

    posts.forEach(function(post) {
      var postText = post.textContent.trim();
      var dateElement = post.closest('div.x1yztbdb.x1n2onr6.xh8yej3.x1ja2u2z').querySelector('a.x1i10hfl.xjbqb8w.x6umtig.x1b1mbwd.xaqea5y.xav7gou.x9f619.x1ypdohk.xt0psk2.xe8uvvx.xdj266r.x11i5rnm.xat24cr.x1mh8g0r.xexx8yu.x4uap5.x18d9i69.xkhd6sd.x16tdsg8.x1hl2dhg.xggy1nq.x1a2a7pz.x1heor9g.xt0b8zv.xo1l8bm span');
      var dateText = dateElement ? dateElement.textContent.trim() : "";

      var count = countKeywordOccurrences(postText, keyword);
      if (count > 0) {
        keywordCount += 1;
        console.log("Keyword:", keyword);
        console.log("Date:", dateText, "Post text:", postText);
        console.log("Keyword count:", count);
      }
    });

    console.log("Total posts:", totalPosts);
    console.log("Total keyword count for", keyword + ":", keywordCount);

    var keywordPercentage = (keywordCount / totalPosts) * 100;
    console.log("Keyword percentage for", keyword + ":", keywordPercentage.toFixed(2) + "%");

    if (keywordPercentage > 70) {
      console.log("The keyword", keyword + " appears in more than 70% of the total posts. 🎉");
    } else {
      console.log("The keyword", keyword + " does not appear in more than 70% of the total posts. 😔");
    }

    console.log("---------------------------");
  });
}

function countKeywordOccurrences(text, keyword) {
  var regex = new RegExp(keyword, "gi");
  var matches = text.match(regex);
  return matches ? matches.length : 0;
}

// Start the process
checkDateAndScroll();

```

## Output

<img src="/output.png" alt="Alt text" title="Output">

##

Press Enter to execute the code.
The script will analyze the posts and display the results in the console.
Enjoy analyzing your Facebook fanpage! 🚀🔎

Make sure to replace the keyword variable with the specific keyword you want to search for.

Note: This script assumes a specific HTML structure for the Facebook fanpage. If the structure changes, the script may not work as expected.

Feel free to reach out if you have any questions! 🤗
