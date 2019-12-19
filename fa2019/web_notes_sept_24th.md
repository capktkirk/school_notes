Django getting started write up :

RESTful API's

Javascript and modern websites.

  * RPC Remote Procedural Calls
  
What is REST? (and Rest API's)

  * We build web API's to deal with authentication or get data/do anything.
  * REprestational State Transfer (REST)
  * It provides structure for sending/receiving data over HTTP
  * EFfectively replaced SOAP and WSDL based interface designs as easier to use.
  * First introduced in 2000 dissertation work from UC Irvine.


DJANGO REST FRAMEWORK (You can set it up to be restful)


Web Socket Challenge (Use API's in final project)

  REST has four main principles.
  1. Use HTTP methods explicitly
  2. Be Stateless
  3. Expose Directory structures like URI's (Uniform Resource Identifier)
  4. Transfer XML, Javascript Object Notation (JSON) or both.

  Expansion :
  1. One-to-one mapping:
    * To create a resource on the server, use POST
    * To retrieve a resource, use GET
    * To change the state of a resource or to update it, use PUT
    * To remove or delete a resource, use DELETE
  2. Be Stateless.
    * Stateful creates a page, and the web service retrieves a static page.
    * Stateless creates a page with a programmed function API call.
    * The server doesn't need to know the current "state" or where you currently are.
  3. Expose Directory Structure-like URI's
    * Organize URI/URLs in a hierarchical structure like directories.
    * Intuitive/Self-explaining URI's
    * Additional Guidelines:
      * Hide the server-side scripting technology file extensions (.jsp, .php, etc)
        * Allows easy porting to some other framework without changing URI's
      * Keep everything lowercase.
      * Substitute spaces with hyphens or underscores
        * Choose one and be specific.
      * Avoid query strings if you can.
      * Instead of 404 Not Found
        * If request URI is for a partial path, provide default page or resource as response.
    * URI's should be static.
  4. Transfer XML or JSON
    * Choose XML or JSON for clients to send/recieve data from server.
    * Alternatively provide way for clients to specify the type of data they want or are sending and
      provide functionality for both.


  ##Conclusion

  * Rest is a list of rules that should be followed when creating a web API
    * If these rules are followed/met considered to be a RESTful API
  * Need to know what type of data the API uses and how that container needs to 
    be structured for various URI directory calls.
  * Need to know what type of data the API uses and how that container needs to be structured for 
    URI directory calls.
  * Read the API documentation
  * Is just HTTP communications that are done with a specific purpose to make it more consistent.


###How do we make a RESTful API?
  * Let's create an API/Route for suggestions.
  * This is necessary if we are going to get it to work with a responsive 
    React client JS method to auto refresh the suggestion list.
    * This technically doesn't need to be RESTful, but it is a good idea for support of mobile 
      or other implementations.
    * Do I need to implement the RESTful call backs myself? _http://www.django-rest-framework.org_


###Testing REST API

  We can interact with things on Postman to see if our calls are coming correctly.
  Javascript we're going to use is VUE.js
  Vuetify is also good, has a library to be added similar to foundation.
  
