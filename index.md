---
layout: workshop      # DON'T CHANGE THIS.
carpentry: "dc"    # what kind of Carpentry (must be either "lc" or "dc" or "swc").
                      # Be sure to update the Carpentry type in _config.yml as well.
venue: "Environnement et Changement climatique Canada"        # brief name of host site without address (e.g., "Euphoric State University")
address: "en ligne"      # full street address of workshop (e.g., "Room A, 123 Forth Street, Blimingen, Euphoria")
country: "Canada"      # lowercase two-letter ISO country code such as "fr" (see https://en.wikipedia.org/wiki/ISO_3166-1#Current_codes)
language: "fr"     # lowercase two-letter ISO language code such as "fr" (see https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes)
latlng: "45.499680,-73.555130"       # decimal latitude and longitude of workshop venue (e.g., "41.7901128,-87.6007318" - use https://www.latlong.net/)
humandate: "22-23 juin 2021"    # human-readable dates for the workshop (e.g., "Feb 17-18, 2020")
humantime: "8h30 - 16h HAE"    # human-readable times for the workshop (e.g., "9:00 am - 4:30 pm")
startdate: 2021-06-22      # machine-readable start date for the workshop in YYYY-MM-DD format like 2015-01-01
enddate: 2021-06-23        # machine-readable end date for the workshop in YYYY-MM-DD format like 2015-01-02
instructor: ["Martin Jean"] # boxed, comma-separated list of instructors' names as strings, like ["Kay McNulty", "Betty Jennings", "Betty Snyder"]
helper: ["NA"]     # boxed, comma-separated list of helpers' names, like ["Marlyn Wescoff", "Fran Bilas", "Ruth Lichterman"]
email: ["martin.jean@ec.gc.ca"]    # boxed, comma-separated list of contact email addresses for the host, lead instructor, or whoever else is handling questions, like ["marlyn.wescoff@example.org", "fran.bilas@example.org", "ruth.lichterman@example.org"]
collaborative_notes:             # optional: URL for the workshop collaborative notes, e.g. an Etherpad or Google Docs document
eventbrite:           # optional: alphanumeric key for Eventbrite registration, e.g., "1234567890AB" (if Eventbrite is being used)
---

{% comment %} See instructions in the comments below for how to edit specific sections of this workshop template. {% endcomment %}

{% comment %}
HEADER

Edit the values in the block above to be appropriate for your workshop.
If the value is not 'true', 'false', 'null', or a number, please use
double quotation marks around the value, unless specified otherwise.
And run 'make workshop-check' *before* committing to make sure that changes are good.
{% endcomment %}


{% if page.carpentry != site.carpentry %}
<div class="alert alert-warning">
You specified <code>carpentry: {{page.carpentry}}</code> in <code>index.md</code> and
<code>carpentry: {{site.carpentry}}</code> in <code>_config.yml</code>. Make sure you edit both files. After editing <code>_config.yml</code>, you need to run <code>make serve</code> again to
see the changes take effect locally.
</div>
{% endif %}


<h2 id="general">Information générale</h2>

{% comment %}
INTRODUCTION

Edit the general explanatory paragraph below if you want to change
the pitch.
{% endcomment %}
{% if page.carpentry == "swc" %}
{% include sc/intro.html %}
{% elsif page.carpentry == "dc" %}
{% include dc/intro.html %}
{% elsif page.carpentry == "lc" %}
{% include lc/intro.html %}
{% endif %}

{% comment %}
AUDIENCE

