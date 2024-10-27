============
Environments
============

Environments in conda are self-contained, isolated spaces where you can install specific versions of software packages, including dependencies, libraries, and Python versions. This isolation helps avoid conflicts between package versions and ensures that your projects have the exact libraries and tools they need.

Why should I create a new environment?
======================================

There are several reasons you might want to create a new environment:

|farm| **Isolation of dependencies** - Environments isolate software and their dependencies from the rest of the software installed on your machine. This means you can have both Python 3.9 and Python 3.10 installed on your machine and use both versions without encountering issues.

|object-ungroup| **Reproducibility** - By creating an environment for each project, you can ensure that your code runs consistently across different machines. :ref:`Sharing the environment configuration <share-environment>` allows others to replicate your setup, ensuring that they have the same package versions and dependencies.

|clipboard-list-check| **Ease of management** - Conda provides tools to easily `create, manage, and delete environments <https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html>`_. You can quickly :ref:`switch between environments <switch-environments>`, making it simple to manage multiple projects with different requirements.

|microscope| **Testing and development** - Environments are perfect for testing new packages or libraries without affecting your stable development setups. You can experiment freely and remove the environment if things don't work out, without impacting your other projects.

Why shouldn't I work in the base environment?
=============================================

When first installing and using conda, you probably saw references to something called ``base`` or a “base environment". This environment is where conda itself is installed, and should only be used for installing anaconda, conda, and conda-related packages, such as ``anaconda-client`` or ``conda-build``.

For your projects, however, Anaconda *strongly* recommends creating new environments to work in. This protects your base environment from breaking due to complex dependency conflicts and allows you to easily manage and reproduce your environment on other machines.

Working with environments
=========================

For convenience, the most common actions users take when managing environments are detailed here. For a full list of actions and more comprehensive guide, see `Manage environments <https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html>`_ in the official conda documentation. Alternatively, follow along with our `Getting started with conda environments <https://anaconda.cloud/getting-started-with-conda-environments>`_ tutorial on Anaconda Cloud.

.. tip::

    If you prefer to create and manage your environments via our graphical interface, Navigator, see :doc:`Managing environments <../navigator/tutorials/manage-environments>`.

Creating an environment
-----------------------

Create a conda environment by opening Anaconda Prompt (Terminal on macOS/Linux) and running one of the following commands: 

.. tab-set::

    .. tab-item:: Empty environment

        .. code-block:: none

            # Replace <ENV_NAME> with a name for your environment
            conda create -n <ENV_NAME>

    .. tab-item:: Environment with Python and packages

        .. code-block:: none

            # Replace <ENV_NAME> with a name for your environment
            # Replace <PACKAGE> with your desired package
            # Replace <VERSION> with your desired version of Python
            conda create -n <ENV_NAME> python=<VERSION> <PACKAGE>=<VERSION>

        .. note::
    
            * This downloads the listed packages and their dependencies.
            * If you do not specify a version of Python or other packages, conda will attempt to install the latest version from its available channels.

        **Example:**

        .. code-block::

            conda create -n myenv python=3.11 beautifulsoup4 docutils jinja2=3.1.4 wheel

.. tip::

    It's best practice to install all the packages you want in your environment at the same time, for a few reasons:

    * It will be faster, because each solve takes time.
    * Any incompatibilities between the packages you want are discovered quickly.
    * If incompatibilities are found, then you haven't left your environment in a half-built state.

Activating an environment
-------------------------

Because environments are isolated spaces, you can only work with one at a time. Selecting an environment to work with is called activating it.

Activate an environment by running the following command:

    .. code-block::

        # Replace <ENV_NAME> with the name of the environment you want to activate
        conda activate <ENV_NAME>

.. _switch-environments:

Switching between environments
------------------------------

When you're ready to switch between projects, simply activate the environment of your other project. Activating a different environment will deactivate your current one.

#. (Optional) View a list of all your environments by running the following command:

    .. code-block:: none

        conda info --envs

#. To switch to a different environment, activate it by running the following command:

    .. code-block:: none
        
        # Replace <ENV_NAME> with the name of the environment you want to switch to
        conda activate <ENV_NAME>
   
Deactivating an environment
---------------------------

It is best practice to deactivate your environment when you are finished working in it. 

To deactivate your active environment, run the following command:
   
    .. code-block:: none
        
        conda deactivate

.. _share-environment:

Sharing an environment
----------------------

Sharing your environment with someone else allows them to use conda to recreate your environment on their machine. 

To share an environment and its software packages, you must export your environment's configurations into a ``.yml`` file. 

