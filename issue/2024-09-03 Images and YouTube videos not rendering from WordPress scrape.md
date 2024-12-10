
First, check if the code has both `<script>` and `<noscript>` sections and whether or not your browser enables JavaScript.

Then check if your `<img>` and `<iframe>` tags are using a bogus `src` for something like a 1x1 pixel  `src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw=="` and hiding the actual source URL in something like `data-src`.

Could be that you toggle JavaScript off to reveal images that are using `src` normally in `<noscript>` sections, but need whatever JavaScript magic to reveal embedded videos.

A helpful search for which files may contain embedded videos:

		grep -r -o "https\:\/\/www\.youtube\.com.*\?" .

Note that WordPress embedded YouTube videos using this format:

		 <div class="wp-block-embed__wrapper">https://www.youtube.com/watch?v=Qn6TsQEQ9GY</div>

			
Howabout extracting from the DB? MAYBE. See [[Install and query MariaDB on MacOS]].

Also - uploading `wp-content/uploads` to a Google Site just for convenient hosting purposes? MAYBE. NOPE. You can insert a view to a folder in Google Drive, but clicking on the items listed in the view will just take you to that item in Google Drive.
