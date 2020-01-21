<h1># uxweb-sweet-alert-laravel</h1>
<h2>Step 1: Install uxweb/sweet-alert Package</h2>

Here, we will install uxweb/sweet-alert composer package that way we can simply use their method for flash message. So let's run bellow command.

<h1>composer require uxweb/sweet-alert</h1>

After successfully install package, open config/app.php file and add service provider and alias.

<h2>config/app.php</h2>

<h3><pre>'providers' => [

	....

	UxWeb\SweetAlert\SweetAlertServiceProvider::class,

],

'aliases' => [

	....

	'Alert' => UxWeb\SweetAlert\SweetAlert::class,

]</pre>
</h3>

<h2>Step 2: Add Route</h2>

In this is step we need to create route for testing with argument. so open your routes/web.php file and add following route.

<h2>routes/web.php</h2>

<h3><pre>Route::get('my-notification/{type}', 'HomeController@myNotification');</pre></h3>

<h2>Step 3: Add Controller Method</h2>

Here, we will add new method myNotification() in HomeController. In this method i use alert() for flash message so let's add following method on your home controller.

app/Http/Controllers/HomeController.php
<h3><pre>
class HomeController extends Controller
{
    /**
     * Create a new controller instance.
     *
     * @return view
     */
    public function myNotification($type)
    {
        switch ($type) {
            case 'message':
                alert()->message('Sweet Alert with message.');
                break;
            case 'basic':
                alert()->basic('Sweet Alert with basic.','Basic');
                break;
            case 'info':
                alert()->info('Sweet Alert with info.');
                break;
            case 'success':
                alert()->success('Sweet Alert with success.','Welcome to ItSolutionStuff.com')->autoclose(3500);
                break;
            case 'error':
                alert()->error('Sweet Alert with error.');
                break;
            case 'warning':
                alert()->warning('Sweet Alert with warning.');
                break;
            default:
                # code...
                break;
        }


        return view('my-notification');
    }
}</pre></h3>


<h2>
Step 4: Add Blade File
</h2>
At Last we have to create my-notification.blade.php file and in that file i write code how to use sweetalert package. So let's create blade file and put that code.<br>
resources/views/my-notification.blade.php
<h3>
<pre>
&lt;html&gt;
    &lt;head&gt;
    	&lt;title&gt;Laravel Sweet Alert Notification&lt;/title&gt;
	&lt;link rel="stylesheet" href="http://demo.itsolutionstuff.com/plugin/bootstrap-3.min.css"&gt;
	&lt;script src="http://demo.itsolutionstuff.com/plugin/jquery.js">&lt;/script&gt;
	&lt;link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/sweetalert/1.1.3/sweetalert.min.css" /&gt;
	&lt;script src="https://cdnjs.cloudflare.com/ajax/libs/sweetalert/1.1.3/sweetalert.min.js">&lt;/script&gt;
    &lt;/head&gt;
    &lt;body&gt;
    &lt;h1 class="text-center"&gt;Laravel Sweet Alert Notification &lt;/h1&gt;
    @include('sweet::alert')

    &lt;/body&gt;
&lt;/html&gt;

</pre>
</h3>

Now we are ready to run our example so run bellow command so quick run:

<h3><pre>php artisan serve</pre></h3>

Now you can open bellow url on your browser:

<h3><pre>
http://localhost:8000/my-notification/success
http://localhost:8000/my-notification/basic
http://localhost:8000/my-notification/message
</pre>
</h3>
