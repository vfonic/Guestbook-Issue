Guestbook-Issue
===============

This is a repository that documents a bug that occurs while accessing JSP file after deployment on Google App Engine

I wanted to make simple app using only one jsp file and one servlet. The root of my app was jsp file and I was calling servlet just when I was submitting the form.

I realised (after several hours of debugging), that, in production (in development/localhost it works), there's a bug with this line here:

    <jsp:forward page="<%= userService.createLoginURL(root) %>" />

...where root is just String object "/".

If I don't explicitly call servlet by typing the URL in the address bar, the application shows "Error: NOT_FOUND" error page.

Here's full code that creates this error:
https://github.com/vfonic/Guestbook-Issue

First try to access the app through this link (it tries to open guestbook.jsp):
http://sitarlabs2.appspot.com/

Then, if you want to get rid of the error, call the servlet and the app will work:
http://sitarlabs2.appspot.com/guestbook

Now go back to:
http://sitarlabs2.appspot.com/

...and everything works normally.
