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
