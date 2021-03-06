.. _settings:

Settings
========

The settings dialog can be invoked at any time by selecting ``Settings`` from the ``Tools`` menu option.

.. image:: /images/settings/settings.png

The following buttons are always available on any page of the Settings dialog. Sometimes the ``Cancel``
button has no effect for the page - this will be noted on the page in the area next to the buttons.

+-------------------------------+--------------------------------------------------------------------------+
| Button                        | Description                                                              |
+===============================+==========================================================================+
|``OK``                         | Save any entered changes made in *any* settings page and close the       |
|                               | Settings dialog.                                                         |
+-------------------------------+--------------------------------------------------------------------------+
|``Cancel``                     | Any entered changes in *any* settings page are *not* saved. The Settings |
|                               | dialog is closed.                                                        |
+-------------------------------+--------------------------------------------------------------------------+
|``Apply``                      | Any entered changes in *any* settings page are saved.                    |
+-------------------------------+--------------------------------------------------------------------------+

Settings that are specific to Git Extensions and apply globally will be stored in a file called ``GitExtensions.settings``
either in the user's application data path or with the program.
The location is dependant on the IsPortable setting in the ``GitExtensions.exe.config`` file that is with the program.
Settings that are specific to Git Extensions but apply to only the current repository will be stored in a file of the same
name, ``GitExtensions.settings``, but in either the root folder of the repository or the ``.git`` folder of the repository,
depending on whether or not they are distributed with that repository.
The settings that are used by Git are stored in the configuration files of Git. The global settings are stored in the file called
``.gitconfig`` in the user directory. The local settings are stored in the ``.git\config`` file of the repository.

.. _settings-checklist:

Checklist
---------

This page is a visual overview of the minimal settings that Git Extensions requires to work properly. Any items highlighted in red should
be configured by clicking on the highlighted item.

This page contains the following settings and buttons.

+---------------------------------------------------+----------------------------------------------------------------------------+
| Setting                                           | Description                                                                |
+===================================================+============================================================================+
|Check settings at startup (disables automatically  | Forces Git Extensions to re-check the minimal set of required settings     |
|if all settings are correct)                       | the next time Git Extensions is started. If all settings are 'green' this  |
|                                                   | will be automatically unchecked.                                           |
+---------------------------------------------------+----------------------------------------------------------------------------+
|``Save and rescan`` button                         | Saves any setting changes made and re-checks the settings to see if the    |
|                                                   | minimal requirements are now met.                                          |
+---------------------------------------------------+----------------------------------------------------------------------------+

.. _settings-git:

Git
---

This page contains the settings needed to access git repositories. The repositories will be accessed using external
tools. For Windows usually "Git for Windows" or Cygwin are used. Git Extensions will try to configure these settings automatically.

+-------------+-------------------------------------+----------------------------------------------------------------------------+
|Group        | Setting                             | Description                                                                |
+=============+=====================================+============================================================================+
|Git          |Command used to run git (git.cmd or  | Needed for Git Extensions to run Git commands. Set the full command used   |
|             |git.exe)                             | to run git ("Git for Windows" or Cygwin). Use the ``Browse`` button to     |
|             |                                     | find the executable on your file                                           |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Path to Linux tools (sh). Leave empty| A few linux tools are used by Git Extensions. When Git for Windows is      |
|             |when it is in the path.              | installed, these tools are located in the bin directory of Git for         |
|             |                                     | Windows. Use the ``Browse`` button to find the directory on your file      |
|             |                                     | system.                                                                    |
+-------------+-------------------------------------+----------------------------------------------------------------------------+
|Environment  |``Change HOME`` button               | This button opens a dialog where the HOME directory can be changed.        |
+-------------+-------------------------------------+----------------------------------------------------------------------------+

The global configuration file used by git will be put in the HOME directory. On some systems the home directory is not set
or is pointed to a network drive. Git Extensions will try to detect the optimal setting for your environment. When there is
already a global git configuration file, this location will be used. If you need to relocate the home directory for git,
click the ``Change HOME`` button to change this setting. Otherwise leave this setting as the default.

.. _settings-git-extensions:

Git Extensions
--------------

This page contains general settings for Git Extensions.

