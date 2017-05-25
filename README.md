# rh-swift
Red Horizon Team - Swift Challenge

1)Checkout the master branch of xcode project with the language of your choice, Swift or Objective-C, to your computer.
 - Swift  - https://github.com/adc-redhorizon/rh-swift.git
 - ObjectiveC - https://github.com/adc-redhorizon/objc-challenge.git

2)Open project in Xcode

3)Setup cocoa pods on your project. You will be using either AFNetworking or AlamoFire to execute the rest requests in your project. 
    - Import the necessary pods for the networking library

4)Call the first rest endpoint to obtain an array of GPS latitude,longitude points in the JSON format. The data will be received in the following format
    - GET http://ec2-34-207-240-57.compute-1.amazonaws.com:3000/locations
    [{"latitude":"X1", "longitude":"Y1"}, {"latitude":"X2", "longitude":"Y2"}...]

5)Use the IOS location manager to obtain your current location.

6)Calculate the linear distance between each set of GPS coordinates received through the rest endpoint and your current location. You can use the formula below to get distance in meters


    var R = 6371e3; // metres
    var rLat1 = lat1.toRadians();
    var rLat2 = lat2.toRadians();
    var dLat = (lat2-lat1).toRadians();
    var dLon = (lon2-lon1).toRadians();

    var a = Math.sin(dLat/2) * Math.sin(dLat/2) +
    Math.cos(rLat1) * Math.cos(rLat2) *
    Math.sin(dLon/2) * Math.sin(dLon/2);
    var c = 2 * Math.atan2(Math.sqrt(a), Math.sqrt(1-a));

    var d = R * c;


7)Once you have the closest location, use the rest endpoint below to obtain the geocoded address corresponding to the closest GPS coordinates
    
    GET
        - url:"https://autofuel.gm.com:8443/api/v1/geocode/reverseGeocode?latitude=X1&longitude=Y1",
        - headers:
            'Authorization':'Basic dXNlcjphdXRvZnVlbHRlc3Q='


8)Print out following details into UI elements of your choice in the view controller
    - String representation of address
    - Distance from current location in miles.

9)Check in your code as a new branch with the branch name {yourfirstname-yourlastname}

Extra Points
Represent the coordinates in a map view embedded into your view controller.
