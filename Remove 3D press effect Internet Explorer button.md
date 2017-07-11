# Remove 3D press effect Internet Explorer button
My solution was to put the button's text within a span element then set the style to transform: translateY(1px);  
For FireFox,need add this :   

    button:active,  
    button:focus,  
    button:hover {  
      margin:0;  
      padding:0;  
    }
