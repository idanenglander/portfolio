====================
Anaconda Code |beta|
====================

Anaconda Code empowers you to write Python code and run it locally, directly within Excel. This gives you flexibility and control over the Python environment in your workbook, allowing you to add and remove packages as needed, all while keeping code and data securely within your workbook.

Initializing Anaconda Code
==========================

.. note::

    Anaconda Code is included in the :doc:`Anaconda Toolbox installation <install>`.

Anaconda Code is powered by `PyScript <https://pyscript.net/>`_, our open-source platform for running Python in the browser. When you first launch Anaconda Code, set up and run your PyScript Python environment using the following steps:

#. Click **Enable PyScript**. 
#. Once PyScript is enabled, sign in to Anaconda Cloud.

Understanding Anaconda Code
===========================

Let’s take a look at the different elements within Anaconda Code using the **Dashboard** tab for reference:

.. thumbnail:: /img/toolbox/code_anatomy.png
    :align: center

#. **Dashboard**
    :ref:`Create and run Python code <run-py-code>` and view script logs
#. **Environment**
    :ref:`Manage the packages and Pyodide version <manage-code-env>` for your coding environment
#. **Imports and Definitions**
    :ref:`Customize the code <initialize>` that affects all code in your workbook
#. **Settings**
    Modify the :ref:`default settings for running code <workbook-settings>`
#. **Code**
    View and :ref:`edit the code <edit-code>` throughout your workbook
#. **Logs**
    View errors and print statements
#. **More**
    Quickly confirm your code's :ref:`cell linking <cell-link>` states
#. **New code**
    Create new code to run in your workbook

.. _run-py-code:

Running Python code
===================

Begin writing Python code in a cell using the following steps:

#. From the Dashboard, click |plus| **New**, then select a cell where you want to insert your code.
#. Enter your Python code in the code editor. If you want to reference a range of data from your spreadsheet in your code, click |link| **Link Range** and select the desired data range.

    .. dropdown:: Using the ``REF`` function
        :animate: fade-in
        :color: primary 

        The ``REF`` function returns a list of lists and can be used in the following ways:

        .. csv-table::
            :file: ref-function.csv
            :widths: 35, 30, 35
            :header-rows: 1

        You can change the behavior of ``to_df()`` and ``to_array()`` from the :ref:`Imports and Definitions <initialize>` tab.

#. Set the :ref:`cell linking and output options <workbook-settings>`.

    .. note::

        Toggle between **isolated** and **linked** modes by clicking the plug |plug| button.

#. Click **Save and Run**.

Your code runs in the designated cell.

.. _edit-code:

Editing Python code
===================

Do not edit your code in the cell itself; instead, modify and re-run your code directly in Anaconda Code. 

.. note::

    An Anaconda.cloud account is required for users to edit shared code.

#. From the Dashboard, click the expand |expand| button to open the edit view.
#. Adjust your code, then click **Run**. 

.. _manage-code-env:

Managing the environment
========================

Anaconda Code hosts a single, self-contained environment, which manages the back-end software packages that enable you to run Python code within your Excel workbook. You can manage software packages within this environment to extend Python's processing, visualization, and analytical capabilities, and even select the version of `Pyodide <https://pyodide.org/en/stable/>`_ (the WASM engine used by PyScript) that you want to run Python.

.. note::

    You can make changes to your environment at any time; however, like with all software projects, altering the environment changes the way the underlying code is interpreted and can cause unintended complications.

Choosing a Pyodide version
--------------------------

The latest version of Pyodide is used by default for all new spreadsheets. For existing spreadsheets, the versions of Pyodide and packages necessary for your code are pinned to the environment.

You can switch versions of Pyodide using the following steps:

#. From the **Environment** tab, click **Edit**.
#. To switch versions of Pyodide, click the |arrow| dropdown beside your current Pyodide version.

Managing software packages
--------------------------

To add new packages, click |plus| **Add**. Alternatively, click the arrow to add from either PyPI or a direct download link to a Python wheel (``.whl``). 

.. thumbnail:: /img/toolbox/code_add_package.png
    :align: center

.. note::
    
    Packages that contain compiled code might not be compatible with PyScript's WASM engine. For more information, visit `PyScript.net <https://pyscript.net/>`_.

To remove a package, click |trash| **Delete** beside the package you want to remove.

.. _initialize:

Customizing code initialization
===============================

You can think of Anaconda Code’s **Imports and Definitions** as an initialization file for your code or like the first cell in a Jupyter Notebook. All code in this section is available to all cells, whether they are :ref:`run isolated or linked <cell-link>`.

To customize your code's Imports and Definitions:

#. From the **Imports and Definitions** tab, establish the connections to the packages you need to run your code.

    .. note::
        
        You can only ``import`` from the packages included in the standard Python installation and those listed in the **Environment** tab.

