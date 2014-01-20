angular-gum
=============

A wrapper for GetUserMedia in AngularJS which returns a Camera object.

Usage
========
```
angular.directive("selfie", ["Camera", function(Camera) {
	return {
		restrict: "E",
		template: "<video autoplay='true' muted='true'></video>",
		link: function(scope, element) {
			Camera.register(function() {
				element.src = Camera.streamURL;
			});			
		}
	};
}]);
```

The Camera object generated by this service contains:
1) A video stream object
2) A URL for that stream (generated via URL.createObjectURL(stream)) which you can reuse concurrently across your app
3) A video element, prepopulated with the stream and ready for attachment anywhere
