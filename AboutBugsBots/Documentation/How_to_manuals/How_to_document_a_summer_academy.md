#How to document a summer academy

##About the process of making this publication by Vicky De Visser, Anja Groten and James Bryan Graves

During the course of the Summer Academy the participants, tutors and organizers actively documented in various ways. We quickly realized this parallel mode of collective production was developing a life of it's own and introduced an interesting form of exchange between all stakeholders. People were using tools like PiratePad for collective note-taking, a local wireless network created with a raspberry pi to share files, swapped usb sticks, and used git repositories to archive scripts and images. However the variety of documentation methods made the following processing of the documented material confusing.<br>
The proposition of this printed matter is to create a documentation of an on and offline documentation process. In addition the intention is to develop an open and central publishing infrastructure before approaching the next H&D Summer Academy in 2016. In the following you will find some considerations that drove the production of this specific hybrid publication.

###Choose an appropriate workflow for your hybrid publishing proces

Before starting with your publication, you will need to inventory your documentation material. Subsequently think about possible future occasions that will require documentation. 

In the case of the H&D Summer Academy documentation we filtered out 3 crucial moments to contemplate:

**Before the summer academy**

Although the academy had not even started yet, a lot of content had been generated already. We had acquired research, chose a subject, planned schedules, got the word out by printed and digital media and processed motivation letters of applicants. It would have been helpful for future editions of the summer academy and possible new collaborators to document that process thoroughly. 

**During the summer academy**

During the summer academy workshop materials were provided by the tutors, using different platforms and formats. While currently working with WikiMedia for assembling, writing and editing the documented content we realize this could have been the right platform to collect workshop descriptions beforehand, gather materials used during the workshops, put presentations there and add notes and scripts produced during workshops. As the summer academy progressed we more and more missed a central platform where participants could always go back to in order to catch up, acquire practical information or dump some interesting references. Pictures were taken both by the organization and participants. After the academy had been accomplished we emailed every participant to ask them to send their pictures. Having created this publishing infrastructure we are considering to offer an immediate access to the actual publishing process in the future, which would save time. 

**After the summer academy**

After the summer academy program had been completed we did not wait long to ask the participants and tutors for feedback. To engage people in creating useful feedback you need to make the feedback process as low barrier as possible by for example asking very specific questions, creating forms that are easy to fill out or by interviewing people directly. A wiki could be a convenient platform to process that feedback. See also: [[Feedback from participants of the HDSA2015]]

###Content managing
In order to compile the documentation material we strived to bundle processes such as co-writing, co-editing and content management optimally all on the same platform. We looked for a back-end that provided real time editing process, that was accessible, provided a comprehensible way of ordering information, had a small learning curve for participants and supported a variety of media files. <br>
The workshops, lectures, screenings, excursions, and the final presentation were documented with media such as videos, sound files, notes, images, and code as well as objects, longer and shorter texts. <br>
Eventually we chose to use WikiMedia, which supports the several file formats and is easy editable by different users. Wikimedia is an easy infrastructure and is well documented. Preparing user guides along the way is beneficial for changing collaborations and teams. <br>
For the first edition of the H&D Summer Academy we didn’t have the opportunity to test WikiMedia as a back-end and content collector for students. We started using it only after the academy to gather the information collected by writing emails and uploading code and pictures to a github and dropbox repositories. During the process of filling the Wiki we did encounter some minor hierarchy and workflow challenges, that we had to get used to as an editorial team.

###Content categorizing
To be able to publish a well structured and logical documentation we started sorting content by categorizing the wiki pages we created. We applied a categorization system that was recommended to us, which sorts content by state, media and topic. <br>
The media category is necessary because not all media, for instance video, sound files or links are suitable for a printed publication. Furthermore very long texts are not suitable for the Hackers & Designers website. <br>
It is important to critically sort the content upfront considering the advantages and disadvantages of different media. 

###Co-writing and editing
After receiving all contributions, the participants and eventually the editorial team must select the most viable material. The challenge of the selection process lies in recognizing that some submissions might not be useful, have another logic or are difficult to implement in the publication for other reasons. The challenge consists to include as much of the content produced as possible without alienating it. <br> 
We advise to give the participants a short introduction beforehand in how to collect and document the content. This way the editors prevent an extensive editing process afterwards. <br> 
WikiMedia lets users adjust articles and write comments on the changes that were made. Participants have accordingly the possibility to go back in time and compare older versions of the same article. That way content will not get lost after editing an article.

