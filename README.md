# bird-me
hair that soars above
<!DOCTYPE html>
<html>

<head>
    <meta charset="UTF-8">
    <!-- generator meta tag -->
    <!-- leave this for stats and Silex version check -->
    <meta name="generator" content="Silex v2.2.7">
    <!-- End of generator meta tag -->
       <link data-silex-static="" href="css/normalize.css" rel="stylesheet">
    <link data-silex-static="" href="css/front-end.css" rel="stylesheet">
     <link data-silex-static="" href="css/bootstrap-grid.css" rel="stylesheet">
     <link data-silex-static="" href="css/bootstrap-grid.css.map" rel="stylesheet">
     <link data-silex-static="" href="css/bootstrap-grid.min.css" rel="stylesheet">
     <link data-silex-static="" href="css/bootstrap-reboot.css" rel="stylesheet">
     <link data-silex-static="" href="css/bootstrap.css" rel="stylesheet">
     <link data-silex-static="" href="css/bootstrap.css.map" rel="stylesheet">
     <link data-silex-static="" href="css/bootstrap.min.css" rel="stylesheet">
     <link data-silex-static="" href="css/bootstrap-reboot.min.css.map" rel="stylesheet">
     <link data-silex-static="" href="css/bootstrap.min.css.map" rel="stylesheet">
     <link data-silex-static="" href="css/content.css" rel="stylesheet">
    <script data-silex-static="" type="text/javascript" src="js/jquery.js"></script>
    <script data-silex-static="" type="text/javascript" src="js/jquery-ui.js"></script>
    <script data-silex-static="" type="text/javascript" src="js/pageable.js"></script>
    <script data-silex-static="" type="text/javascript" src="js/front-end.js"></script>
    <script data-silex-static="" type="text/javascript" src="js/js/bootstrap.bundle.js"></script>
     <script data-silex-static="" type="text/javascript" src="js/js/bootstrap.bundle.js.map"></script>
     <script data-silex-static="" type="text/javascript" src="js/js/bootstrap.bundle.min.js"></script>
     <script data-silex-static="" type="text/javascript" src="js/js/bootstrap.bundle.min.js.map"></script>
     <script data-silex-static="" type="text/javascript" src="js/js/bootstrap.js"></script>
     <script data-silex-static="" type="text/javascript" src="js/js/bootstrap.js.map"></script>
     <script data-silex-static="" type="text/javascript" src="js/js/bootstrap.min.js"></script>
     <script data-silex-static="" type="text/javascript" src="js/js/bootstrap.min.js.map"></script>
   
    <script type="text/javascript" class="silex-script">
        /**
         * keep the menu visible when you scroll down
         */
        $(function() {
            var nav = $(".nav");
            var navBg = $(".nav-bg");
            var navOffset = nav.offset().top;
            $(window).scroll(function() {
                if ($(this).scrollTop() <= navOffset) {
                    nav.css('position', '');
                    navBg.css('position', '');
                    nav.css('top', '');
                    navBg.css('top', '');
                    nav.css('z-index', '');
                }
                else {
                    nav.css('position', 'fixed');
                    navBg.css('position', 'fixed');
                    nav.css('top', '0');
                    navBg.css('top', '0');
                    nav.css('z-index', '101');
                }
            });
        });
        
        /*
         * active menu widget for Silex
         * create an element which links to an anchor, e.g. an element with a link to #anchor1
         * add the css class "anchor-link" to this element
         * create an element which is the anchor, e.g. an element with the css class "anchor1"
         * when the user clicks on the link, the scroll slides until the element is visible
         * when the user slides and the element is visible, the link gets a css class "active-menu"
         */
        $(function() {
            // Cache selectors
            var lastId,
                // All list items
                menuItems = $(".nav a"),
                // Anchors corresponding to menu items
                // find the name of the elements which are anchors
                scrollItems = menuItems.map(function(){
                    // the names are in the href attribute of the anchor links
                    var attr = $(this).attr("data-silex-href") || $(this).attr("href");
                    // case of a link in text field or an external link after publish
                    $(this).find("[href]").each(function() {
                        attr = $(this).attr("href");
                    });
                    // case of an "external link" before publish
                    $(this).find("[data-silex-href]").each(function() {
                        attr = $(this).attr("href");
                    });
                    // the links to anchors are expected to start with #
                    if(attr && attr.indexOf("#") === 0) {
                        var name = attr.substring(1);
                        var item = $("." + name);
                        // check if there is a hash in the URL to scroll to the anchor at start
                        if(window.location.hash.indexOf(name) === 1) {
                            var offsetTop = item.offset().top;
                            $('html, body').stop().animate({
                                scrollTop: offsetTop
                            }, 300);
                        }
                        // now find the element itself, which has the name as a css class
                        if (item.length) { return {
                                "link": this,
                                "item": item.get(0)
                            };
                        }
                    }
                });
            // Bind click handler to menu items
            // so we can get a fancy scroll animation
            scrollItems.each(function() {
                var link = this.link;
                var item = this.item;
                $(link).click(function(e){
                  var offsetTop = $(item).offset().top;
                  $('html, body').stop().animate({
                      scrollTop: offsetTop - 50
                  }, 300);
                  e.preventDefault();
                });
            })
        
            // Bind to scroll
            $(window).scroll(function(){
               // Get container scroll position
               var fromTop = $(this).scrollTop() + 50;
               // Get id of current scroll item
               var cur = scrollItems.map(function(){
                 if ($(this.item).offset().top <= fromTop)
                   return this;
               });
               // add the css class on the current menu item
               $(".active-menu").removeClass("active-menu");
               if(cur.length > 0) {
                   cur = cur[cur.length-1];
                   $(cur.link).addClass("active-menu");
               }
            });
        });
        
        /**
         * this widget https://github.com/silexlabs/Silex/issues/443
         */
        $(function() {
        
            window.sr = ScrollReveal({
                distance: '100px'
            });
            sr.reveal('.from-left', { origin:  'left'});
            sr.reveal('.from-right', { origin:  'right'});
            sr.reveal('.from-top', { origin:  'top'});
            sr.reveal('.from-bottom', { origin:  'bottom'});
        
        })
    </script>
  

    <title></title>
    <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=2.2" data-silex-viewport="">
    <meta name="publicationPath" content="/api/1.0/github/exec/put/galaxee/wip">