+-------------+-------------------------------------+----------------------------------------------------------------------------+
|Group        | Setting                             | Description                                                                |
+=============+=====================================+============================================================================+
|Performance  |Show repository status in browse     | When enabled, the number of pending commits are shown on the toolbar as a  |
|             |dialog (number of changes in toolbar,| figure in parentheses next to the ``Commit`` button. Git Extensions must be|
|             |restart required)                    | stopped and restarted to activate changes to this option.                  |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Show current working dir changes in  | When enabled, two extra revisions are added to the revision graph. The     |
|             |revision graph                       | first shows the current working directory status. The second shows the     |
|             |                                     | staged files. This option can cause slowdowns when browsing large          |
|             |                                     | repositories.                                                              |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Use FileSystemWatcher to check if    | Using the FileSystemWatcher to check index state improves the performance  |
|             |index is changed                     | in some cases. Turn this off if you experience refresh problems in commit  |
|             |                                     | log.                                                                       |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Show stash count on status bar in    | When you use the stash a lot, it can be useful to show the number of       |
|             |browse window                        | stashed items on the toolbar. This option causes serious slowdowns in large|
|             |                                     | repositories and is turned off by default.                                 |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Check for uncommitted changes in     | Git Extensions will not allow you to checkout a branch if you have         |
|             |checkout branch dialog               | uncommitted changes on the current branch. If you select this option, Git  |
|             |                                     | Extensions will display a dialog where you can decide what to do with      |
|             |                                     | uncommitted changes before swapping branches.                              |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Limit number of commits that will be | This number specifies the maximum number of commits that Git Extensions    |
|             |loaded in list at start-up           | will load when it is started. These commits are shown in the Commit Log    |
|             |                                     | window. To see more commits than are loaded, then this setting will need   |
|             |                                     | to be adjusted and Git Extensions restarted.                               |
+-------------+-------------------------------------+----------------------------------------------------------------------------+
|Behaviour    |Close Process dialog when process    | When a process is finished, close the process dialog automatically. Leave  |
|             |succeeds                             | this option off if you want to see the result of processes. When a process |
|             |                                     | has failed, the dialog will automatically remain open.                     |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Show console window when executing   | Git Extensions uses command line tools to access the git repository. In    |
|             |git process                          | some environments it might be useful to see the command line dialog when a |
|             |                                     | process is executed. An option on the command line dialog window displayed |
|             |                                     | allows this setting to be turned off.                                      |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Use patience diff algorithm          | Use the Git 'patience diff' algorithm instead of the default. This         |
|             |                                     | algorithm is useful in situations where two files have diverged            |
|             |                                     | significantly and the default algorithm may become 'misaligned', resulting |
|             |                                     | in a totally unusable conflict file.                                       |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Include untracked files in stash     | If checked, when a stash is performed as a result of any action except a   |
|             |                                     | manual stash request, e.g. checking out a new branch and requesting a stash|
|             |                                     | then any files not tracked by git will also be saved to the stash.         |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Follow renames in file history       | Try to follow file renames in the file history.                            |
|             |(experimental)                       |                                                                            |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Open last working dir on startup     | When starting Git Extensions, open the last used repository (bypassing the |
|             |                                     | Start Page).                                                               |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Play Special Startup Sound           | Play a sound when starting Git Extensions. It will put you in a good       |
|             |                                     | moooooood!                                                                 |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Default clone destination            | Git Extensions will pre-fill destination directory input with value of this|
|             |                                     | setting on any form used to perform repository clone.                      |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Revision grid quick search timeout   | The timeout (milliseconds) used for the quick search feature in the        |
|             |[ms]                                 | revision graph. The quick search will be enabled when you start typing and |
|             |                                     | the revision graph has the focus.                                          |
+-------------+-------------------------------------+----------------------------------------------------------------------------+
|Email        |SMTP server name                     | SMTP server to use for sending patches.                                    |
|settings for +-------------------------------------+----------------------------------------------------------------------------+
|sending      |Port                                 | SMTP port number to use.                                                   |
|patches      +-------------------------------------+----------------------------------------------------------------------------+
|             |Use SSL/TLS                          | Check this box if the SMTP server uses SSL or TLS.                         |
+-------------+-------------------------------------+----------------------------------------------------------------------------+

.. _settings-commit-dialog:

Commit dialog
-------------

This page contains settings for the Git Extensions Commit dialog.

+-------------+-------------------------------------+----------------------------------------------------------------------------+
|Group        | Setting                             | Description                                                                |
+=============+=====================================+============================================================================+
|Behaviour    |Show errors when staging files       | If an error occurs when files are staged (in the Commit dialog), then the  |
|             |                                     | process dialog showing the results of the git command is shown if this     |
|             |                                     | setting is checked.                                                        |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Compose commit messages in Commit    | If this is unchecked, then commit messages cannot be entered in the commit |
|             |dialog (otherwise the message will be| dialog. When the ``Commit`` button is clicked, a new editor window is      |
|             |requested during commit)             | opened where the commit message can be entered.                            |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Number of previous messages in commit| The number of commit messages, from the top of the current branch, that    |
|             |dialog                               | will be made available from the ``Commit message`` combo box on the Commit |
|             |                                     | dialog.                                                                    |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Show additional buttons in commit    | Tick the boxes in this sub-group for any of the additional buttons that you|
|             |button area                          | wish to have available below the commit button. These buttons are          |
|             |                                     | considered additional to basic functionality and have consequences if you  |
|             |                                     | should click them accidentally, including resetting unrecorded work.       |
+-------------+-------------------------------------+----------------------------------------------------------------------------+

.. _settings-appearance:

Appearance
----------

This page contains settings that affect the appearance of the application.