#. Click **Run**.

.. _workbook-settings:

Modifying workbook settings
===========================

While you can adjust the settings for running code in your workbook on a case-by-case basis when creating and editing code, you can also assign default settings from the **Settings** tab.

.. _cell-link:

Cell linking
------------

.. csv-table::
    :file: isolated-linked.csv
    :widths: 20, 80
    :header-rows: 1

Cell output
-----------

.. csv-table::
    :file: cell-output.csv
    :widths: 20, 80
    :header-rows: 1

Troubleshooting
===============

If you encounter an issue that is not listed here, you can obtain support for Anaconda through the `Anaconda community <https://community.anaconda.cloud/>`_ or by `opening a support ticket <https://support.anaconda.com/hc/en-us/requests/new?ticket_form_id=360000993773>`_.

Error installing functions
--------------------------

.. dropdown:: Cause
    :animate: fade-in
    :color: primary

        This error can occur when Excel loads the Anaconda Toolbox add-in and registers its custom functions. This error happens within Excel and cannot be resolved by the Anaconda Toolbox.

.. dropdown:: Solution
    :animate: fade-in
    :color: primary

        Close and reopen Excel. If the issue persists, uninstall the Anaconda Toolbox add-in, then reinstall.

.. |arrow| raw:: html

      <svg class="inline" width="1em" height="1em" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg">
      <path 
        d="M15.8 7.73c.28.3.27.78-.03 1.06l-5.25 5a.75.75 0 0 1-1.04 0l-5.25-5a.75.75 0 0 1 1.04-1.08L10 12.2l4.73-4.5a.75.75 0 0 1 1.06.02Z"
      />
    </svg>

.. |plus| raw:: html

    <i class="fa-light fa-plus"></i>

.. |beta| raw:: html

    <svg class="inline" width="31" height="14" viewBox="0 0 31 14" fill="none" xmlns="http://www.w3.org/2000/svg">
    <rect width="31" height="14" rx="3" fill="#6D5BF6"/>
    <path d="M6.88281 7.58203H5.41797L5.41016 6.68359H6.59766C6.8112 6.68359 6.98177 6.66016 7.10938 6.61328C7.23698 6.5638 7.32943 6.49219 7.38672 6.39844C7.44661 6.30469 7.47656 6.1875 7.47656 6.04688C7.47656 5.88542 7.44661 5.75521 7.38672 5.65625C7.32682 5.55729 7.23177 5.48568 7.10156 5.44141C6.97396 5.39453 6.80859 5.37109 6.60547 5.37109H5.93359V10H4.5625V4.3125H6.60547C6.95703 4.3125 7.27083 4.34505 7.54688 4.41016C7.82292 4.47266 8.05729 4.56901 8.25 4.69922C8.44531 4.82943 8.59375 4.99349 8.69531 5.19141C8.79688 5.38672 8.84766 5.61719 8.84766 5.88281C8.84766 6.11458 8.79818 6.33203 8.69922 6.53516C8.60026 6.73828 8.4349 6.90365 8.20312 7.03125C7.97396 7.15625 7.66016 7.22135 7.26172 7.22656L6.88281 7.58203ZM6.82812 10H5.08594L5.55469 8.94531H6.82812C7.01562 8.94531 7.16536 8.91667 7.27734 8.85938C7.39193 8.79948 7.47396 8.72135 7.52344 8.625C7.57552 8.52604 7.60156 8.41667 7.60156 8.29688C7.60156 8.15104 7.57682 8.02474 7.52734 7.91797C7.48047 7.8112 7.40495 7.72917 7.30078 7.67188C7.19661 7.61198 7.05729 7.58203 6.88281 7.58203H5.73047L5.73828 6.68359H7.11719L7.4375 7.04297C7.81771 7.02734 8.11849 7.08073 8.33984 7.20312C8.5638 7.32552 8.72396 7.48698 8.82031 7.6875C8.91667 7.88802 8.96484 8.09766 8.96484 8.31641C8.96484 8.6888 8.88411 9 8.72266 9.25C8.5638 9.5 8.32552 9.6875 8.00781 9.8125C7.6901 9.9375 7.29688 10 6.82812 10ZM14.6406 8.94531V10H11.6094V8.94531H14.6406ZM12.0977 4.3125V10H10.7266V4.3125H12.0977ZM14.25 6.57031V7.58984H11.6094V6.57031H14.25ZM14.6523 4.3125V5.37109H11.6094V4.3125H14.6523ZM19.0352 4.3125V10H17.6641V4.3125H19.0352ZM20.7461 4.3125V5.37109H15.9922V4.3125H20.7461ZM24.2617 5.50781L22.875 10H21.4023L23.4922 4.3125H24.4258L24.2617 5.50781ZM25.4102 10L24.0195 5.50781L23.8398 4.3125H24.7852L26.8867 10H25.4102ZM25.3555 7.87891V8.9375H22.4375V7.87891H25.3555Z" fill="white"/>

    </svg>

