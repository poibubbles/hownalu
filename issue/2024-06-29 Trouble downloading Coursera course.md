Wasn't able to download Coursera course using `coursera-dl`.

Naive attempts with username+password are likely to end up with something like:

		400 Client Error: Bad Request for url: https://api.coursera.org/api/login/v3

``CAUTH`` or ``-ca`` attempts need a ``CAUTH`` value that you can find after logging in via browser in ``Inspect > Application > Storage > Cookies > [url] > CAUTH``. (Finding a ``cookies.txt`` or viewing or exporting is probably more difficult.)

But using ``CAUTH`` wound up with a fancy:

	Coursera - API Route Does Not Exist

..which sounds like the same thing.

Also, ``coursera-dl`` is probably looking for the course name as part of the URL after ``learn``, as in ``https://www.coursera.org/learn/preparing-for-your-pr...``.

In order to get to a location that has that ``learn/`` in the URL, you'll
probably have to navigate there from your list of enrolled courses.
