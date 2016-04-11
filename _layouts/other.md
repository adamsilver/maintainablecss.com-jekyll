<!DOCTYPE HTML>
<html dir="ltr" lang="en">
	<head>
	    <title>{{ page.title }} | {{ site.name }}</title>
	    {% include head.html %}
	</head>
	<body>
		{% include header.html %}
        <div class="content">
			<h1>{{page.title }}</h1>
           	{{ content }}
        </div>
        {% include footer.html %}
	</body>
</html>