+-------------+-------------------------------------+----------------------------------------------------------------------------+
|Group        | Setting                             | Description                                                                |
+=============+=====================================+============================================================================+
|General      |Show relative date instead of full   | Show relative date, e.g. 2 weeks ago, instead of full date.                |
|             |date                                 | Displayed on the ``commit`` tab on the main Commit Log window.             |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Show current branch in Visual Studio | Determines whether or not the currently checked out branch is displayed on |
|             |                                     | the Git Extensions toolbar within Visual Studio.                           |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Auto scale user interface when high  | Automatically resize controls and their contents according to the current  |
|             |DPI is used                          | system resolution of the display, measured in dots per inch (DPI).         |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Truncate long filenames              | This setting affects the display of filenames in a component of a window   |
|             |                                     | e.g. in the Diff tab of the Commit Log window. The options that can be     |
|             |                                     | selected are:                                                              |
|             |                                     |                                                                            |
|             |                                     | | ``None``: no truncation occurs; a horizontal scroll bar is used to see   |
|             |                                     |   the whole filename.                                                      |
|             |                                     | | ``Compact``: no horizontal scroll bar. Filenames are truncated at both   |
|             |                                     |   start and end to fit into the width of the display component.            |
|             |                                     | | ``Trimstart``: no horizontal scroll bar. Filenames are truncated at the  |
|             |                                     |   start only.                                                              |
|             |                                     | | ``FileNameOnly``: the path is always removed, leaving only the name of   |
|             |                                     |   the file, even if there is space for the path.                           |
+-------------+-------------------------------------+----------------------------------------------------------------------------+
|Author images|Get author image from gravatar.com   | If checked, `gravatar <http://gravatar.com/>`_ will be accessed to         |
|             |                                     | retrieve an image for the author of commits. This image is displayed on    |
|             |                                     | the ``commit`` tab on the main Commit Log window.                          |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Image size                           | The display size of the user image.                                        |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Cache images                         | The number of days to elapse before gravatar is checked for any changes to |
|             |                                     | an authors image.                                                          |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |No image service                     | If the author has not set up their own image, then gravatar can return an  |
|             |                                     | image based on one of these services.                                      |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |``Clear image cache`` button         | Clear the cached avatars.                                                  |
+-------------+-------------------------------------+----------------------------------------------------------------------------+
|Fonts        |Code font                            | Change the font used for the display of file contents.                     |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Application font                     | Change the font used on Git Extensions windows and dialogs.                |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Commit font                          | Change the font used for entering a commit message in the Commit dialog.   |
+-------------+-------------------------------------+----------------------------------------------------------------------------+
|Language     |Language (restart required)          | Choose the language for the Git Extensions interface.                      |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Dictionary for spelling checker      | Choose the dictionary to use for the spelling checker in the Commit dialog.|
+-------------+-------------------------------------+----------------------------------------------------------------------------+

.. _revision-links:

Revision Links
--------------

You can configure here how to convert parts of a revision into clickable links. These links will be located under the commit message on the ``Commit``
tab in the ``Related links`` section.

+---------------------------------------------------+----------------------------------------------------------------------------+
| Setting                                           | Description                                                                |
+===================================================+============================================================================+
|Categories                                         | Lists all the currently defined Categories. Click the ``Add`` button to    |
|                                                   | add a new empty Category. The default name is 'new'.  To remove a Category |
|                                                   | select it and click the ``Remove`` button.                                 |
+---------------------------------------------------+----------------------------------------------------------------------------+
|Name                                               | This is the Category name used to match the same categories defined on     |
|                                                   | different levels of the Settings.                                          |
+---------------------------------------------------+----------------------------------------------------------------------------+
|Enabled                                            | Indicates whether the Category is enabled or not. Disabled categories are  |
|                                                   | skipped while creating links.                                              |
+---------------------------------------------------+----------------------------------------------------------------------------+
|Search in                                          | List of revision parts that will be checked when searching for matching    |
|                                                   | text to be converted into links. Only the checked parts will be searched   |
|                                                   | for matches.                                                               |
+---------------------------------------------------+----------------------------------------------------------------------------+
|Search pattern/Nested pattern                      | Regular expression used for matching text in chosen revision parts.        |
|                                                   | Each matched fragment will be used to create a new link. More than one     |
|                                                   | fragment can be used in a single link by using a capturing group.          |
|                                                   | A capturing group value can be passed to a link by using zero-based indexed|
|                                                   | placeholders in a link format definition e.g. {0}. ``Nested pattern`` can  |
|                                                   | be used when only part of the text matched by the ``Search pattern``       |
|                                                   | should be used to format the link. When the ``Nested pattern`` is empty,   |
|                                                   | matches found by the ``Search pattern`` are used to create links.          |
+---------------------------------------------------+----------------------------------------------------------------------------+
|Links: Caption/URI                                 | List of links to be created from a single match. Each link consists of     |
|                                                   | the ``Caption`` to be displayed and the ``URI`` to be opened when the link |
|                                                   | is clicked on. In addition to the standard zero-based indexed placeholders,|
|                                                   | the ``%COMMIT_HASH%`` placeholder can be used to put the commit's hash into|
|                                                   | the link. For example:                                                     |
|                                                   | ``https://github.com/gitextensions/gitextensions/commit/%COMMIT_HASH%``    |
+---------------------------------------------------+----------------------------------------------------------------------------+

.. _settings-colors:

Colors
------

This page contains settings to define the colors used in the application.

