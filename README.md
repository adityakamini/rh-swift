# rh-swift

1)Checkout the master branch of xcode project with the language of your choice, Swift or Objective-C, to your computer.
 - Swift  - https://github.com/adc-redhorizon/rh-swift.git
 - ObjectiveC - https://github.com/adc-redhorizon/objc-challenge.git

2)Open project in Xcode

3)Setup cocoa pods on your project. You will be using either AFNetworking or AlamoFire to execute the rest requests in your project. 
    - Import the necessary pods for the networking library

4)Call the first rest endpoint to obtain an array of GPS latitude,longitude points in the JSON format. The data will be received in the following format

        - GET https://labs.gm.com/interview/api/location
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
        - url:https://labs.gm.com/interview/api/geocode/reverse?latitude=42.511852&longitude=-83.038858,
        - response: {
            "address":"General Motors Technical Center",
            "formattedAddress":"General Motors Technical Center, Warren, MI 48090",
            "locality":"Warren",
            "region":"MI",
            "postal":"48090"}




8)Print out following details into UI elements of your choice in the view controller
    - String representation of address
    - Distance from current location in miles.

9)Check in your code as a new branch with the branch name {yourfirstname-yourlastname}

Extra Points
Represent the coordinates in a map view embedded into your view controller.
