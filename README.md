# RPA-Challange-Shortest-Path
## Introduction

This is an attended bot working in tandem with user. This implementation solves the shortest path puzzle from Automation Challenge website. This is a learning exercise, so code is not as polished as it should be for any production ready implementation.

http://www.rpachallenge.com/assets/shortestPath/public/shortestpath.html

## Challenges and Resolution

On a first glance it looks like a very straight forward exercise of extract data from tables and fill in the forms but as soon as you start digging into the implementation you realise there is more to it than meets the eyes. 

... Almost all input elements on the form has dynamic ids so from one page load to next they changes. Workaround for this issue is to use Anchor Base Activity
... Except for the name field all the fields on the input tables are images. You cannot directly extract text from them and from one page load to another their positions change so you cannot rely on table row numbers. In this case OCR comes to the rescue but as OCR is not 100% accurate to predict text you have to sanitize the extracted values. 
... Once you have extracted data and know what goes where it is matter of using Anchor Base activity to populate input fields.
... Initially tried resetting checkboxes using Image Exists activity but that didn't go well as it was a hit and miss with checkboxes. I have reverted to using bit of JavaScript magic and used Inject Js Script activity to reset checkboxes after each iteration.

## Conclusion

Obviously, this is a first cut version and there is lot desired in the implementation. You can add try catch blocks and separate out data extraction and input logic in different activities and make the main block more elegant.
