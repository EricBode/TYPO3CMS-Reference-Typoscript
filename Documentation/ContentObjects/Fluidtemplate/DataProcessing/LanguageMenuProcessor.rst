.. include:: /Includes.rst.txt
.. _LanguageMenuProcessor:

=====================
LanguageMenuProcessor
=====================

This menu processor generates a json encoded menu string that will be
decoded again and assigned to the :typoscript:`FLUIDTEMPLATE` as a variable.

.. hint:: The third party extension
   `b13/menus <https://extensions.typo3.org/extension/menus>`__ also provides
   a language menu processors: :php:`B13\Menus\DataProcessing\LanguageMenu`.

   Refer to the
   `manual of the extension b13/menus <https://github.com/b13/menus/blob/master/README.md>`__
   for more information.


Options:
========

.. confval:: if

   :Required: false
   :type: :ref:`if` condition
   :default: ""

   If the condition is not met the data is not processed

.. confval:: languages

   :Required: true
   :type: string, :ref:`stdWrap`
   :default: "auto"
   :Example: "0,1,2"

   A list of comma separated language IDs (e.g. 0,1,2) to use
   for the menu creation or `auto` to load from site configuration


.. confval:: addQueryString.exclude

   :Required: true
   :type: string, :ref:`stdWrap`
   :default: ""
   :Example: "gclid,contrast"

   A list of comma separated parameter names to be excluded from
   the language menu urls.

.. confval:: as

   :Required: false
   :type: string
   :default: defaults to the fieldName

   The variable's name to be used in the Fluid template


Example: Menu of all language from site configuration
=====================================================

Please see also :ref:`dataProcessing-about-examples`.


TypoScript
----------

Using the :php:`LanguageMenuProcessor` the following scenario is possible:

.. include:: /CodeSnippets/DataProcessing/TypoScript/LanguageMenuProcessor.rst.txt


The Fluid template
------------------

This generated menu can be used in Fluid like this:


.. include:: /CodeSnippets/DataProcessing/Template/DataProcLangMenu.rst.txt

Output
------

The array now contains information on all languages as defined in the site
configuration. As the current page is not translated into German, the
German language has the :php:`item.available` set to false. It therefore
doesn't get linked in the template.

.. include:: /Images/AutomaticScreenshots/DataProcessing/LanguageMenuProcessor.rst.txt