.. caution:: 

    Simply copying your Anaconda or Miniconda files over to a new directory or another machine will not recreate the environment. You must export the environment as a whole.

Exporting the environment configuration ``.yml`` file
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. warning::

    If you already have an environment configuration ``.yml`` file in your current directory, it will be overwritten during the export process.

#. Activate the environment you want to export by running the following command:

   .. code-block:: none

      # Replace <ENV_NAME> with the name of the environment you want exported
      conda activate <ENV_NAME>

#. Export the environment by running the following command:

    .. code-block:: none

        conda env export > environment.yml

    .. note::

        This file handles both the environment's pip packages and conda packages.

#. Share the exported environment configuration ``.yml`` file with another user.

Creating an environment from an environment.yml file
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If someone has shared an environment with you—or you need to recreate your environment on a new machine—follow these steps to create a new environment using the environment configuration ``.yml`` file:

#. Run the following command from the directory where you stored the ``environment.yml`` file:

   .. code-block:: none
    
        conda env create -f environment.yml

   The first line of the file sets the new environment's name. For more details, see `Creating an environment file manually <https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#create-env-file-manually>`_.

#. Once your environment is successfully created, conda provides you with commands to activate it. Once activated, you can begin working in your new environment.

.. |farm| raw:: html

    <svg class="inline" height="1em" width="1em" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 576 512"><path d="M0 104V456c0 30.9 25.1 56 56 56h72c4.4 0 8-3.6 8-8s-3.6-8-8-8H56c-22.1 0-40-17.9-40-40V192H144c4.4 0 8-3.6 8-8s-3.6-8-8-8H16V104c0-48.6 39.4-88 88-88s88 39.4 88 88v8c0 4.4 3.6 8 8 8s8-3.6 8-8v-8C208 46.6 161.4 0 104 0S0 46.6 0 104zM365.1 81.7c1.9-.7 3.9-.7 5.8 0l132 51.3c2 .8 3.6 2.3 4.4 4.2l52 118.8c.4 1 .7 2.1 .7 3.2V472c0 13.3-10.7 24-24 24H448V424c0-22.1-17.9-40-40-40H328c-22.1 0-40 17.9-40 40v72H200c-13.3 0-24-10.7-24-24V259.3c0-1.1 .2-2.2 .7-3.2l52-118.8c.9-1.9 2.4-3.5 4.4-4.2l132-51.3zM304 496V424c0-13.3 10.7-24 24-24h80c13.3 0 24 10.7 24 24v72H304zM376.7 66.8c-5.6-2.2-11.8-2.2-17.4 0l-132 51.3c-5.9 2.3-10.7 6.9-13.3 12.7L162 249.7c-1.3 3-2 6.3-2 9.6V472c0 22.1 17.9 40 40 40H536c22.1 0 40-17.9 40-40V259.3c0-3.3-.7-6.6-2-9.6L522 130.9c-2.6-5.8-7.3-10.4-13.3-12.7l-132-51.3zM400 208c8.8 0 16 7.2 16 16v64c0 8.8-7.2 16-16 16H336c-8.8 0-16-7.2-16-16V224c0-8.8 7.2-16 16-16h64zm-64-16c-17.7 0-32 14.3-32 32v64c0 17.7 14.3 32 32 32h64c17.7 0 32-14.3 32-32V224c0-17.7-14.3-32-32-32H336z"/></svg>

.. |object-ungroup| raw:: html
    
    <svg class="inline" height="1em" width="1em" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 512"><path d="M0 48C0 71.8 17.3 91.5 40 95.3V256.7C17.3 260.5 0 280.2 0 304c0 26.5 21.5 48 48 48c23.8 0 43.5-17.3 47.3-40H352.7c3.8 22.7 23.6 40 47.3 40c26.5 0 48-21.5 48-48c0-23.8-17.3-43.5-40-47.3V95.3c22.7-3.8 40-23.6 40-47.3c0-26.5-21.5-48-48-48c-23.8 0-43.5 17.3-47.3 40H95.3C91.5 17.3 71.8 0 48 0C21.5 0 0 21.5 0 48zm352.7 8C356 76.1 371.9 92 392 95.3V256.7c-20.1 3.4-36 19.2-39.3 39.3H95.3C92 275.9 76.1 260 56 256.7V95.3C76.1 92 92 76.1 95.3 56H352.7zM480 200h-8v16h8 64.7c3.4 20.1 19.2 36 39.3 39.3V416.7c-20.1 3.4-36 19.2-39.3 39.3H287.3c-3.4-20.1-19.2-36-39.3-39.3V352v-8H232v8 64.7c-22.7 3.8-40 23.6-40 47.3c0 26.5 21.5 48 48 48c23.8 0 43.5-17.3 47.3-40H544.7c3.8 22.7 23.6 40 47.3 40c26.5 0 48-21.5 48-48c0-23.8-17.3-43.5-40-47.3V255.3c22.7-3.8 40-23.6 40-47.3c0-26.5-21.5-48-48-48c-23.8 0-43.5 17.3-47.3 40H480zm112 40a32 32 0 1 1 0-64 32 32 0 1 1 0 64zM560 464a32 32 0 1 1 64 0 32 32 0 1 1 -64 0zM240 496a32 32 0 1 1 0-64 32 32 0 1 1 0 64zM368 304a32 32 0 1 1 64 0 32 32 0 1 1 -64 0zM48 336a32 32 0 1 1 0-64 32 32 0 1 1 0 64zM368 48a32 32 0 1 1 64 0 32 32 0 1 1 -64 0zM48 80a32 32 0 1 1 0-64 32 32 0 1 1 0 64z"/></svg>