Explain who your audience is.  (In particular, tell readers if the
workshop is only open to people from a particular institution.
{% endcomment %}
{% if page.carpentry == "swc" %}
{% include sc/who.html %}
{% elsif page.carpentry == "dc" %}
{% include dc/who.html %}
{% elsif page.carpentry == "lc" %}
{% include lc/who.html %}
{% endif %}

{% comment %}
LOCATION

This block displays the address and links to maps showing directions
if the latitude and longitude of the workshop have been set.  You
can use https://itouchmap.com/latlong.html to find the lat/long of an
address.
{% endcomment %}
{% if page.latlng %}
<p id="where">
  <strong>Où:</strong>
  {{page.address}}.
  Obtenez l’itinéraire avec
  <a href="//www.openstreetmap.org/?mlat={{page.latlng | replace:',','&mlon='}}&zoom=16">OpenStreetMap</a>
  ou
  <a href="//maps.google.com/maps?q={{page.latlng}}">Google Maps</a>.
</p>
{% endif %}

{% comment %}
DATE

This block displays the date and links to Google Calendar.
{% endcomment %}
{% if page.humandate %}
<p id="when">
  <strong>Quand:</strong>
  {{page.humandate}}.
  {% include workshop_calendar.html %}
</p>
{% endif %}

{% comment %}
SPECIAL REQUIREMENTS

Modify the block below if there are any special requirements.
{% endcomment %}
<p id="requirements">
  <strong>Exigences:</strong> Les participants doivent apporter leur ordinateur, fonctionnant
  macOS, Linux, ou Windows (pas de tablette, ni Chromebook, etc.) et possédant les droits d’administration. Certaines logiciels peuvent être installés (voir liste <a href="#setup">plus bas</a>).
</p>

{% comment%}
CODE OF CONDUCT
{% endcomment %}
<p id="code-of-conduct">
<strong>Code de conduite:</strong>  Chaque participant aux activités Carpentries doivent se respecter le <a href="https://docs.carpentries.org/topic_folders/policies/code-of-conduct.html">Code de Conduite</a>. Ce document explique en outre comment rapporter un incident, si nécessaire.
</p>


{% comment %}
ACCESSIBILITY

Modify the block below if there are any barriers to accessibility or
special instructions.
{% endcomment %}
<p id="accessibility">
  <strong>Accessibilité:</strong> Nous nous sommes engagés à rendre nos atelier accessibles à tous.
  L’organisateur de cet atelier a vérifié que:
</p>
<ul>
  <li>La pièce (le cas échéant) est accessible aux fauteuils roulants.</li>
  <li>Des toilettes accessibles sont disponibles.</li>
</ul>
<p>
  Les documents seront fournis avant l’atelier et et des documents en gros caractères sont disponibles si nécessaire en prévenant les organisateurs à l’avance. Si nous pouvons vous aider à rendre l’apprentissage plus facile pour vous (par exemple, interprètes en langue des signes, installations d'allaitement), veuillez nous contacter (aux coordonnées ci-dessous) et nous essaierons de vous les fournir.
</p>

{% comment %}
CONTACT EMAIL ADDRESS

Display the contact email address set in the configuration file.
{% endcomment %}
<p id="contact">
  <strong>Contact</strong>:
  Veuillez envoyer un courriel à
  {% if page.email %}
  {% for email in page.email %}
  {% if forloop.last and page.email.size > 1 %}
  or
  {% else %}
  {% unless forloop.first %}
  ,
  {% endunless %}
  {% endif %}
  <a href='mailto:{{email}}'>{{email}}</a>
  {% endfor %}
  {% else %}
  to-be-announced
  {% endif %}
  pour plus d’informations.
</p>

<hr/>

{% comment %}
SURVEYS - DO NOT EDIT SURVEY LINKS
{% endcomment %}
<h2 id="surveys">Sondages</h2>
<p>Veuillez vous assurer de compléter les sondages avant et après l’atelier.</p>
{% if site.carpentry == "swc" %}
<p><a href="{{ site.swc_pre_survey }}{{ site.github.project_title }}">Pre-workshop Survey</a></p>
<p><a href="{{ site.swc_post_survey }}{{ site.github.project_title }}">Post-workshop Survey</a></p>
{% elsif site.carpentry == "dc" %}
<p><a href="{{ site.dc_pre_survey }}{{ site.github.project_title }}">Sondage pré-atelier</a></p>
<p><a href="{{ site.dc_post_survey }}{{ site.github.project_title }}">Sondage post-atelier</a></p>
{% elsif site.carpentry == "lc" %}
<p><a href="{{ site.lc_pre_survey }}{{ site.github.project_title }}">Pre-workshop Survey</a></p>
<p><a href="{{ site.lc_post_survey }}{{ site.github.project_title }}">Post-workshop Survey</a></p>
{% endif %}

<hr/>


{% comment %}
SCHEDULE

Show the workshop's schedule.  Edit the items and times in the table
to match your plans.  You may also want to change 'Day 1' and 'Day
2' to be actual dates or days of the week.
{% endcomment %}
<h2 id="schedule">Horaire</h2>

{% if page.carpentry == "swc" %}
{% include sc/schedule.html %}
{% elsif page.carpentry == "dc" %}
{% include dc/schedule.html %}
{% elsif page.carpentry == "lc" %}
{% include lc/schedule.html %}
{% endif %}

{% comment %}
Collaborative Notes

If you want to use an Etherpad, go to

http://pad.carpentries.org/YYYY-MM-DD-site

where 'YYYY-MM-DD-site' is the identifier for your workshop,
e.g., '2015-06-10-esu'.
{% endcomment %}
{% if page.collaborative_notes %}
<p id="collaborative_notes">
  We will use this <a href="{{page.collaborative_notes}}">collaborative document</a> for chatting, taking notes, and sharing URLs and bits of code.
</p>
{% endif %}

<hr/>

{% comment %}
SYLLABUS

Show what topics will be covered.

1. If your workshop is R rather than Python, remove the comment
around that section and put a comment around the Python section.
2. Some workshops will delete SQL.
3. Please make sure the list of topics is synchronized with what you
intend to teach.
4. You may need to move the div's with class="col-md-6" around inside
the div's with class="row" to balance the multi-column layout.

This is one of the places where people frequently make mistakes, so
please preview your site before committing, and make sure to run
'tools/check' as well.
{% endcomment %}
<h2 id="syllabus">Syllabus</h2>

{% if page.carpentry == "swc" %}
{% include sc/syllabus.html %}
{% elsif page.carpentry == "dc" %}
{% include dc/syllabus.html %}
{% elsif page.carpentry == "lc" %}
{% include lc/syllabus.html %}
{% endif %}

<hr/>

{% comment %}
SETUP

Delete irrelevant sections from the setup instructions.  Each
section is inside a 'div' without any classes to make the beginning
and end easier to find.

This is the other place where people frequently make mistakes, so
please preview your site before committing, and make sure to run
'tools/check' as well.
{% endcomment %}

<h2 id="setup">Préparatifs</h2>

<p>
  Pour participer à un atelier sur la
  {% if page.carpentry == "swc" %}
  Software Carpentry
  {% elsif page.carpentry == "dc" %}
  menuiserie des données (Data Carpentry)
  {% elsif page.carpentry == "lc" %}
  Library Carpentry
  {% endif %}
  workshop,
  vous devrez avoir accès aux logiciels suivants: Notepad++, OpenRefine, R, et RStudio.
  De plus, vous devez avoir accès à un fureteur Web récent et à jour.
</p>

<p>
De plus, vous pouvez installer à votre choix les applications suivantes:
</p>


<div id="shell"> {% comment %} Start of 'shell' section. {% endcomment %}
  <h3>Le Shell Bash</h3>
  <p>
    Bash est un interpréteur de commandes couramment utilisé qui vous permet d'effectuer des tâches simples plus rapidement.
  </p>

  <div>
    <ul class="nav nav-tabs nav-justified" role="tablist">
      <li role="presentation" class="active"><a data-os="windows" href="#shell-windows" aria-controls="Windows" role="tab" data-toggle="tab">Windows</a></li>
      <li role="presentation"><a data-os="macos" href="#shell-macos" aria-controls="MacOS" role="tab" data-toggle="tab">MacOS</a></li>
      <li role="presentation"><a data-os="linux" href="#shell-linux" aria-controls="Linux" role="tab" data-toggle="tab">Linux</a></li>
    </ul>

    <div class="tab-content">
      <article role="tabpanel" class="tab-pane active" id="shell-windows">
        <a href="https://www.youtube.com/watch?v=339AEqk9c-8">Video Tutorial</a>
        <ol>
          <li>Download the Git for Windows <a href="https://git-for-windows.github.io/">installer</a>.</li>
          <li>Run the installer and follow the steps below:
            <ol>
              {% comment %} Git 2.22.0 Setup {% endcomment %}
              <li>
                Click on "Next" four times (two times if you've previously
                installed Git).  You don't need to change anything
                in the Information, location, components, and start menu screens.
              </li>
              <li>
                <strong>
                  Select "Use the nano editor by default" and click on "Next".
                </strong>
              </li>
              {% comment %} Adjusting your PATH environment {% endcomment %}
              <li>
                Keep "Git from the command line and also from 3rd-party software" selected and click on "Next".
                If you forgot to do this programs that you need for the workshop will not work properly.
                If this happens rerun the installer and select the appropriate option.
              </li>
              {% comment %} Choosing the SSH executable {% endcomment %}
              <li>Click on "Next".</li>
              {% comment %} Choosing HTTPS transport backend {% endcomment %}
              <li>Select "Use the native Windows Secure Channel library", and click "Next".</li>
              {% comment %} This should mean that people stuck behind corporate firewalls that do MITM attacks
                                 with their own root CA are still able to access remote git repos. {% endcomment %}
              {% comment %} Configuring the line ending conversions {% endcomment %}
              <li>
                Keep "Checkout Windows-style, commit Unix-style line endings" selected and click on "Next".
              </li>
              {% comment %} Configuring the terminal emulator to use with Git Bash {% endcomment %}
              <li>
                <strong>
                  Select "Use Windows' default console window" and click on "Next".
                </strong>
              </li>
              {% comment %} Configuring extra options {% endcomment %}
              <li>Leave all three items selected, and click on "Next".</li>
              {% comment %} Configuring experimental options {% endcomment %}
              <li>Do not select the experimental option. Click "Install".</li>
              {% comment %} Installing {% endcomment %}
              {% comment %} Completing the Git Setup Wizard {% endcomment %}
              <li>Click on "Finish".</li>
            </ol>
          </li>
          <li>
            If your "HOME" environment variable is not set (or you don't know what this is):
            <ol>
              <li>Open command prompt (Open Start Menu then type <code>cmd</code> and press <kbd>Enter</kbd>)</li>
              <li>
                Type the following line into the command prompt window exactly as shown:
                <p><code>setx HOME "%USERPROFILE%"</code></p>
              </li>
              <li>Press <kbd>Enter</kbd>, you should see <code>SUCCESS: Specified value was saved.</code></li>
              <li>Quit command prompt by typing <code>exit</code> then pressing <kbd>Enter</kbd></li>
            </ol>
          </li>
        </ol>
        <p>This will provide you with both Git and Bash in the Git Bash program.</p>
      </article>
      <article role="tabpanel" class="tab-pane active" id="shell-macos">
        <p>
          The default shell in all versions of macOS is Bash, so no
          need to install anything.  You access Bash from the Terminal
          (found in
          <code>/Applications/Utilities</code>).
          See the Git installation <a href="https://www.youtube.com/watch?v=9LQhwETCdwY ">video tutorial</a>
          for an example on how to open the Terminal.
          You may want to keep
          Terminal in your dock for this workshop.
        </p>
      </article>
      <article role="tabpanel" class="tab-pane active" id="shell-linux">
        <p>
          The default shell is usually Bash, but if your
          machine is set up differently you can run it by opening a
          terminal and typing <code>bash</code>.  There is no need to
          install anything.
        </p>
      </article>
    </div>
  </div>
</div> {% comment %} End of 'shell' section. {% endcomment %}

<div id="git"> {% comment %} Start of 'Git' section. GitHub browser compatibility
  is given at https://help.github.com/articles/supported-browsers/{% endcomment %}
  <h3>Git</h3>
  <p>
    Git est un système de gestion des versions permettant de suivre les modifications faites (qui, quoi et quand) et offre des options facilitant la mise à jour de code partagé ou publique sur <a href="https://github.com/">github.com</a> ou l'équivalent. Vous devez utiliser un des
    <a href="https://help.github.com/articles/supported-browsers/">fureteurs web supportés</a>.
  </p>
  <p>
    Vous devez posséder un compte <a href="https://github.com/">github.com</a>
    pour certaines des parties de la formation. Le compte de base GitHub est gratuit. Nous vous encourageons à créer un compte GitHub si vous n’en avez pas un.
    Prendre en considération quelles informations personnelles vous souhaitez voir divulguer. Par exemple,
    vous pouvez consulter ces
    <a href="https://help.github.com/articles/keeping-your-email-address-private/">instructions
      pour ne pas divulguer votre adresse courriel</a> utilisée pour GitHub.
  </p>

  <div>
    <ul class="nav nav-tabs nav-justified" role="tablist">
      <li role="presentation" class="active"><a data-os="windows" href="#git-windows" aria-controls="Windows" role="tab" data-toggle="tab">Windows</a></li>
      <li role="presentation"><a data-os="macos" href="#git-macos" aria-controls="MacOS" role="tab" data-toggle="tab">MacOS</a></li>
      <li role="presentation"><a data-os="linux" href="#git-linux" aria-controls="Linux" role="tab" data-toggle="tab">Linux</a></li>
    </ul>

    <div class="tab-content">
      <article role="tabpanel" class="tab-pane active" id="git-windows">
        <p>
          Git should be installed on your computer as part of your Bash
          install (described above).
        </p>
      </article>
      <article role="tabpanel" class="tab-pane active" id="git-macos">
        <a href="https://www.youtube.com/watch?v=9LQhwETCdwY ">Video Tutorial</a>
        <p>
          <strong>For OS X 10.9 and higher</strong>, install Git for Mac
          by downloading and running the most recent "mavericks" installer from
          <a href="http://sourceforge.net/projects/git-osx-installer/files/">this list</a>.
          Because this installer is not signed by the developer, you may have to
          right click (control click) on the .pkg file, click Open, and click
          Open on the pop up window.
          After installing Git, there will not be anything in your <code>/Applications</code> folder,
          as Git is a command line program.
          <strong>For older versions of OS X (10.5-10.8)</strong> use the
          most recent available installer labelled "snow-leopard"
          <a href="http://sourceforge.net/projects/git-osx-installer/files/">available here</a>.
        </p>
      </article>
      <article role="tabpanel" class="tab-pane active" id="git-linux">
        <p>
          If Git is not already available on your machine you can try to
          install it via your distro's package manager. For Debian/Ubuntu run
          <code>sudo apt-get install git</code> and for Fedora run
          <code>sudo dnf install git</code>.
        </p>
      </article>
    </div>
  </div>
</div> {% comment %} End of 'Git' section. {% endcomment %}

<div id="editor"> {% comment %} Start of 'editor' section. {% endcomment %}
  <h3>Éditeur de texte</h3>

  <p>
    Lorsque vous écrivez du code, il est agréable d’avoir un éditeur de texte qui est optimisé
    pour l'écriture de code, avec des fonctions telles que le codage couleur automatique des mots clés.
  </p>

  <div>
    <ul class="nav nav-tabs nav-justified" role="tablist">
      <li role="presentation" class="active"><a data-os="windows" href="#editor-windows" aria-controls="Windows" role="tab" data-toggle="tab">Windows</a></li>
      <li role="presentation"><a data-os="macos" href="#editor-macos" aria-controls="MacOS" role="tab" data-toggle="tab">MacOS</a></li>
      <li role="presentation"><a data-os="linux" href="#editor-linux" aria-controls="Linux" role="tab" data-toggle="tab">Linux</a></li>
    </ul>

    <div class="tab-content">
      <article role="tabpanel" class="tab-pane active" id="editor-windows">
        <p>
          nano is a basic editor and the default that instructors use in the workshop.
          It is installed along with Git.
        </p>
        <p>
          Others editors that you can use are
          <a href="https://notepad-plus-plus.org/">Notepad++</a> or
          <a href="https://www.sublimetext.com/">Sublime Text</a>.
          <strong>Be aware that you must
            add its installation directory to your system path.</strong>
          Please ask your instructor to help you do this.
        </p>
      </article>
      <article role="tabpanel" class="tab-pane active" id="editor-macos">
        <p>
          nano is a basic editor and the default that instructors use in the workshop.
          See the Git installation <a href="https://www.youtube.com/watch?v=9LQhwETCdwY ">video tutorial</a>
          for an example on how to open nano.
          It should be pre-installed.
        </p>
        <p>
          Others editors that you can use are
          <a href="https://www.barebones.com/products/bbedit/">BBEdit</a> or
          <a href="https://www.sublimetext.com/">Sublime Text</a>.
        </p>
      </article>
      <article role="tabpanel" class="tab-pane active" id="editor-linux">
        <p>
          nano is a basic editor and the default that instructors use in the workshop.
          It should be pre-installed.
        </p>
        <p>
          Others editors that you can use are
          <a href="https://wiki.gnome.org/Apps/Gedit">Gedit</a>,
          <a href="https://kate-editor.org/">Kate</a> or
          <a href="https://www.sublimetext.com/">Sublime Text</a>.
        </p>
      </article>
    </div>
  </div>
</div> {% comment %} End of 'editor' section. {% endcomment %}


<div id="r"> {% comment %} Start of 'R' section. {% endcomment %}
  <h3>R</h3>

  <p>
    <a href="https://www.r-project.org">R</a> est un langage de programmation spécialement
    conçu pour l'exploration, la visualisation et l'analyse statistique de données.
    Pour intéragir avec R, nous utilisons
    <a href="https://www.rstudio.com/">RStudio</a>.
  </p>

  <div>
    <ul class="nav nav-tabs nav-justified" role="tablist">
      <li role="presentation" class="active"><a data-os="windows" href="#rstats-windows" aria-controls="Windows" role="tab" data-toggle="tab">Windows</a></li>
      <li role="presentation"><a data-os="macos" href="#rstats-macos" aria-controls="MacOS" role="tab" data-toggle="tab">MacOS</a></li>
      <li role="presentation"><a data-os="linux" href="#rstats-linux" aria-controls="Linux" role="tab" data-toggle="tab">Linux</a></li>
    </ul>

    <div class="tab-content">
      <article role="tabpanel" class="tab-pane active" id="rstats-windows">
        <a href="https://www.youtube.com/watch?v=q0PjTAylwoU">Video Tutorial</a>
        <p>
          Install R by downloading and running
          <a href="https://cran.r-project.org/bin/windows/base/release.htm">this .exe file</a>
          from <a href="https://cran.r-project.org/index.html">CRAN</a>.
          Also, please install the
          <a href="https://www.rstudio.com/products/rstudio/download/#download">RStudio IDE</a>.
          Note that if you have separate user and admin accounts, you should run the
          installers as administrator (right-click on .exe file and select "Run as
          administrator" instead of double-clicking). Otherwise problems may occur later,
          for example when installing R packages.
        </p>
      </article>
      <article role="tabpanel" class="tab-pane active" id="rstats-macos">
        <a href="https://www.youtube.com/watch?v=5-ly3kyxwEg">Video Tutorial</a>
        <p>
          Install R by downloading and running
          <a href="https://cran.r-project.org/bin/macosx/R-latest.pkg">this .pkg file</a>
          from <a href="https://cran.r-project.org/index.html">CRAN</a>.
          Also, please install the
          <a href="https://www.rstudio.com/products/rstudio/download/#download">RStudio IDE</a>.
        </p>
      </article>
      <article role="tabpanel" class="tab-pane active" id="rstats-linux">
        <p>
          You can download the binary files for your distribution
          from <a href="https://cran.r-project.org/index.html">CRAN</a>. Or
          you can use your package manager (e.g. for Debian/Ubuntu
          run <code>sudo apt-get install r-base</code> and for Fedora run
          <code>sudo dnf install R</code>).  Also, please install the
          <a href="https://www.rstudio.com/products/rstudio/download/#download">RStudio IDE</a>.
        </p>
      </article>
    </div>
  </div>
</div> {% comment %} End of 'R' section. {% endcomment %}


<div id="openrefine"> {% comment %} Start of 'OpenRefine' section. {% endcomment %}
  <h3>OpenRefine</h3>
  <p>
    Vous aurez besoin dans cet atelier d’<em>OpenRefine</em> et d’un fureteur Web. <em>Note:</em> il s’agit d’un programme Java qui s’exécute sur votre ordinateur (et non en ligne), dans votre fureteur Web,
    mais sans connexion à internet.
  </p>

  <div>
    <ul class="nav nav-tabs nav-justified" role="tablist">
      <li role="presentation" class="active"><a data-os="windows" href="#openrefine-windows" aria-controls="Windows" role="tab" data-toggle="tab">Windows</a></li>
      <li role="presentation"><a data-os="macos" href="#openrefine-macos" aria-controls="MacOS" role="tab" data-toggle="tab">MacOS</a></li>
      <li role="presentation"><a data-os="linux" href="#openrefine-linux" aria-controls="Linux" role="tab" data-toggle="tab">Linux</a></li>
    </ul>

    <div class="tab-content">
      <article role="tabpanel" class="tab-pane active" id="openrefine-windows">
        <p>
          Check that you have either the Firefox or the Chrome browser installed and set as your default browser.
          <strong>OpenRefine runs in your default browser.</strong>
          It will not run correctly in Internet Explorer.
        </p>
        <p>Download software from <a href="http://openrefine.org/">http://openrefine.org/</a></p>
        <p>Create a new directory called OpenRefine.</p>
        <p>Unzip the downloaded file into the OpenRefine directory by right-clicking and selecting "Extract ...". </p>
        <p>Go to your newly created OpenRefine directory.</p>
        <p>Launch OpenRefine by clicking <code>openrefine.exe</code> (this will launch a command prompt window, but you can ignore that - just wait for OpenRefine to open in the browser).</p>
        <p>If you are using a different browser, or if OpenRefine does not automatically open for you, point your browser at <a href="http://127.0.0.1:3333/">http://127.0.0.1:3333/</a> or <a href="http://localhost:3333">http://localhost:3333</a> to use the program.</p>
      </article>
      <article role="tabpanel" class="tab-pane active" id="openrefine-macos">
        <p>Check that you have either the Firefox or the Chrome browser installed and set as your default browser. <strong>OpenRefine runs in your default browser.</strong> It may not run correctly in Safari.</p>
        <p>Download software from <a href="http://openrefine.org/">http://openrefine.org/</a>.</p>
        <p>Create a new directory called OpenRefine.</p>
        <p>Unzip the downloaded file into the OpenRefine directory by double-clicking it.</p>
        <p>Go to your newly created OpenRefine directory.</p>
        <p>Launch OpenRefine by dragging the icon into the Applications folder.</p>
        <p>Use <code>Ctrl-click/Open ... </code> to launch it.</p>
        <p>If you are using a different browser, or if OpenRefine does not automatically open for you, point your browser at <a href="http://127.0.0.1:3333/">http://127.0.0.1:3333/</a> or <a href="http://localhost:3333">http://localhost:3333</a> to use the program.</p>
      </article>
      <article role="tabpanel" class="tab-pane active" id="openrefine-linux">
        <p>Check that you have either the Firefox or the Chrome browser installed and set as your default browser. <strong>OpenRefine runs in your default browser.</strong></p>
        <p>Download software from <a href="http://openrefine.org/">http://openrefine.org/</a>.</p>
        <p>Make a directory called OpenRefine.</p>
        <p>Unzip the downloaded file into the OpenRefine directory.</p>
        <p>Go to your newly created OpenRefine directory.</p>
        <p>Launch OpenRefine by entering <code>./refine</code> into the terminal within the OpenRefine directory.</p>
        <p>If you are using a different browser, or if OpenRefine does not automatically open for you, point your browser at <a href="http://127.0.0.1:3333/">http://127.0.0.1:3333/</a> or <a href="http://localhost:3333">http://localhost:3333</a> to use the program.</p>
      </article>
    </div>
  </div>
</div> {% comment %} End of 'OpenRefine' section. {% endcomment %}

{% comment %}
<div id="vm">
  <h3>Virtual Machine</h3>

  <p>
    Some instructors prefer to have learners use a virtual machine (VM)
    rather than install software on their own computers.  If your
    instructors have chosen to do this, please:
  </p>
  <ol>
    <li>
      Install <a href="https://www.virtualbox.org/">VirtualBox</a>.
    </li>
    <li>
      Download our <a href="{{site.swc_vm}}">VM image</a>.
      <strong>Warning:</strong> this file is 1.7 GByte, so please
      download it <em>before</em> coming to your workshop.
    </li>
    <li>
      Load the VM into VirtualBox by selecting "Import Appliance" and
      loading the <code>.ova</code> file.
    </li>
  </ol>
</div>
{% endcomment %}