+-------------+-------------------------------------+----------------------------------------------------------------------------+
|Group        | Setting                             | Description                                                                |
+=============+=====================================+============================================================================+
|Revision     |Multicolor branches                  | Displays branch commits in different colors if checked. If unchecked,      |
|graph        |                                     | all branches are shown in the same color. This color can be selected.      |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Striped branch change                | When a new branch is created from an existing branch, the common part of   |
|             |                                     | the history is shown in a 'hatch' pattern.                                 |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Draw branch borders                  | Outlines branch commits in a black border if checked.                      |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Draw non relatives graph gray        | Show commit history in gray for branches not related to the current branch.|
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Draw non relatives text gray         | Show commit text in gray for branches not related to the current branch.   |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Color tag                            | Color to show tags in.                                                     |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Color branch                         | Color to show branch names in.                                             |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Color remote branch                  | Color to show remote branch names in.                                      |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Color other label                    | Color to show other labels in.                                             |
+-------------+-------------------------------------+----------------------------------------------------------------------------+
|Application  |Icon style                           | Change icons. Useful for recognising various open instances.               |
|Icon         +-------------------------------------+----------------------------------------------------------------------------+
|             |Icon color                           | Changes color of the selected icons.                                       |
+-------------+-------------------------------------+----------------------------------------------------------------------------+
|Difference   |Color removed line                   | Highlight color for lines that have been removed.                          |
|View         |                                     |                                                                            |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Color added line                     | Highlight color for lines that have been added.                            |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Color removed line highlighting      | Highlight color for characters that have been removed in lines.            |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Color added line highlighting        | Highlight color for characters that have been added in lines.              |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Color section                        | Highlight color for a section.                                             |
+-------------+-------------------------------------+----------------------------------------------------------------------------+

.. _settings-start-page:

Start Page
----------

This page allows you to add/remove or modify the Categories and repositories that will appear on the Start Page when Git Extensions is
launched. Per Category you can either configure an RSS feed or add repositories. The order of both Categories, and repositories within
Categories, can be changed using the context menus in the Start Page. See :ref:`start-page` for further details.

+---------------------------------------------------+----------------------------------------------------------------------------+
| Setting                                           | Description                                                                |
+===================================================+============================================================================+
|Categories                                         | Lists all the currently defined Categories. Click the ``Add`` button to    |
|                                                   | add a new empty Category. The default name is 'new'.  To remove a Category |
|                                                   | select it and click Remove. This will delete the Category *and* any        |
|                                                   | repositories belonging to that Category.                                   |
+---------------------------------------------------+----------------------------------------------------------------------------+
|Caption                                            | This is the Category name displayed on the Start Page.                     |
+---------------------------------------------------+----------------------------------------------------------------------------+
|Type                                               | Specify the type: an RSS feed or a repository.                             |
+---------------------------------------------------+----------------------------------------------------------------------------+
|RSS Feed                                           | Enter the URL of the RSS feed.                                             |
+---------------------------------------------------+----------------------------------------------------------------------------+
|Path/Title/Description                             | For each repository defined for a Category, shows the path, title and      |
|                                                   | description. To add a new repository, click on a blank line and type the   |
|                                                   | appropriate information. The contents of the Path field are shown on the   |
|                                                   | Start Page as a link to your repository *if* the Title field is blank. If  |
|                                                   | the Title field is non-blank, then this text is shown as the link to your  |
|                                                   | repository. Any text in the Description field is shown underneath the      |
|                                                   | repository link on the Start Page.                                         |
+---------------------------------------------------+----------------------------------------------------------------------------+

An RSS Feed can be useful to follow repositories on GitHub for example. See this page on GitHub: https://help.github.com/articles/about-your-profile/.
You can also follow commits on public GitHub repositories by

1) In your browser, navigate to the public repository on GitHub.
2) Select the branch you are interested in.
3) Click on the Commits tab.
4) You will find a RSS icon next to the words "Commit History".
5) Copy the link
6) Paste the link into the RSS Feed field in the Settings - Start Page as shown above.

Your Start Page will then show each commit - clicking on a link will open your browser and take you to the commit on GitHub.

.. _settings-git-config:
.. _settings-global-settings:
.. _settings-local-settings:

Git Config
----------

This page contains some of the settings of Git that are used by and therefore can be changed from within Git Extensions.

If you change a Git setting from the Git command line using ``git config`` then the same change in setting can be seen inside
Git Extensions. If you change a Git setting from inside Git Extensions then that change can be seen using ``git config --get``.

Git configuration can be global or local configuration. Global configuration applies to all repositories. Local configuration overrides
the global configuration for the current repository.

+-------------+-------------------------------------+----------------------------------------------------------------------------+
|Group        | Setting                             | Description                                                                |
+=============+=====================================+============================================================================+
|             |User name                            | User name shown in commits and patches.                                    |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |User email                           | User email shown in commits and patches.                                   |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Editor                               | Editor that git.exe opens (e.g. for editing commit message). This is not   |
|             |                                     | used by Git Extensions, only when you call git.exe from the command line.  |
|             |                                     | By default Git will use the built in editor.                               |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Mergetool                            | Merge tool used to solve merge conflicts. Git Extensions will search for   |
|             |                                     | common merge tools on your system.                                         |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Path to mergetool                    | Path to merge tool. Git Extensions will search for common merge tools on   |
|             |                                     | your system.                                                               |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Mergetool command                    | Command that Git uses to start the merge tool. Git Extensions will try to  |
|             |                                     | set this automatically when a merge tool is chosen. This setting can be    |
|             |                                     | left empty when Git supports the mergetool (e.g. kdiff3).                  |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Keep backup (.orig) after merge      | Check to save the state of the original file before modifying to solve     |
|             |                                     | merge conflicts. Refer to Git configuration setting                        |
|             |                                     | ```mergetool.keepBackup```.                                                |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Difftool                             | Diff tool that is used to show differences between source files. Git       |
|             |                                     | Extensions will search for common diff tools on your system.               |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Path to difftool                     | The path to the diff tool. Git Extensions will search for common diff tools|
|             |                                     | on your system.                                                            |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |DiffTool command                     | Command that Git uses to start the diff tool. This setting should only be  |
|             |                                     | filled in when Git doesn't support the diff tool.                          |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Path to commit template              | A path to a file whose contents are used to pre-populate the commit message|
|             |                                     | in the commit dialog.                                                      |
+-------------+-------------------------------------+----------------------------------------------------------------------------+
|Line endings |Checkout/commit radio buttons        |Choose how git should handle line endings when checking out and checking in |
|             |                                     |files. Refer to                                                             |
|             |                                     |https://help.github.com/articles/dealing-with-line-endings/#platform-all    |
+-------------+-------------------------------------+----------------------------------------------------------------------------+
|             |Files content encoding               | The default encoding for file contents.                                    |
+-------------+-------------------------------------+----------------------------------------------------------------------------+

