```
https://d1wrvpqjkwb0k5.cloudfront.net/
https://s3-ap-northeast-1.amazonaws.com/wp.workingholiday.com.tw/

UPDATE wp_posts
SET post_content = REPLACE(post_content, 'https://s3-ap-northeast-1.amazonaws.com/wp.workingholiday.com.tw/', 'https://d1wrvpqjkwb0k5.cloudfront.net/')
```
