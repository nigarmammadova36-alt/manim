Installatifrom manim import *

class PifagorIsbati(Scene):
    def construct(self):

        # Tərəflər
        a = 2.4
        b = 3.2
        c = 4.0

        # Üçbucaq
        A = LEFT * 3 + DOWN * 2
        B = LEFT * 3 + UP * 2
        C = RIGHT * 2 + DOWN * 2

        triangle = Polygon(
            A, B, C,
            color=WHITE,
            stroke_width=3
        )

        # Tərəf yazıları
        label_a = MathTex("a").next_to(A, DOWN)
        label_b = MathTex("b").next_to(B, LEFT)
        label_c = MathTex("c").next_to(triangle, UP)

        # Başlanğıc
        self.play(Create(triangle))
        self.play(
            Write(label_a),
            Write(label_b),
            Write(label_c)
        )
        self.wait(1)

        # a²
        square_a = Square(
            side_length=2,
            color=WHITE
        ).move_to(RIGHT * 1.5 + DOWN * 2)

        a2 = MathTex("a^2").move_to(square_a)

        # b²
        square_b = Square(
            side_length=2,
            color=WHITE
        ).move_to(LEFT * 1.5 + UP * 1.8)

        b2 = MathTex("b^2").move_to(square_b)

        self.play(
            Create(square_a),
            Write(a2)
        )
        self.play(
            Create(square_b),
            Write(b2)
        )

        self.wait(1)

        # c²
        square_c = Square(
            side_length=3.5,
            color=WHITE
        ).move_to(RIGHT * 1 + UP * 0.5)

        c2 = MathTex("c^2").move_to(square_c)

        self.play(Create(square_c))
        self.play(Write(c2))

        self.wait(1)

        # Son düstur
        formula = MathTex(
            "a^2+b^2=c^2",
            font_size=60
        ).to_edge(DOWN)

        self.play(
            Write(formula),
            run_time=2
        )

        self.wait(3)on
============

Depending on your use case, different installation options are recommended:
if you just want to play around with Manim for a bit, interactive in-browser
notebooks are a really simple way of exploring the library as they
require no local installation. Head over to
https://try.manim.community to give our interactive tutorial a try.

Otherwise, if you intend to use Manim to work on an animation project,
we recommend installing the library locally (preferably to some isolated
virtual Python environment, or a conda-like environment, or via Docker).

.. warning::

   Note that there are several different versions of Manim. The
   instructions on this website are **only** for the *community edition*.
   Find out more about the :ref:`differences between Manim
   versions <different-versions>` if you are unsure which
   version you should install.

#. :ref:`(Recommended) Installing Manim via Python's package manager pip
   <local-installation>`
#. :ref:`Installing Manim to a conda environment <conda-installation>`
#. :ref:`Using Manim via Docker <docker-installation>`
#. :ref:`Interactive Jupyter notebooks via Binder / Google Colab
   <interactive-online>`


.. _local-installation:

Installing Manim locally via pip
********************************

The recommended way of installing Manim is by using Python's package manager
pip. If you already have a Python environment set up, you can simply run
``pip install manim`` to install the library.

Our :doc:`local installation guide <installation/uv>` provides more detailed
instructions, including best practices for setting up a suitable local environment.

.. toctree::
   :hidden:

   installation/uv

.. _conda-installation:

Installing Manim via Conda and related environment managers
***********************************************************

Conda is a package manager for Python that allows creating environments
where all your dependencies are stored. Like this, you don't clutter up your PC with
unwanted libraries and you can just delete the environment when you don't need it anymore.
It is a good way to install manim since all dependencies like ``pycairo``, etc. come with it.
Also, the installation steps are the same, no matter if you are
on Windows, Linux, Intel Macs or on Apple Silicon.

.. NOTE::

   There are various popular alternatives to Conda like
   `mamba <https://mamba.readthedocs.io/en/latest/>`__ /
   `micromamba <https://mamba.readthedocs.io/en/latest/user_guide/micromamba.html>`__,
   or `pixi <https://pixi.sh>`__.
   They all can be used to setup a suitable, isolated environment
   for your Manim projects.

The following pages show how to install Manim in a conda environment:

.. toctree::
   :maxdepth: 2

   installation/conda


.. _docker-installation:

Using Manim via Docker
**********************

`Docker <https://www.docker.com>`__ is a virtualization tool that
allows the distribution of encapsulated software environments (containers).

The following pages contain more information about the docker image
maintained by the community, ``manimcommunity/manim``:

.. toctree::

   installation/docker


.. _interactive-online:

Interactive Jupyter notebooks for your browser
**********************************************

Manim ships with a built-in ``%%manim`` IPython magic command
designed for the use within `Jupyter notebooks <https://jupyter.org>`__.
Our interactive tutorial over at https://try.manim.community illustrates
how Manim can be used from within a Jupyter notebook.

The following pages explain how you can setup interactive environments
like that yourself:

.. toctree::

   installation/jupyter

.. _editor-addons:

Editors
********

If you're using Visual Studio Code you can install an extension called
*Manim Sideview* which provides automated rendering and an integrated preview
of the animation inside the editor. The extension can be installed through the
`marketplace of VS Code <https://marketplace.visualstudio.com/items?itemName=Rickaym.manim-sideview>`__.

.. caution::

   This extension is not officially maintained by the Manim Community.
   If you run into issues, please report them to the extension's author.


Installation for developers
***************************

In order to change code in the library, it is recommended to
install Manim in a different way. Please follow the instructions
in our :doc:`contribution guide <contributing>` if you are
interested in that.