</head>

<body >
     <a name="home"></a>
    <div class="container">
                <div class="row ">
                    <div class="col-md-12">
                        <div class="center">
                   <img src="assets/bird_logo.png" class="img-responsive" style="width: 300px;">
                        </div>
                    </div>
                </div>
        <p>&nbsp;</p>
        <div class="row">
            <div class="col-md-12">
            <a href="" target="_blank"><img src="assets/app-store-logo.png" class="img-responsive" style="width: 100px;"></a>&nbsp;
           <a href="" target="_blank"><img src="assets/Android-app-store-1.png" class="img-responsive" style="width: 110px;"></a>
        </div>
        </div>
        <p>&nbsp;</p>
    </div>
    <div data-silex-type="container" class=" black-nav prevent-draggable container-element website-min-width editable-style  section-element" >
        <div data-silex-type="container" class="editable-style silex-element-content website-width bird-nav1 bird-container-content container-element prevent-draggable" data-silex-id="bird-nav1">
            <div data-silex-type="text" class="editable-style black-nav text-element paged-element page-galaxee-home-page nav full-width hide-on-mobile" >
                <div class="container">
                    <ul> 
                    <li><a href="#home" class="navatags">Home</a></li>&nbsp;
                        <li><a href="#Why" class="navatags">Why</a></li>
                        <li><a href="#contact" class="navatags">Contact</a></li>
<!--
                        <li><a href="#testimonials">Testimonials</a></li>
                        <li><a href="#services">Services</a></li>
                        <li><a href="#team">Team</a></li>
                        <li><a href="#pricing">Pricing</a></li>
                        <li><a href="#contact">Contact</a></li>
-->
                    </ul>
                </div>
            </div>
        </div>
    </div>
    
<section >
     <a name="Why"></a>
    <p>&nbsp;</p>
    <div class="container">
    <div class="row">
       
        <div class="col-md-12" >
                    <h1  class="heading1">Why</h1>
        </div>
    </div>
        <div class="row">
            <div class="col-md-12" >
                        <p>We as a company believe in great hair and authentic beauty.</p>
                <p>We get there because our creativity and passion for what we do create an interstellar connection between beauty and lifestyle each one of these feeds the other.</p>
                <p>We inspire people through the way we make them feel about themselves. Aesthetically, mentally, and physically.</p>
                <p>We create a world where anything is possible.</p>
                   <p><b>Integrity equals beauty</b></p>
                    </div>
                </div>
<!--
    <div class="row">
     <div class="col-md-12">  
         <div class="center">
        <p class="button" >About More</p>
      </div>
         </div>
    </div>
-->
    </div>
     <p>&nbsp;</p>
</section>

