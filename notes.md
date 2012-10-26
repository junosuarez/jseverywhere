 - large number of libraries trying to cope with async programming model in Node
 - async is a big issue in the browser, too: especially with long-running and real-time apps

 -async is important for keeping the UI humming along while your app is doing things, important for user experience

 promises: temporal decoupling for your application
 seperation of concerns
 define the interface:
 i need x, I do y

 promises allow for a programming model we're all familiar with in sync programming:

 var user = createAccount();
 saveToDb(user);
 sendWelcomeEmail(user);

 but even better, they let us do cool functional programming style things:

 users = db.getUsers()
 var total = users.
 map(function(user) {
  return user.joinDate;
 }).
 reduce(function(a, joinDate) { return a + daysSince(joinDate); }, 0);
 alert('our users have ' + total + ' days of combined experience')

 better still, it lets the implementations of these methods not care about when they're when application flow happens.
 program reuse through functional composition, now with temporal decoupling. twilight zone.

 cross-cutting concerns:
 logging
 auditing
 analytics

 validation
 cryptography
 cacheing    \ ____ data access
 memoization /

 authorization
 feature flags
 policy injection

 ui - indicate loading / activity state


 a few ways to deal with the above:
 -AOP / direct pipelining of invocations (before/wrap/after advice)
 -reactive / unobtrusive observable on events (especially for logging)
 -foundations level interfaces: I/O, logging


 further, it doesn't matter whether things are running in-proc, through IPC, or RPC
 - at least not from a logical point of view. ultimately, you need to get real about some of the things. but having conceptual clarity in your application architecture gives you the freedom and flexibility to makes these choices for the right reasons - what's good for your application, not what's possible by the constraints of your development model.

 recommended resources:
 for the server: Q, when.js


comparison to synch programming paradigm:
a function takes a number of parameters and can either return a value or throw an exception.
using promises, you're still writing functions
they take parameters and always return a promise. a promise can already be fulfilled, or it can be pending. rather than throwing an error on an exception, a promise-returning function should reject the promise.

like dominoes: http://www.domino-play.com/TopplingBasic.htm
