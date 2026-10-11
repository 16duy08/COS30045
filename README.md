Appliance Energy Consumption Website

A small multi-page website that compares the yearly energy use of televisions sold in Australia. It was built for COS30045 Data Visualisation, Exercise 1 using HTML and CSS, with charts created in KNIME.

Author: Phạm Trần Anh Duy (Swinburne University of Technology) Live site (Mercury): https://mercury.swin.edu.au/cos30045/s105692075/index.html GitHub repository: <!-- TODO: paste your GitHub Classroom repository link here --> Aim

To demonstrate a simple website that uses HTML for structure, CSS for consistent styling, and a GitHub repository for version control, and to display data visualisations produced in KNIME.

Pages Page File Content Home index.html Introduction, three summary boxes, FAQ section that is hidden by default Televisions televisions.html Example table of television sizes and power use, plus the KNIME charts About Us about.html About the site and author Website requirements checklist Four HTML pages: Home, Televisions, The Story, About Us Top navigation on every page, with links to all three pages Power logo (PowerIcon.png) in the top-left corner, linking back to the Home page Mouse-over (hover) effect on the navigation links Current page clearly highlighted in the navigation Placeholder content about appliance energy use on the Home page FAQ section that is hidden by default and can be revealed and hidden All styling in one external CSS file Colour scheme applied consistently across all pages Footer on every page with the year, my name and a Generative AI acknowledgement Website hosted on the Mercury server Notes on how the requirements were met FAQ behaviour: the FAQ uses the HTML <details> and <summary> elements, which open and close without JavaScript. This version of the site does not use JavaScript at all, so the optional JavaScript Energy Calculator extension was not implemented. Colours: the colour scheme is a dark navy background with cyan and green accents, chosen to suit an energy theme. It does not follow the colours of the supplied yellow logo, which is a deliberate design choice. Footer year: the year in the footer is written directly in the HTML (2026). Folder structure / index.html televisions.html story.html about.html README.md assets/ css/ style.css img/ PowerIcon.png chart-energy-by-tech.png chart-share-by-tech.png chart-scatter.png chart-histogram.png

There is no js folder because no JavaScript is used.

Data and charts

Data source: Australian Government Energy Rating registry export of registered television models (tv_2026_09_30.csv, exported 30 September 2026). It has 5,036 rows (one per model) and 32 columns, including brand, screen technology, screen size, labelled yearly energy consumption (kWh/year) and star rating.

Processing in KNIME:

Read the CSV with CSV Reader. Trim extra spaces in text columns with String Cleaner. Group by Screen_Tech and calculate the mean of Labelled energy consumption (kWh/year) with GroupBy. Convert screen size from centimetres to inches (divide by 2.54) with Expression. Create charts with the Bar Chart, Pie Chart, Scatter Plot and Histogram nodes, then export each chart as a PNG image.

Charts on the Televisions page:

Bar chart: average yearly energy use by screen technology (LCD about 351, LCD (LED) about 457, OLED about 481 kWh). Pie chart: each technology's share of the combined average yearly energy use. Scatter plot: relationship between screen size and energy use. Histogram: distribution of yearly energy use across television models.

Data story (story.html, Week 3):

The story answers one question: is OLED really the thirstiest television? It has four chapters. (1) Average energy by technology makes OLED look worst (LCD about 351, LCD (LED) about 457, OLED about 481 kWh/year). (2) The scatter plot shows screen size is the hidden factor (correlation about 0.85). (3) A grouped bar chart splits sizes into Small (under 43 inches), Medium (43 to under 65) and Large (65 and over) so technologies are compared at similar size; Large averages about 748 kWh/year against about 159 for Small, and Small OLED has only 19 models. (4) Star rating index by technology is almost flat (LCD about 5.2, OLED about 5.1, LCD (LED) about 5.0). All figures use the same 5,036 registry rows as the rest of the site. <!-- TODO: replace the SVG charts in story.html with KNIME PNG exports once made -->

Limitations of the data:

The data lists registered models, not televisions sold or used in homes. Energy figures are labelled test values, not real household use. The mean can be pulled up by a small number of very large televisions. The numbers in the example table on the Televisions page and the summary boxes on the Home page are placeholders for illustration, not figures from the dataset. How to run

Open index.html in a web browser. No build step is needed. The page loads two fonts (Orbitron and Exo 2) from Google Fonts, so an internet connection is needed to see them; a standard font is used if they cannot load.

Generative AI Reflection

<!-- Edit this section so it describes what YOU actually did. Keep it honest. -->

Tool(s) used: I used Claude (Anthropic) in a chat window.

What I used it for:

Generating the first version of the HTML, CSS and JavaScript from the task description. Explaining the code line by line so I could understand it. Guidance on KNIME: which nodes to use, how to set up the charts, and checking my workflow file for mistakes. Help with the Mercury server: activating the account, installing the VPN and uploading files with WinSCP. Explaining statistics ideas (mean and median) for the oral Q&A.

What I changed or adapted after generation:

I decided to drop the yellow theme and use a dark energy theme (navy, cyan and green) and asked for a different font style. I asked for the site to use only HTML and CSS, so the JavaScript accordion and calculator were replaced by the <details> FAQ and an example table. I asked for the CSS to be rewritten in a simpler style that I could understand. I built the KNIME workflow and charts myself and exported the chart images. After the generated review I corrected the nodes and added more charts. <!-- TODO: list the specific changes you actually made in KNIME --> I uploaded the finished site to Mercury and checked the live link myself.

What I learned:

How HTML structure, one external CSS file and the hover and active styles work together across several pages. How the <details> element can make a hidden FAQ without JavaScript. How to clean, group and chart data in KNIME, and why the mean and median can differ when the data is skewed. That a chart can be misleading even when it is correct, for example comparing OLED and LCD averages without taking screen size into account. How to host a site on a university server using SSH, a VPN and SFTP.

Limitations and issues I encountered:

The AI wrote placeholder numbers (for example daily household electricity use) with no source, so I treated them only as placeholders and did not present them as facts. Some generated instructions were out of date or not specific to my unit, for example an old VPN address that did not work; I had to find the current one from the university's instructions. It could not see my KNIME settings from a screenshot, and when it checked my workflow file it found mistakes in the first version of my charts (wrong columns on the scatter plot and histogram, and unused nodes), so I had to fix them myself. The generated design did not follow the assignment's rule about colours matching the logo, and it did not use JavaScript for the FAQ, so I had to decide whether to accept these differences. I had to check generated numbers and claims against the data rather than trust them.