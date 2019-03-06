<DOCTYPE HTML>
	<HTML>
		<head>
			<link rel="stylesheet" type="text/css" href="color-clock.css">
  <title>Color Clock</title>
        <meta http-equiv="Content-type" content="text/html; charset=utf-8">
        <meta name="apple-mobile-web-app-capable" content="yes">
        <meta name="apple-mobile-web-app-status-bar-style" content="black">
        
        <meta name="apple-mobile-web-app-title" content="Color Clock">
        
        <!-- iPhone, iOS 7+, retina -->
        <link href="apple-touch-icon-120x120.png" sizes="120x120" 
            rel="apple-touch-icon-precomposed">
        <!-- iPhone 6 startup image -->
        <link href="apple-touch-startup-image-750x1294.png"
              media="(device-width: 375px) and (device-height: 667px)
                     and (-webkit-device-pixel-ratio: 2)"
              rel="apple-touch-startup-image">
        
        <style type="text/css" media="screen">
      <style>
       
   
       
      </style> -->
      <!--<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.12.4/jquery.min.js"></script>-->
        <script src="js/jquery.min.js" type="text/javascript" charset="utf-8"></script>
        <script src="js/jquery.color.js" type="text/javascript" charset="utf-8"></script>
      <script>
        $(document).ready(function(){
          function clockUpdate(){
          var date = new Date();
          var hours = date.getHours();
          var minutes = date.getMinutes();
          var seconds =date.getSeconds();
          var timeString = padZero(hours) + ":" + padZero(minutes) + ":" + padZero(seconds);
          console.log(hours + ":" + minutes + ":" + seconds);
          $("#time").html( timeString  );
          var color = "#" + timeToHex(hours, minutes,seconds);
          $("#hex").html( color );
          $('body').css(    {'background-color': color}   );
          $('body').animate({'background-color': color},  800, function(){
          blackOrWhiteTextColorBasedOnBackground();
        
        });
};
        clockUpdate(); 
        setInterval(clockUpdate,1000);
        function timeToHex (hours, minutes, seconds){
          return padZero(    parseInt((hours/24) * 255, 10). toString(16))+
 
          padZero(    parseInt(( minutes/60) * 255, 10). toString(16))+
          padZero(    parseInt((seconds/60) * 255, 10). toString(16));
        }
        function padZero(val){
          var value = val.toString();
          return (value.length < 2) ? "0" + value : value;
        }
        $('#selectors a').click (function(){
        	$($(this).attr('href')).show( ).siblings( ).hide();
            $(this).addClass('active').siblings().removeClass('active');
        });
function blackOrWhiteTextColorBasedOnBackground() {
                    //get color in rgb format, as well as locations of first and last char of the string
                    //e.g. "rgb(255, 255, 255)", 4, and 17
                    var color = $('body').css('background-color');
                    var startIndex = color.indexOf('(') + 1;
                    var lastIndex = color.indexOf(')');
                    
                    //pull string of numbers only from color (using start and end parens as indeces)
                    //  and create array of values by splitting around comma delimiter
                    var values = color.slice(startIndex,lastIndex).split(',');
                    
                    //using the brightness index, determine color contrast value
                    var o = Math.round( ( (parseInt(values[0]) * 299) + 
                                          (parseInt(values[1]) * 587) + 
                                          (parseInt(values[2]) * 114) ) / 1000);
                    //if brighter than the middle composite color value (255/2), make text black. else make white
                    (o > 127) ? $('#hex, #time').css('color', 'black') : $('#hex, #time').css('color', 'white');
                    //(o > 127) ? $('#time').css('color', 'black') : $('#time').css('color', 'white');
                }
            
          //var output;
      
            
          
        
        
        } );
        //setInterval(showString, 1000);
      
        /*  var x = 1;
       function showString(){
         
        var y = 1;
        console.log(new Date());
       }
        showString();setInterval(showString,1);
var x = 1;
        console.log("ready"):doIt();
       
       function doIt(){ console.log("done");
       } 
       doIt(2);      function console.log(arg){ return (3*arg);        6
 } 
 */
        
      </script>
		</head>
<body>
	<!-- clock -->
   <div id="clock">
   	<div id="textDisplay">
   	   <div id="time" class= "visibleText noSelect">
   	   	00:00:00
       </div>
   	   <div id= "hex" class= "visibleText noSelect" style="display :none;">
   	   	#000000
    		</div>
      </div>
  
   	    <div id= "selectors">
          <a class= "active" href="#time"></a>
            <a href=" #hex"  ></a> 
        </div>
      </div>
	
</body>
	</html>