.. |clipboard-list-check| raw:: html
    
    <svg class="inline" height="1em" width="1em" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 384 512"><path d="M192 0c-37.1 0-67.6 28-71.6 64H112C91.1 64 73.3 77.4 66.7 96H64C28.7 96 0 124.7 0 160V448c0 35.3 28.7 64 64 64H320c35.3 0 64-28.7 64-64V160c0-35.3-28.7-64-64-64h-2.7c-6.6-18.6-24.4-32-45.3-32h-8.4c-4-36-34.5-64-71.6-64zM16 160c0-26.5 21.5-48 48-48v16c0 17.7 14.3 32 32 32H288c17.7 0 32-14.3 32-32V112c26.5 0 48 21.5 48 48V448c0 26.5-21.5 48-48 48H64c-26.5 0-48-21.5-48-48V160zM136 72c0-30.9 25.1-56 56-56s56 25.1 56 56c0 4.4 3.6 8 8 8h16c17.7 0 32 14.3 32 32v16c0 8.8-7.2 16-16 16H96c-8.8 0-16-7.2-16-16V112c0-17.7 14.3-32 32-32h16c4.4 0 8-3.6 8-8zm56 24a16 16 0 1 0 0-32 16 16 0 1 0 0 32zM157.7 237.7c3.1-3.1 3.1-8.2 0-11.3s-8.2-3.1-11.3 0L96 276.7 77.7 258.3c-3.1-3.1-8.2-3.1-11.3 0s-3.1 8.2 0 11.3l24 24c3.1 3.1 8.2 3.1 11.3 0l56-56zM192 264c0 4.4 3.6 8 8 8H312c4.4 0 8-3.6 8-8s-3.6-8-8-8H200c-4.4 0-8 3.6-8 8zM160 384c0 4.4 3.6 8 8 8H312c4.4 0 8-3.6 8-8s-3.6-8-8-8H168c-4.4 0-8 3.6-8 8zM96 400a16 16 0 1 0 0-32 16 16 0 1 0 0 32z"/></svg>

.. |microscope| raw:: html

    <svg class="inline" height="1em" width="1em" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><path d="M176 24V40c0 4.4-3.6 8-8 8h-8c-8.8 0-16 7.2-16 16V288c0 8.8 7.2 16 16 16h96c8.8 0 16-7.2 16-16V144 128 64c0-8.8-7.2-16-16-16h-8c-4.4 0-8-3.6-8-8V24c0-4.4-3.6-8-8-8H184c-4.4 0-8 3.6-8 8zM288 144V288c0 17.7-14.3 32-32 32H160c-17.7 0-32-14.3-32-32V64c0-17.7 14.3-32 32-32V24c0-13.3 10.7-24 24-24h48c13.3 0 24 10.7 24 24v8c17.7 0 32 14.3 32 32v64c106 0 192 86 192 192c0 78.7-47.4 146.4-115.1 176H504c4.4 0 8 3.6 8 8s-3.6 8-8 8H288 208 8c-4.4 0-8-3.6-8-8s3.6-8 8-8H208h80c97.2 0 176-78.8 176-176s-78.8-176-176-176zM160 360c0-4.4 3.6-8 8-8h80c4.4 0 8 3.6 8 8s-3.6 8-8 8H168c-4.4 0-8-3.6-8-8zM96 424c0-4.4 3.6-8 8-8H312c4.4 0 8 3.6 8 8s-3.6 8-8 8H104c-4.4 0-8-3.6-8-8z"/></svg>