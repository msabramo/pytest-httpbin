pytest-httpbin
==============

httpbin is an amazing web service for testing HTTP libraries. It has several great endpoints that can test pretty much everything you need in a HTTP library. The only problem is: maybe you don't want to wait for your tests to travel across the Internet and back to make assertions against a remote web service.

Enter pytest-httpbin. Pytest-httpbin creates a pytest "fixture" that is dependency-injected into your tests. It automatically starts up a HTTP server in a separate thread running httpbin and provides your test with the URL in the fixture. Check out this example:

    def test_that_my_library_works_kinda_ok(httpbin):
        assert requests.get(httpbin.url + '/get/').status_code == 200
    
This replaces a test that might have looked like this before:

    def test_that_my_library_works_kinda_ok():
        assert requests.get('http://httpbin.org/get').status_code == 200

pytest-httpbin also supports https and includes its own CA cert you can use.  Check out `the full documentation`_ on the github page.

.. _the full documentation: https://github.com/kevin1024/pytest-httpbin
