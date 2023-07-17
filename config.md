<!--
Add here global page variables to use throughout your website.
-->
+++
author = "Septimia Zenobia"
mintoclevel = 2

# Add here files or directories that should be ignored by Franklin, otherwise
# these files might be copied and, if markdown, processed by Franklin which
# you might not want. Indicate directories by ending the name with a `/`.
# Base files such as LICENSE.md and README.md are ignored by default.
ignore = ["node_modules/"]

# RSS (the website_{title, descr, url} must be defined to get RSS)
generate_rss = true
rss_website_title = "Overoxidize"
website_descr = "Rust, C, Lisp, Research, Math Physics, Thoughts."
website_url   = "https://overoxidize.github.io/"
rss_full_content = false
+++

@def hascode = true
@def prepath = ""
@def website_title = "0xhound" 
@def website_url = "https://overoxidized.github.io/"
<!--
Add here global latex commands to use throughout your pages.
-->
\newcommand{\R}{\mathbb R}
\newcommand{\scal}[1]{\langle #1 \rangle}
