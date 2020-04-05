Development Guide
=========================

.. contents::
  :depth: 2

Requirements
----------------------------------

Working on the SEED platform requires a fairly recent computer with one of
the following supported operating systems:

* Apple Mac OS X 10.13.2 'High Sierra' or later
* Ubuntu 18.04 LTS or later
* Windows 10 or later

In terms of hardware, the recommended configuration is at least an 8-core CPU
with 8 GB RAM, and preferrably a fast SSD.

Recommended Editors and Tools
----------------------------------

The repository comes with a
`Sublime Text 3 <https://www.sublimetext.com/>`_ project file, as our preferred
editor is Sublime Text 3. On top of Sublime Text 3 you might find the following
Sublime packages useful:

* `Package Control <https://packagecontrol.io/>`_: The basic package manager
  plugin for Sublime Text 3.
* `Anaconda <http://damnwidget.github.io/anaconda/>`_: A quite good Python
  development environment for Sublime Text 3.
* `Sublime Linter <https://github.com/SublimeLinter/SublimeLinter>`_: A code
  linting framework for Sublime Text 3.
* `Sublime Linter - pylint <https://github.com/SublimeLinter/SublimeLinter-pylint>`_:
  A linter plugin for Sublime Linter that executes pylint.
* `SublimeCodeIntel <https://packagecontrol.io/packages/SublimeCodeIntel>`_: An
interface plugin for CodeIntel.
* `A File Icon <https://github.com/sublimetext/afileicon>`_: Adds file type
  specific icons to Sublime Text 3.
* `Bracket Highlighter <https://github.com/facelessuser/BracketHighlighter>`_:
  Utility package that helps matching opening and closing brackets of various
  types.
* `Git <https://github.com/kemayo/sublime-text-git>`_: Adds Git interaction
  to Sublime Text 3.
* `GitGutter <https://github.com/jisaacks/GitGutter>`_: Adds Git diff support
  to Sublime Text 3.
* `Log Highlight <https://packagecontrol.io/packages/Log%20Highlight>`_: Adds
  the option to specify syntax highlighting for log files.
* `Trailing Spaces <https://github.com/SublimeText/TrailingSpaces>`_:
  Highlights and automatically removes unnecessary whitespaces from the end of
  source code lines.
* `INI <https://packagecontrol.io/packages/INI>`_: Provides syntax
  highlighting for INI files.
* `Markdown Extended <https://github.com/jonschlinkert/sublime-markdown-extended>`_:
  Provides additional syntax highlighting for markdown files.
* `Protobuf Syntax Highlighting <https://packagecontrol.io/packages/Protobuf%20Syntax%20Hightlighting>`_:
  Provides syntax highlighting for Google Protocol Buffer files.
* `SideBar Enchancements <https://github.com/SideBarEnhancements-org/SideBarEnhancements>`_:
  Provides various sidebar enhancements to the default Sublime Text 3 sidebar.
* `TTCNComplete <https://packagecontrol.io/packages/TtcnComplete>`_: Provides
  syntax highlighting and code completion for TTCN.
* `AutoDocstring <https://packagecontrol.io/packages/AutoDocstring>`_: Provides
  support to automatically generate Python docstring skeletons.
* `Dockerfile Syntax Highlight <https://packagecontrol.io/packages/Dockerfile%20Syntax%20Highlight>`_: Provides
  syntax highlighting for Dockerfile.
* `Color Highlighter <https://packagecontrol.io/packages/Color%20Highlighter>`_: Underlays
  selected hexadecimal colorcodes.
* `Terminus <https://github.com/randy3k/Terminus>`_: Allows opening terminals
  inside Sublime 3.

Directory Structure
----------------------------------

The top level directory structure of the repository is the following:

* **.env**: The directory containing the virtual Python environment created by
  virtualenv. Only present when working in a virtual environment.
* **.git**: The directory containing Git internals. Do not touch, unless you
  absolutely know what you are doing.
* **assets**: Contains all binary assets, typically images and other media
+ * **doc**: Contains the documentation of the platform.
* **scripts**: Contains various utility scripts mainly utilized by CI.
* **src**: Contains the source code of the various componets of the platform.
* **templates**: Contains template files used by the various components.

Each subdirectory contains additional README.md files with a description of
the content of that subdirectory.

Installation
----------------------------------

Coding Style
----------------------------------

The following documents outline the coding styles used by the various
components of the platform.

.. toctree::
  :maxdepth: 1

  python_style_guide


Development Workflow
----------------------------------
