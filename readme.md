# What is Paintjob?

Paintjob is a project I built to easily create beautiful looking demo pages for my other projects. Github Readmes are pefect for documentation, but lack the ability to have interactive demos. So Paintjob uses a repo's readme file to build a beautiful page with navigation and relevent links, and generates runnable and interactive demo's using code blocks in the readme.

To use Paintjob, I simply drop the folder into the `gh-pages` branch of a new project, configure the project data in the `index.html`, and add whatever necessary js files needed to run the demos.

If you are viewing this as the github readme, then click [here](http://stolksdorf.github.io/Paintjob/) to check out this project Paintjob'd.

# Project Data

Each project has it's own unique project data object. It defines the user, the repo, where links should go, and how demos should work. Here's an example of it

	{
		user :'USERNAME',
		repo :'REPO',

		logo_class : 'icon-question',
		logo_color : 'orange',

		/* Project Icons */
		icons : [
			{
				icon_class : 'icon-github',
				color      : 'blue',
				link       : 'https://github.com/USERNAME/REPO',
				tooltip    : 'View on Github'
			},
			{
				icon_class : 'icon-code-fork',
				color      : 'green',
				link       : 'https://github.com/USERNAME/REPO/fork',
				tooltip    : 'Fork on Github'
			},
			{
				icon_class : 'icon-code',
				color      : 'steel',
				link       : 'https://raw.github.com/USERNAME/REPO/BRANCH/FILE.html',
				tooltip    : 'View Raw'
			},
			{
				icon_class : 'icon-home',
				color      : 'red',
				link       : 'https://github.com/USERNAME',
				tooltip    : 'Check out more cool things'
			}

		],

		/* Code Blocks */
		runnable_code_blocks : false, //Adds the run buttn to code blocks in your readme
		show_html_example    : false, //Shows a html demo under each code block

		/* Example */
		example_initialize : function(){
			//This code will be ran once the example html is loaded
			//Use it to start animations or run demos
		},
	}

# Title and Description

Paintjob uses the [Github API](http://developer.github.com/), to pull out the repo's title, description, and it's `README`. The title and description are injected, and the readme is processed to generated the rest of the content.

# Content and Navigation

The README is parsed from Markdown into HTML, then each `<h1>` tag is grouped together into the colored sections you see. I use these sections to build out the navigation on the left.

# Code Blocks

Paintjob will then parse through the content and find code blocks defined with `<pre>` and `<code>`.It converts each of these into instances of [CodeMirror](http://codemirror.net/), which the user can edit. If desired, I can set these code blocks to be runnable using `eval`.

If the project requires html elements for the example to use and modify, I define this html in the project data, which is copied and injected for each code block. A specific scoped reference to that element is exposed in the scope of the eval under the variable name `example`, allowing that code block to only effect that html element and no other ones on the page.

# Footer

The footer is simply static that I want to have on each of my projects. It outlines the licenses I use, as well as a few links to the rest of my resources.