.. |expand| raw:: html

      <svg class="inline" width="1em" height="1em" viewBox="0 0 16 16" xmlns="http://www.w3.org/2000/svg">
      <path 
        d="M4 3.5a.5.5 0 0 0-.5.5v1.61a.75.75 0 0 1-1.5 0V4c0-1.1.9-2 2-2h1.61a.75.75 0 0 1 0 1.5H4Zm5.64-.75c0-.41.33-.75.75-.75H12a2 2 0 0 1 2 2v1.61a.75.75 0 0 1-1.5 0V4a.5.5 0 0 0-.5-.5h-1.61a.75.75 0 0 1-.75-.75ZM2.75 9.64c.41 0 .75.33.75.75V12c0 .28.22.5.5.5h1.61a.75.75 0 0 1 0 1.5H4a2 2 0 0 1-2-2v-1.61c0-.42.34-.75.75-.75Zm10.5 0c.41 0 .75.33.75.75V12a2 2 0 0 1-2 2h-1.61a.75.75 0 1 1 0-1.5H12a.5.5 0 0 0 .5-.5v-1.61c0-.42.34-.75.75-.75Z"
      />
    </svg>

.. |link| raw:: html

      <svg class="inline" width="1em" height="1em" viewBox="0 0 16 16" xmlns="http://www.w3.org/2000/svg">
      <path 
        d="M12 6.5A3.5 3.5 0 0 0 8.5 3H4.3A3.5 3.5 0 0 0 3 9.67a4.57 4.57 0 0 1 .1-1.1A2.5 2.5 0 0 1 4.5 4h4.16a2.5 2.5 0 0 1-.16 5h-1l-.1.01a.5.5 0 0 0 .1 1l1-.01h.2A3.5 3.5 0 0 0 12 6.5Zm2 3a2.5 2.5 0 0 0-1.1-2.07 4.52 4.52 0 0 0 .1-1.1A3.5 3.5 0 0 1 11.7 13l-.2.01h-4a3.5 3.5 0 0 1-.2-7h1.2a.5.5 0 0 1 .09 1H7.5a2.5 2.5 0 0 0-.16 5h4.16A2.5 2.5 0 0 0 14 9.5Z"
      />
    </svg>

.. |plug| raw:: html

      <svg class="inline" width="1em" height="1em" viewBox="0 0 16 16" xmlns="http://www.w3.org/2000/svg">
      <path 
        d="M15.35.65a.5.5 0 0 0-.7 0l-2.07 2.07a3.61 3.61 0 0 0-4.64.42l-.13.14a1.25 1.25 0 0 0 0 1.76l3.18 3.19a1.24 1.24 0 0 0 1.77 0l.22-.22a3.47 3.47 0 0 0 .31-4.6l2.06-2.06a.5.5 0 0 0 0-.7Zm-7.2 8.5-.88.88-1.3-1.3.88-.88a.5.5 0 0 0-.7-.7l-.88.88L5 7.77a1.25 1.25 0 0 0-1.76 0L3.03 8a3.47 3.47 0 0 0-.32 4.6L.65 14.63a.5.5 0 0 0 .7.71l2.08-2.07c.6.44 1.3.65 2.03.65.94 0 1.89-.36 2.6-1.08l.14-.13c.48-.48.48-1.28 0-1.77l-.23-.22.88-.88a.5.5 0 0 0-.7-.7Z"
      />
    </svg>

.. |trash| raw:: html

      <svg class="inline" width="1em" height="1em" viewBox="0 0 16 16" xmlns="http://www.w3.org/2000/svg">
      <path 
        d="M7 3h2a1 1 0 0 0-2 0ZM6 3a2 2 0 1 1 4 0h4a.5.5 0 0 1 0 1h-.56l-1.2 8.84A2.5 2.5 0 0 1 9.74 15h-3.5a2.5 2.5 0 0 1-2.48-2.16L2.57 4H2a.5.5 0 0 1 0-1h4Zm1 3.5a.5.5 0 0 0-1 0v5a.5.5 0 0 0 1 0v-5ZM9.5 6c.28 0 .5.22.5.5v5a.5.5 0 0 1-1 0v-5c0-.28.22-.5.5-.5Zm-4.74 6.7c.1.75.74 1.3 1.49 1.3h3.5a1.5 1.5 0 0 0 1.5-1.3L12.42 4H3.57l1.19 8.7Z"
      />
    </svg>