###Editorial considerations
After building and filling the wiki with content we revisited all articles created and considered an appropriate translation of the content for a website and a printed publication format. For print we looked into two options: 1. creating a publication from the website and 2. creating a publication directly from the wiki. 

**Current set-up**
{| class="wikitable" border="2"
|-
|CMS
|[http://wiki.hackersanddesigners.nl wiki.hackersanddesigners.nl]

|-
|Front-End
|[http://hackersanddesigners.nl hackersanddesigners.nl]

|-
|Print publication
|[http://wiki.hackersanddesigners.nl/mediawiki/index.php/Book_sprint_2015 wiki.hackersanddesigners.nl > Book sprint 2015] 
|}

**Editorial quest**   
* collecting & sorting        
* prepping (i.e. retouching or re-taking foto's)          
* developing an editorial voice (in our case: The format of''How to'' manuals are the unifying component for every article)       
* generating content: co-writing and editing         
* publishing (online)         
* printing         
* distributing (publishing offline)         

**Translation wiki to website**
{| class="wikitable" border="1"
|-
|Javascript
|Requests content from wiki

|-
|Mediawiki API
|Returns wiki content

|-
|HTML/CSS
|Layout of the website
|}

'''Translation wiki to print'''
{| class="wikitable" border="1"
|-
|Pandoc
|Translates wiki markup to LaTeX mark-up

|-
|Python Script
|Initiates several actions

|-
|LaTeX
|Lay-out of wiki content and generating PDF
|}

###Publishing online
The wiki content is published on the Hackers & Designers website in real-time. Meaning every time the website is loaded or pages are requested the web browser queries the MediaWiki back-end using the MediaWiki provided API, along with installed wiki semantic extensions and their APIs, through a Javascript client-side web application (AngularJS).

**Example API Requests** <br>  
**See also [> How to document a summer academy](http://wiki.hackersanddesigners.nl/mediawiki/index.php/How_to_document_a_summer_academy#Publishing wiki.hackersanddesigners.nl)**    

**Request a page:**
    curl 'http://wiki.hackersanddesigners.nl/
    mediawiki/api.php?action=parse&
    page=How_to_document_a_summer_academy&
    format=json&disableeditsection=true&
    prop=wikitext|images|links'

**Request an image:**
    curl 'http://wiki.hackersanddesigners.nl/
    mediawiki/api.php?action=query&
    titles=File:Chicken-and-Potato-Soup.png&
    prop=imageinfo&&iiprop=url&format=json'

**The code is available on: <br>
[github.com/hackersanddesigners/handd-web](https://github.com/hackersanddesigners/handd-web github.com/hackersanddesigners/handd-web).**

###Publishing in print
**Web to print: HTML to print with CSS and print preview** <br>
One way to publish a print publication from an online environment is printing a webpage by using CSS. A user can just click ‘Print Page’, a pop-up print preview will appear and the custom CSS will translate the webpage and media to a printable print publication divided in pages.
The design is also made with code/text, which means that you can use text editors such as EtherPad to collaborate on content with several people at the same time. The negative side on using this set-up is that you if you decide to not use a single page website you will have to print each article separate and later bind it into a book. This way no table of contents will be created or there will be no option to apply different lay outing for indexes, special chapters, or glossaries. 

**Differences between CSS for the web and CSS for print**<br>
You also have to consider the differences between a webpage and a printed publication. What will happen with image galleries, sliders, menu’s and the like? If your webpage has a slideshow with ten images at the top, that’s not going to translate well to paper. The most basic level of interaction on the web is a link. This too becomes problematic. On your computer, you can simply click a link to see where it goes, on paper this functionality is lost so you need a good way to take all those inline links and show the reader where they lead. <br>
The biggest difference, and conceptual shift, is that printed documents refer to a page model that is of a fixed size. Whereas on the web we are constantly reminded that we have no idea of the size of the viewport, in print the fixed size of each page has a bearing on everything that we do. Due to this fixed page size, we have to consider our document as a collection of pages, paged media, rather than the continuous media that is a web page.
Paged media introduces concepts that make no sense on the web. For example, you need to be able to generate page numbers, put chapter titles in margins, break content appropriately in order that figures don’t become disassociated from their captions. You might need to create cross-references and footnotes, indexes and tables of content from your document. You could import the document into a desktop publishing package and create all of this by hand, however, the work would then need redoing the next time you update the copy. This is where CSS comes in, whose specifications are designed for use in creating paged media.

**Print preview** <br>
If you want to print your website a print preview window appears. The back-end code in the browser needs to do heavy lifting to support all the requests coming from the front-end.

The majority of the work in the back-end involves restructuring the HTML to support preview. Once all the platforms are brought in line, the printing pipeline needs to be broken up into two pieces: PDF generation and printing. The user has to select a printer before a print render is generated for a preview. When printing, the renderer generates printing metadata one page at a time, so it can generate them while the PrintJobWorker in the browser process sends them to the printer at the same time.

**From CSS and HTML to print with Prince.**  <br>
After you prepared your HTML and CSS for the website, and the layout for the book is set with CSS, Prince or another API can be used for translating the HTML language to a PDF. <br>
You can download a free trial of Prince and install it with Terminal. The Terminal runs Prince and uses it to translate the website into a pdf. Prince is not an open source program.

**Wiki to print** <br>
**Collection and the Offline Content Generator** <br>
After doing some research we found out that WikiMedia had already developed an open source plug-in, called Collections created by The Wiki Publisher Project. The extension makes it possible to select pages to create pdf’s or compile books. The user can create different chapters and arrange articles. Then the compiled pages are send to the OCG (Offline Content Generator). The OCG invokes a /Bundler to spider the articles and fetch all images, stylesheets, etc required to render them. One of several /Backends are then invoked to convert the bundle into a PDF, ZIM file, or other appropriate output format. This conversion to a pdf happens on wiki servers. We wanted to use this open source plug-in and adjust the code to fit our needs. (eg layout, page size, content table,…)  <br>
For rendering on your own server (not using the wiki content generator) we installed the Offline Content Generator. This way we were able to change the layout of the output files. (pdf’s) 

**Offline content generator the package:**
* Service
* Bundler: This tool grabs all the dependencies for a given set of articles and creates a directory or zip file. 
* Latexer

**Latex'** <br>
Latex is a high-quality typesetting system; it includes features designed for the production of technical and scientific documentation. LaTeX is available as free language.
* Several extensions are available for LaTex called: ‘packages’ or ‘styles’ (better image placement, implementation of mathematic formula,...)
* Create a text file in LaTex mark-up, which LaTex reads to produce the final document.
* User needs to know the commands for the LaTex mark-up
* LaTex automatically adjusts fonts, text size, line heights or text flow.
* LaTex is not flexible for lay outing, but you’re able to write your own macro’s or download them from others at CTAN 
* pdfTex: engine or pdf compiler. This converts the LaTeX mark-up to a pdf.

To be able to use the LaTeX mark-up, you have to install LaTeX distribution and an Editor. We used the TexMaker editor for Mac because this editor enables you to see quick previews of the Pdf file.

**Bookshelf**<br>
This WikiMedia plug-in allows previous compiled books to be added to the bookshelf. The bookshelves can be used to print previously published editions of a publication by other users. This way we can compile one 'official' documentation book and let other people print it.

**Pandoc**  <br>
This program converts files from one mark-up language to another. In this case, we used it convert the WikiMedia mark-up to HTML for our website, and to LaTex mark-up for the print publication.

**Mark-up**  <br>
A mark-up language is a notation used to annotate a document’s content to give information regarding the structure of the text or instructions for how it is to be displayed.

###Concluding: The Hackers & Designers approach
Hackers & Designers through evaluating all the options available opted for using a Python script to collect MediaWiki content and then to use Pandoc together with a Latex template to generate the final PDF.
 

**Step 1** <br> 
Download repository from: [github.com/hackersanddesigners/handd-book''] (https://github.com/hackersanddesigners/handd-book) 


**Step 2** <br>
Type into your terminal: ''python get_wiki.py'' <br>
Missing python dependencies can be installed with:

    pip install <module_name>

**Step 3** Type into your terminal the following Pandoc command: <br>
    pandoc --template handd-book.template handd-book.wiki -o handd-book.pdf --toc \ 
    -M fontsize=12pt -M author='Hackers \& Designers' -M title='About Bugs, Bots and Bytes' \
    --latex-engine xelatex -M mainfont='Helvetica' -M papersize='a5paper' -V links-as-notes

Missing latex dependencies can be installed with:

    tlmgr install <pkgname>


[[File:documentation-workflow.jpg|500px|Diagram: How this publication came into being]]

###Dos and Don'ts      
* Adding links to titles will cause errors    
* Image galleries will cause errors     
* Using & and other glyphs in titles might cause errors      
* Try to name your images in a meaningful way (no cryptical numbers)         
* Avoid spaces in file names       
* In your wiki mark-up: avoid single ''=…='' to mark-up titles. Start your hierarchy with ''==…==''
