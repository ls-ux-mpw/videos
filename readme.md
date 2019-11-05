# Videos Page

## Updating Carousels
Carousel slides consist of three different items in different sections of the code in corresponding order -- a thumbnail, a modal, and a click event tying the thumbnail and the modal. Carousel slides' naming convention is `carousel #`-`slide` (e.g. third carousel, fourth slide would be `3-4`). As new slides/videos are added or content is reorganized, the name of each slide is adjusted. 

### Thumbnails
```html
<div class="video-wrap" id="thumb-1-7" style="margin-left:15px;"><img class="video-img" src="https://content.lovesac.com/images/content/751584.jpg">
  <br>
  <p class="video-text">How To Use The Wedge Seat</p>
</div>
```
Thumbnail slides are created in the "Videos Page" project in the LS Figma account; each artboard is to be exported as a jpg file @2x following the in-file naming convention. Slide IDs are `thumb-` + `carousel-slide`, and the `src` tag of the `img` is the filename of the uploaded slide.

### Modals
```html
<div class="video-modal-lightbox" id="video-1-7">
  <div class="video-modal-body"><a class="video-modal-close">&times;</a>
  <br><span class="fr-video fr-draggable" contenteditable="false"><iframe class="youtube-iframe" width="560" height="315" src="https://www.youtube.com/embed/SIZVRBfFHOg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen=""></iframe></span></div>
</div>
```
The only things that generally change here are the `id` in the wrapping div and the `src` of the embedded video (the full iframe code is available via YouTube). The `id` maintains the same naming convention as a thumbnail, except `video-` is used in place of `thumb`.

### Click Events
```js
$("#thumb-1-7").on("click", function() {
  $("#video-1-7").show();
});
```
These elements essentially ensure that the right video modal appears when you click on a thumbnail. You'll only have to add new click events if the number of videos in a carousel increases -- as they're irrespective of content, they don't change when thumbnails or videos are shifted around.

## URL-Based Functions
At the bottom of the code is a separate script that performs different functions based on what's typed into a url suffix -- in this case, if you add `?dc=` then a parameter name, it automatically clicks on a different page element depending on the parameter name. For example, according to the code below, if you type `https://www.lovesac.com/how-to?dc=unpacking-your-sactionals`, the page will open, then the "Unpacking Your Sactionals" video modal will appear the second the page loads.
```js
if (dynamicContent == 'unpacking-your-sactionals') {

  $('#thumb-3-1').click();
  
} else if (dynamicContent == 'putting-on-sactionals-covers') {

  $('#thumb-3-2').click();
  
} else if (dynamicContent == 'setting-up-your-sactionals') {

  $('#thumb-3-3').click();
  
} else if (dynamicContent == 'all-about-sacs') {

  $('#thumb-2-1').click();
  
} else if (dynamicContent == 'how-to-fluff-your-sac') {

  $('#thumb-2-2').click();
}
```
Adding more url-based functions just involves adding another `else if` to the conditional statement. Just copy and paste in an existing one after the closing bracket of the previous part of the conditional, change the `dynamicContent == '{whatever}'` to a name of your choice (kebab-case please), and change the selector tied to its `.click()` method to the link ID of your choice. Additionally or alternatively, feel free to ditch the `.click()` method and replace it with any JavaScript or jQuery you want!

You can add this script tag to any custom page on our site if you need to add url-dependent JS -- this comes in handy when trying to create links from emails or social ads. Just be sure to copy and paste the entire script, not just this conditional.
