# 演示文档

---

````html
<h2>Images</h2>
<div class="sectionLabel">
    &lt;div id=&quot;imageSectionOne&quot; class=&quot;imageSection&quot;&gt;
</div>
<div id="imageSectionOne" class="imageSection">
    <img src="http://www.cirkuit.net/projects/jquery/onImagesLoad/images/3.jpg" height="100" alt="image" id="imageSectionOne_img1">
    <img src="http://www.cirkuit.net/projects/jquery/onImagesLoad/images/5.jpg" height="100" alt="image" id="imageSectionOne_img2">
</div>
<div class="sectionLabel">
    &lt;div id=&quot;imageSectionTwo&quot; class=&quot;imageSection&quot;&gt;
</div>
<div id="imageSectionTwo" class="imageSection">
    <img src="http://www.cirkuit.net/projects/jquery/onImagesLoad/images/3.jpg" height="100" alt="image" id="imageSectionTwo_img1">
    <img src="http://www.cirkuit.net/projects/jquery/onImagesLoad/images/4.jpg" height="100" alt="image" id="imageSectionTwo_img2">
</div>
````

````javascript
seajs.use('onImagesLoad', function($){
     $(function(){
        var eventNumber = 1; //so we can track the ordering of the events in the example
        //attach directly to each image within each .imageSection
        $('.imageSection img').onImagesLoad({
            each : eachImgLoaded,
            all : allImgsLoaded
        });
        //the 'each' callback is invoked once for each individual image that loads
        //i.e. the 'each' callback will be invoked "$('.imageSection img').length" times
        function eachImgLoaded(domObject){
            //note: this == domObject. domObject will be the image element that has just finished loaded
            $(domObject).parent().prepend('<div class="loaded">Event #'+(eventNumber++)+': Image ' + displayTxt(domObject) +
            ' has loaded. Displayed dimensions: ' + domObject.width + 'x' + domObject.height + '</div>');
        }
        //the 'all' is invoked only once: when all images that
        //$('.imageSection img') encapsulates have loaded
        function allImgsLoaded($selector){
            //note: this == $selector. $selector is $('.imageSection img') here
            var allLoaded = ""; //build a string of all items within the selector
            $selector.each(function(){
                allLoaded  = displayTxt(this) + ', ';
            })
            $('body').prepend('<div class="loaded">Event #'+(eventNumber++)+': The following images have loaded within selector $(&quot;' +
                this.selector + '&quot;), which contains the following ' + $selector.length + ' items: ' + allLoaded + '</div>');
        }
        function displayTxt(domObject){ //helper function for displaying results
            return '&lt;' + domObject.tagName + (domObject.id ? ' id=&quot;' + domObject.id + '&quot;' : '') + '&gt;';
        }
    });
});
````
