The goal is to export WordPress posts along with their dependencies (images, links to YouTube videos, etc.).

Selecting posts that have some content:

		select * from wp_bhzn_posts where post_content != '';

Hookuaaina stats:
211 posts with content. 1488 attachments (`post_type = 'attachment'`)

Takeaways:
`post_name` looks like a unique and somewhat file-friendly ID.
	`post_mime_type` includes `image/jpeg`, `image/png`, `application/pdf`, `audio/mpeg`, `font/woff`, `image/x-icon`, `video/mp4`
`post _parent` items aren't really interesting - mainly titles, sections, and links to external things like forms.