.. _settings-build-server-integration:

Build server integration
------------------------

This page allows you to configure the integration with build servers. This allows the build status of each commit
to be displayed directly in the revision log, as well as providing a tab for direct access to the Build Server
build report for the selected commit.

+-------------+-----------------------------------------+----------------------------------------------------------------------------+
|Group        | Setting                                 | Description                                                                |
+=============+=========================================+============================================================================+
|General      |Enable build server integration          | Check to globally enable/disable the integration functionality.            |
|             +-----------------------------------------+----------------------------------------------------------------------------+
|             |Show build status summary in revision log| Check to show a summary of the build results with the commits in the main  |
|             |                                         | revision log.                                                              |
|             +-----------------------------------------+----------------------------------------------------------------------------+
|             |Build server type                        | Select an integration target.                                              |
+-------------+-----------------------------------------+----------------------------------------------------------------------------+
|Jenkins      |Jenkins server URL                       | Enter the URL of the server (and port, if applicable).                     |
|             +-----------------------------------------+----------------------------------------------------------------------------+
|             |Project name                             | Enter the name of the project which tracks this repository in Jenkins.     |
+-------------+-----------------------------------------+----------------------------------------------------------------------------+
|TeamCity     |TeamCity server URL                      | Enter the URL of the server (and port, if applicable).                     |
|             +-----------------------------------------+----------------------------------------------------------------------------+
|             |Project name                             | Enter the name of the project which tracks this repository in TeamCity.    |
|             |                                         | Multiple project names can be entered separated by the | character.        |
|             +-----------------------------------------+----------------------------------------------------------------------------+
|             |Build Id Filter                          | Enter a regexp filter for which build results you want to retrieve in the  |
|             |                                         | case that your build project creates multiple builds. For example, if your |
|             |                                         | project includes both devBuild and docBuild you may wish to apply a filter |
|             |                                         | of "devBuild" to retrieve the results from only the program build.         |
+-------------+-----------------------------------------+----------------------------------------------------------------------------+
|Team         |Tfs server (Name or URL)                 | Enter the URL of the server (and port, if applicable).                     |
|Foundation   +-----------------------------------------+----------------------------------------------------------------------------+
|             |Team collection name                     |                                                                            |
|             +-----------------------------------------+----------------------------------------------------------------------------+
|             |Project name                             | Enter the name of the project which tracks this repository in Tfs.         |
|             +-----------------------------------------+----------------------------------------------------------------------------+
|             |Build definition name                    |                                                                            |
|             |(use first found if left empty)          |                                                                            |
+-------------+-----------------------------------------+----------------------------------------------------------------------------+

.. _settings-ssh:

SSH
---

This page allows you to configure the SSH client you want Git to use. Git Extensions is optimized for PuTTY. Git Extensions
will show command line dialogs if you do not use PuTTY and user input is required (unless you have configured SSH to use authentication
with key instead of password). Git Extensions can load SSH keys for PuTTY when needed.

+-------------+-------------------------------------+----------------------------------------------------------------------------+
|Group        | Setting                             | Description                                                                |
+=============+=====================================+============================================================================+
|Specify which|``PuTTY`` radio button               | Use PuTTY as SSH client.                                                   |
|ssh client   +-------------------------------------+----------------------------------------------------------------------------+
|to use       |``OpenSSH`` radio button             | Use OpenSSH as SSH client.                                                 |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |``Other ssh client`` radio button    | Use another SSH client. Enter the path to the SSH client you wish to use.  |
+-------------+-------------------------------------+----------------------------------------------------------------------------+
|Configure    |Path to plink.exe                    | Enter the path to the plink.exe executable.                                |
|PuTTY        |                                     |                                                                            |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Path to puttygen                     | Enter the path to the puttygen.exe executable.                             |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Path to pageant                      | Enter the path to the pageant.exe executable.                              |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Automatically start authentication   | If an SSH key has been configured, then when accessing a remote repository |
|             |                                     | the key will automatically be used by the SSH client if this is checked.   |
+-------------+-------------------------------------+----------------------------------------------------------------------------+


.. _settings-scripts:

Scripts
-------

This page allows you to configure specific commands to run before/after Git actions or to add a new command to the User Menu.
The top half of the page summarises all of the scripts currently defined. If a script is selected from the summary, the bottom
half of the page will allow modifications to the script definition.

A hotkey can also be assigned to execute a specific script. See :ref:`settings-hotkeys`.

