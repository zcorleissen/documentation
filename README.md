ObjectRocket Documentation
=====================
This Github repository represents ObjectRocket's documentation site, located at http://docs.objectrocket.com. The site is based on the [Sphinx](http://sphinx-doc.org/) documentation generator for Python.


To suggest changes to the documentation, please submit an [Issue](https://github.com/objectrocket/documentation/issues/new) or [Pull Request](https://github.com/objectrocket/documentation/compare/).

reStructuredText
----------------
The documentation pages are built using the [reStructuredText](http://docutils.sourceforge.net/rst.html) standard.
Github supports RST, so modification via Github's editor is recommended.

Building the Docs
-----------------
Activate your favorite [virtualenv](http://virtualenv.readthedocs.org/en/latest/) or [pyenv](https://github.com/yyuu/pyenv), and do the following from your terminal:

    pip install -r requirements.txt
    cd source
    make clean html

Your newly built HTML will live under ``source/_build/html/``. Open ``source/_build/html/index.html`` to see the root page.

Run ``make clean html`` or just ``make html`` from the ``source`` directory whenever you need a new build of the docs.

Support and Feedback
--------------------
If you find an issue, please submit the issue in Github directly.
[Documentation Issues](https://github.com/objectrocket/documentation/issues)

And as a small thank you if we merge your pull request, we’ll send you a really nice ObjectRocket t-shirt.  Just email your github handle, size and postal address to [support@objectrocket.com](mailto:support@objectrocket.com).

As always, if you need additional assistance, drop us a note at
[support@objectrocket.com](mailto:support@objectrocket.com).