<!--
      <section>
           <a name="experience"></a>
          <div class="container">
          <div class="row">
   <div class="col-md-12">
                    <h1 class="heading1">Experience</h1>
                        <p class="normal">Id strip steak officia swine, irure quis ea pig. Voluptate doner excepteur leberkas laboris. Irure eu turkey non duis biltong meatloaf ullamco laborum aliqua porchetta ad. Pig kevin rump cupidatat strip steak irue hamburger eiusmod
                            ut. Pancetta eu jowl drumstick pork chop capicola. Lorem in deserunt, kevin hamburger in spare ribs.</p>
                        <br>
               </div>   
            </div>
               <div class="row">
            <div class="col-md-6">
                    <h1 class="heading1">Web Design</h1>
                    <h2 class="heading2">2014-2015</h2>
                    <h3 class="heading3">Web Solution "Solution Name"</h3>
                        <p class="normal">Id strip steak officia swine, irure quis ea pig. Voluptate doner excepteur leberkas laboris. Irure eu turkey non duis biltong meatloaf ullamco laborum aliqua porchetta ad.&nbsp;</p>
                    </div>
            
          <div class="col-md-6">
                    <h1 class="heading1">Mobile Apps Developer</h1>
                    <h2 class="heading2">2013-2014</h2>
                    <h3 class="heading3">Web Solution "Solution Name"</h3>
                    
                        <p class="normal">Id strip steak officia swine, irure quis ea pig. Voluptate doner excepteur leberkas laboris. Irure eu turkey non duis biltong meatloaf ullamco laborum aliqua porchetta ad.&nbsp;</p>
                </div>  
            </div>
               <div class="row">
           <div class="col-md-6">
                    <h1 class="heading1">WordPress Developer</h1>
                    <h2 class="heading2">2012-2013</h2>
                    <h3 class="heading3">Web Solution "Solution Name"</h3>
                        <p class="normal">Id strip steak officia swine, irure quis ea pig. Voluptate doner excepteur leberkas laboris. Irure eu turkey non duis biltong meatloaf ullamco laborum aliqua porchetta ad.&nbsp;</p>
            </div>
           <div class="col-md-6">
                    <h1 class="heading1">Web Design</h1>
                    <h2 class="heading2">2014-2015</h2>
                    <h3 class="heading3">Web Solution "Solution Name"</h3>
                        <p class="normal">Id strip steak officia swine, irure quis ea pig. Voluptate doner excepteur leberkas laboris. Irure eu turkey non duis biltong meatloaf ullamco laborum aliqua porchetta ad.&nbsp;</p>
            </div>
              </div>
               <div class="row">
            <div class="col-md-6">
                    <h1 class="heading1">Mobile Apps Developer</h1>
                    <h2 class="heading2">2013-2014</h2>
                    <h3 class="heading3">Web Solution "Solution Name"</h3>
                        <p class="normal">Id strip steak officia swine, irure quis ea pig. Voluptate doner excepteur leberkas laboris. Irure eu turkey non duis biltong meatloaf ullamco laborum aliqua porchetta ad.&nbsp;</p>
            </div>
    <div class="col-md-6">
                    <h1 class="heading1">WordPress Developer</h1>
                    <h2 class="heading2">2012-2013</h2>
                    <h3 class="heading3">Web Solution "Solution Name"</h3>
                        <p class="normal">Id strip steak officia swine, irure quis ea pig. Voluptate doner excepteur leberkas laboris. Irure eu turkey non duis biltong meatloaf ullamco laborum aliqua porchetta ad.&nbsp;</p>
              </div> 
            </div>
          </div>
 <p>&nbsp;</p>
</section> 
-->

 
<!--
<section>
    <div class="container">
<div class="row">
    <div class="center">
                    <h1 class="heading1">Pricing table</h1>
                        <p class="normal">Id strip steak officia swine, irure quis ea pig. Voluptate doner excepteur leberkas laboris. Irure eu turkey non duis biltong meatloaf ullamco laborum aliqua porchetta ad. Pig kevin rump cupidatat strip steak irure hamburger eiusmod
                            ut. Pancetta eu jowl drumstick pork chop capicola. Lorem in deserunt, kevin hamburger in spare ribs.</p>
                        <br>
</div>
    </div>
    </div>
    <p>&nbsp;</p>
    </section>
-->
    <section class="black-background">
         <a name="contact"></a>
        <p>&nbsp;</p>
        <div class="container">
    <div class="row" name="contact">
        <div class="col-md-6">
        <h1>Contact Us!</h1>
        <p><a href="mailto:bird.me@icloud.com">bird.me@icloud.com</a></p>
        <p>1320 Post Road</p>
        <p>East Westport CT, 06880</p></div>
        <div class="col-md-6"><iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d1502.4069681358005!2d-73.31932614770561!3d41.13858759553013!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x89e81afc9ca1e247%3A0x98fcf028f4152ce1!2s1320+Post+Rd+E%2C+Westport%2C+CT+06880!5e0!3m2!1sen!2sus!4v1528164914221" class="img-responsive" width="500" height="450" frameborder="0" style="border:0" allowfullscreen></iframe></div>
        </div>
        </div>
        <p>&nbsp;</p>
    </section>
    
</body>

</html>
© 2018 GitHub, In
