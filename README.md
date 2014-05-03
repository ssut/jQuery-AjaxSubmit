## jQuery-AjaxSubmit
AjaxSubmit is a plugin for jQuery which is designed to submit form data(such as Username, Email, Password) with XMLHttpRequest(Ajax).

Please refer to the example for how to use this.

## Features
* AJAX form submit with small codes
* Detect form attributes (such as action, method ..)
* Auto serialize form data
* Detect `placeholder` text (use for `required` alert dialog)
* Add `disabled` attribute to form input/button elements (remove attribute when complete load data)
* `success` or `error` callbacks (error callback support: keep use `this` object)
* ... and much more!

## Example
```html
<form id="form" method="post" action="/users/signup">
	<input type="text" name="username" placeholder="Username" />
    <input type="email" name="email" placeholder="Email address" />
    <input type="password" name="password" placeholder="Password" />
    <input type="submit" value="Sign up" />
</form>
<script type="text/javascript">
$('#form').ajaxSubmit({
	required: [
    	/*
        form elements name here (e.g. email, password..)
        */
        'username',
        'email',
        'password',
    ],
    /*
    errorType: 'alert' or 'function'
    alert errorType is showing an alert box on the screen when error occurs.
    function errorType is execute 'error' anonymous function when error occurs.
    */
    errorType: 'function',
    error: function(errors) {
    	// 'this' will point to form element (same context)
    	var messages = $(this).find('div.messages');
        for(var i = 0; i < errors.length; i++) {
        // 'error' object keys defined in server
        var error = errors[i];
        messages.append('<div>' +
        	'<strong>' + error.field + '</strong>' +
            '<span>' + error.message + '</span>');
        }
    },
    success: function() {
    	// Something, What you want to do..
        location.reload();
    }
});
</script>
```

## How To Use
The steps to using AjaxSubmit are as follows:
1. add 'jquery.ajax-submit.js' to your project static directory
2. add `<script src="jquery.ajax-submit.js"></script>` below jQuery core
3. Enjoy! You are shortened your time!