+---------------------------------------------------+----------------------------------------------------------------------------+
| Setting                                           | Description                                                                |
+===================================================+============================================================================+
|``Add`` button                                     | Adds a new script. Complete the details in the bottom half of the screen.  |
+---------------------------------------------------+----------------------------------------------------------------------------+
|``Remove`` button                                  | Removes a script.                                                          |
+---------------------------------------------------+----------------------------------------------------------------------------+
|Up/Down Arrows                                     | Changes order of scripts.                                                  |
+---------------------------------------------------+----------------------------------------------------------------------------+
|Name                                               | The name of the script.                                                    |
+---------------------------------------------------+----------------------------------------------------------------------------+
|Enabled                                            | If checked, the script is active and will be performed at the appropriate  |
|                                                   | time (as determined by the On Event setting).                              |
+---------------------------------------------------+----------------------------------------------------------------------------+
|Ask for confirmation                               | If checked, then a popup window is displayed just before the script is run |
|                                                   | to confirm whether or not the script is to be run. Note that this popup    |
|                                                   | is *not* displayed when the script is added as a command to the User Menu  |
|                                                   | (On Event setting is ShowInUserMenuBar).                                   |
+---------------------------------------------------+----------------------------------------------------------------------------+
|Run in background                                  | If checked, the script will run in the background and Git Extensions will  |
|                                                   | return to your control without waiting for the script to finish.           |
+---------------------------------------------------+----------------------------------------------------------------------------+
|Add to revision grid context menu                  | If checked, the script is added to the context menu that is displayed when |
|                                                   | right-clicking on a line in the Commit Log page.                           |
+---------------------------------------------------+----------------------------------------------------------------------------+
|Command                                            | Enter the command to be run. This can be any command that your system can  |
|                                                   | run e.g. an executable program, a .bat script, a Python command, etc.      |
|                                                   | Use the ``Browse`` button to find the command to run.                      |
+---------------------------------------------------+----------------------------------------------------------------------------+
|Arguments                                          | Enter any arguments to be passed to the command that is run.  The          |
|                                                   | ``Help`` button displays items that will be resolved by Git Extensions     |
|                                                   | before executing the command e.g. {cBranch} will resolve to the currently  |
|                                                   | checked out branch, {UserInput} will display a popup where you can enter   |
|                                                   | data to be passed to the command when it is run.                           |
+---------------------------------------------------+----------------------------------------------------------------------------+
|On Event                                           | Select when this command will be executed, either before/after certain Git |
|                                                   | commands, or displayed on the User Menu bar.                               |
+---------------------------------------------------+----------------------------------------------------------------------------+

.. _settings-hotkeys:

Hotkeys
-------

This page allows you to define keyboard shortcuts to actions when specific pages of Git Extensions are displayed.
The HotKeyable Items identifies a page within Git Extensions. Selecting a Hotkeyable Item displays the list of
commands on that page that can have a hotkey associated with them.

The Hotkeyable Items consist of the following pages

1) Commit: the page displayed when a Commit is requested via the ``Commit`` User Menu button or the ``Commands/Commit`` menu option.
2) Browse: the Commit Log page (the page displayed after a repository is selected from the Start Page).
3) RevisionGrid: the list of commits on the Commit Log page.
4) FileViewer: the page displayed when viewing the contents of a file.
5) FormMergeConflicts: the page displayed when merge conflicts are detected that need correcting.
6) Scripts: shows scripts defined in Git Extensions and allows shortcuts to be assigned. Refer :ref:`settings-scripts`.

+---------------------------------------------------+----------------------------------------------------------------------------+
| Setting                                           | Description                                                                |
+===================================================+============================================================================+
|Hotkey                                             | After selecting a Hotkeyable Item and the Command, the current keyboard    |
|                                                   | shortcut associated with the command is displayed here. To alter this      |
|                                                   | shortcut, click in the box where the current hotkey is shown and press the |
|                                                   | new keyboard combination.                                                  |
+---------------------------------------------------+----------------------------------------------------------------------------+
|``Apply`` button                                   | Click to apply the new keyboard combination to the currently selected      |
|                                                   | Command.                                                                   |
+---------------------------------------------------+----------------------------------------------------------------------------+
|``Clear`` button                                   | Sets the keyboard shortcut for the currently selected Command to 'None'.   |
+---------------------------------------------------+----------------------------------------------------------------------------+
|``Reset all Hotkeys to defaults`` button           | Resets all keyboard shortcuts to the defaults (i.e. the values when Git    |
|                                                   | Extensions was first installed).                                           |
+---------------------------------------------------+----------------------------------------------------------------------------+

.. _settings-shell-extension:

Shell Extension
---------------

When installed, Git Extensions adds items to the context menu when a file/folder is right-clicked within Windows Explorer. One of these items
is ``Git Extensions`` from which a further (cascaded) menu can be opened. This settings page determines which items will appear on that cascaded
menu and which will appear in the main context menu. Items that are checked will appear in the cascaded menu.

To the right side of the list of check boxes is a preview that shows you how the Git Extensions menu items will be arranged with
your current choices.

By default, what is displayed in the context menu also depends on what item is right-clicked in Windows Explorer; a file or a folder
(and whether the folder is a Git repository or not). If you want Git Extensions to always include all of its context menu items,
check the box ``Always show all commands``.

.. _settings-advanced:

