# Uncommon HTML DOM Manipulation Bug

This repository demonstrates an uncommon bug related to the timing of DOM manipulation in HTML. The bug occurs because the script attempts to access and modify a DOM element ('myDiv') before the browser has fully parsed and rendered it.  This can result in the element not being found or unexpected behavior.

## Bug Description

The `bug.html` file contains a script that tries to hide a div element immediately after it is defined in the HTML. In many cases, this will work, but in some scenarios (or in different browsers), the script runs *before* the browser has finished rendering the div.  This causes the `getElementById` call to fail silently, resulting in no change to the visibility of the div, or in some cases throws a `TypeError` or `ReferenceError`.  This is a subtle and harder-to-debug issue than the more common errors that usually arise when manipulating the DOM.

## Solution

The `solution.html` file provides a correct way to manipulate the DOM. We use the `DOMContentLoaded` event, which ensures that the script only runs after the entire HTML document has been fully parsed and the DOM is ready for modification.  This guarantees that the `getElementById` call will successfully find the element.

This example illustrates the importance of understanding the order of operations and DOM rendering in HTML and JavaScript.