Advanced
--------
This page allows advanced settings to be modified. Clicking on the '+' symbol on the tree of settings will display further settings.
Refer :ref:`settings-confirmations`.

+-------------+-------------------------------------+----------------------------------------------------------------------------+
|Group        | Setting                             | Description                                                                |
+=============+=====================================+============================================================================+
|Checkout     |Always show checkout dialog          | Always show the Checkout Branch dialog when swapping branches. This dialog |
|             |                                     | is normally only shown when uncommitted changes exist on the current branch|
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Use last chosen "local changes"      | This setting works in conjunction with the 'Git Extensions/Check for       |
|             |action as default action.            | uncommitted changes in checkout branch dialog' setting. If the 'Check for  |
|             |                                     | uncommitted changes' setting is checked, then the Checkout Branch dialog   |
|             |                                     | is shown *only* if this setting is unchecked. If this setting is checked,  |
|             |                                     | then no dialog is shown and the last chosen action is used.                |
+-------------+-------------------------------------+----------------------------------------------------------------------------+
|General      |Don't show help images               | In the Pull, Merge and Rebase dialogs, images are displayed by default to  |
|             |                                     | explain what happens with the branches and their commits and the meaning of|
|             |                                     | LOCAL, BASE and REMOTE (for resolving merge conflicts) in different merge  |
|             |                                     | or rebase scenarios.                                                       |
|             |                                     | If checked, these Help images will not be displayed.                       |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Always show advanced options         | In the Push, Merge and Rebase dialogs, advanced options are hidden by      |
|             |                                     | default and shown only after you click a link or checkbox. If this setting |
|             |                                     | is checked then these options are always shown on those dialogs.           |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Remember the ignore-white-space      | If checked, the diff views will be able to remember the ignore-white-spaces|
|             |preference                           | preference.                                                                |
+-------------+-------------------------------------+----------------------------------------------------------------------------+

.. _settings-confirmations:

Confirmations
-------------
This page allows you to turn off certain confirmation popup windows.

+-------------+-------------------------------------+----------------------------------------------------------------------------+
|Group        | Setting                             | Description                                                                |
+=============+=====================================+============================================================================+
|Don't ask to |Amend last commit                    |If checked, do not display the popup warning about the rewriting of history |
|confirm to   |                                     |when you have elected to amend the last committed change.                   |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Apply stashed changes after          |In the Pull dialog, if ``Auto stash`` is checked, then any changes will be  |
|             |successful pull                      |stashed before the pull is performed. Any stashed changes are then          |
|             |                                     |re-applied after the pull is complete. If this setting is checked, the      |
|             |                                     |stashed changes are applied with no confirmation popup.                     |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Apply stashed changes after          |In the Checkout Branch dialog, if ``Stash`` is checked, then any changes    |
|             |successful checkout                  |will be stashed before the branch is checked out. If this setting is        |
|             |                                     |checked, then the stashed changes will be automatically re-applied after    |
|             |                                     |successful checkout of the branch with no confirmation popup.               |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Add a tracking reference for newly   |When you push a local branch to a remote and it doesn't have a tracking     |
|             |pushed branch                        |reference, you are asked to confirm whether you want to add such a          |
|             |                                     |reference. If this setting is checked, a tracking reference will always be  |
|             |                                     |added if it does not exist.                                                 |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Push a new branch for the remote     |When pushing a new branch that does not exist on the remote repository, a   |
|             |                                     |confirmation popup will normally be displayed. If this setting is checked,  |
|             |                                     |then the new branch will be pushed with no confirmation popup.              |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Update submodules on checkout        |When you check out a branch from a repository that has submodules, you will |
|             |                                     |be asked to update the submodules. If this setting is checked, the          |
|             |                                     |submodules will be updated without asking.                                  |
+-------------+-------------------------------------+----------------------------------------------------------------------------+

.. _settings-plugins:

Plugins
-------

Plugins provide extra functionality for Git Extensions.

+-------------+-------------------------------------+----------------------------------------------------------------------------+
|Plugin       | Setting                             | Description                                                                |
+=============+=====================================+============================================================================+
|Auto compile |**This plugin proposes (confirmation required) that you automatically build submodules after they are updated via |
|SubModules   |the GitExtensions Update submodules command.**                                                                    |
|             |                                                                                                                  |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Enabled (true/false)                 | Enter true to enable the plugin, or false to disable.                      |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Path to msbuild.exe                  | Enter the path to the msbuild.exe executable.                              |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |msbuild.exe arguments                | Enter any arguments to msbuild.                                            |
+-------------+-------------------------------------+----------------------------------------------------------------------------+
|Periodic     |**This plugin keeps your remote tracking branches up-to-date automatically by fetching periodically.**            |
|background   +-------------------------------------+----------------------------------------------------------------------------+
|fetch        |Arguments of git command to run      |Enter the git command and its arguments into the edit box. The default      |
|             |                                     |command is ``fetch --all``, which will fetch all branches from all remotes. |
|             |                                     |You can modify the command if you would prefer, for example, to fetch only  |
|             |                                     |a specific remote, e.g. ``fetch upstream``.                                 |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Fetch every (seconds)                |Enter the number of seconds to wait between each fetch.                     |
|             |                                     |Enter 0 to disable this plugin.                                             |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Refresh view after fetch             |If checked, the commit log and branch labels will be refreshed after the    |
|             |                                     |fetch. If you are browsing the commit log and comparing revisions you may   |
|             |                                     |wish to disable the refresh to avoid unexpected changes to the commit log.  |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Fetch all submodules                 |If checked, also perform "git fetch --all" recursively on all configured    |
|             |                                     |submodules as part of the periodic background fetch.                        |
+-------------+-------------------------------------+----------------------------------------------------------------------------+
|Create local |**This plugin will create local tracking branches for all branches on a remote repository. The remote repository  |
|tracking     |is specified when the plugin is run.**                                                                            |
|branches     |                                                                                                                  |
+-------------+-------------------------------------+----------------------------------------------------------------------------+
|Delete       |**This plugin allows you to delete obsolete branches i.e. those branches that are fully merged to another         |
|obsolete     |branch. It will display a list of obsolete branches for review before deletion.**                                 |
|branches     |                                                                                                                  |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Delete obsolete branches older than  |Select branches created greater than the specified number of days ago.      |
|             |(days)                               |                                                                            |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Branch where all branches should be  |The name of the branch where a branch *must* have been merged into to be    |
|             |merged                               |considered obsolete.                                                        |
+-------------+-------------------------------------+----------------------------------------------------------------------------+
|Find large   |**Finds large files in the repository and allows you to delete them.**                                            |
|files        |                                                                                                                  |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Find large files bigger than (Mb)    |Specify what size is considered a 'large' file.                             |
|             |                                     |                                                                            |
+-------------+-------------------------------------+----------------------------------------------------------------------------+
|Gerrit Code  |**The Gerrit plugin provides integration with Gerrit for GitExtensions. This plugin has been based on the         |
|Review       |git-review tool.**                                                                                                |
|             |                                                                                                                  |
|             |For more information see: https://www.gerritcodereview.com/                                                       |
+-------------+-------------------------------------+----------------------------------------------------------------------------+
|GitFlow      |**The GitFlow plugin provides high-level repository operations for Vincent Driessen's branching model**           |
|             |                                                                                                                  |
|             |For more information see: https://github.com/nvie/gitflow                                                         |
+-------------+-------------------------------------+----------------------------------------------------------------------------+
|Github       |**This plugin will create an OAuth token so that some common GitHub actions can be integrated with Git            |
|             |Extensions.**                                                                                                     |
|             |                                                                                                                  |
|             |For more information see: https://github.com/                                                                     |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |OAuth Token                          |The token generated and retrieved from GitHub.                              |
+-------------+-------------------------------------+----------------------------------------------------------------------------+
|Impact Graph |**This plugin shows in a graphical format the number of commits and counts of changed lines in the repository     |
|             |performed by each person who has committed a change.**                                                            |
+-------------+-------------------------------------+----------------------------------------------------------------------------+
|Statistics   |**This plugin provides various statistics (and a pie chart) about the current Git repository. For example, number |
|             |of commits by author, lines of code per language.**                                                               |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Code files                           |Specifies extensions of files that are considered code files.               |
|             |                                     |                                                                            |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Directories to ignore (EndsWith)     |Ignore these directories when calculating statistics.                       |
|             |                                     |                                                                            |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Ignore submodules (true/false)       |Ignore submodules when calculating statistics.                              |
|             |                                     |                                                                            |
+-------------+-------------------------------------+----------------------------------------------------------------------------+
|gource       |**Gource is a software version control visualization tool.**                                                      |
|             |                                                                                                                  |
|             |For more information see: http://gource.io/                                                                       |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Path to "gource"                     | Enter the path to the gource software.                                     |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Arguments                            |Enter any arguments to gource.                                              |
+-------------+-------------------------------------+----------------------------------------------------------------------------+
|Proxy        |**This plugin can set/unset the value for the http.proxy git config file key as per the settings entered here.**  |
|Switcher     |                                                                                                                  |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Username                             |The user name needed to access the proxy.                                   |
|             |                                     |                                                                            |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Password                             |The password attached to the username.                                      |
|             |                                     |                                                                            |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |HttpProxy                            |Proxy Server URL.                                                           |
|             |                                     |                                                                            |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |HttpProxyPort                        |Proxy Server port number.                                                   |
|             |                                     |                                                                            |
+-------------+-------------------------------------+----------------------------------------------------------------------------+
|Release Notes|**This plugin will generate 'release notes'. This involves summarising all commits between the specified from and |
|Generator    |to commit expressions when the plugin is started. This output can be copied to the clipboard in various formats.**|
+-------------+-------------------------------------+----------------------------------------------------------------------------+
|Create       |**If your repository is hosted on Atlassian Bitbucket Server (Stash) then this plugin will enable you to create   |
|Stash Pull   |a pull request for Stash from Git Extensions**                                                                    |
|Request      |                                                                                                                  |
|             |For more information see: https://www.atlassian.com/software/bitbucket/server                                     |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Stash Username                       |The username required to access Stash.                                      |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Stash Password                       |The password required to access Stash.                                      |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Specify the base URL to Stash        |The URL from which you will access Stash.                                   |
|             +-------------------------------------+----------------------------------------------------------------------------+
|             |Disable SSL verification             |Check this option if you do not require SSL verification to access          |
|             |                                     |Bitbucket Server (Stash).                                                   |
+-------------+-------------------------------------+----------------------------------------------------------------------------+
