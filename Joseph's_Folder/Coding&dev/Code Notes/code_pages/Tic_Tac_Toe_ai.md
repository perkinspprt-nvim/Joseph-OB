# Build a Tic-Tac-Toe Game Engine With an AI Player in Python

by [Bartosz Zaczyński](https://realpython.com/tic-tac-toe-ai-python/#author) Oct 19, 2022 [23 Comments](https://realpython.com/tic-tac-toe-ai-python/#reader-comments) [advanced](https://realpython.com/tutorials/advanced/) [best-practices](https://realpython.com/tutorials/best-practices/) [gamedev](https://realpython.com/tutorials/gamedev/) [gui](https://realpython.com/tutorials/gui/) [projects](https://realpython.com/tutorials/projects/) [python](https://realpython.com/tutorials/python/)

[Tweet](https://twitter.com/intent/tweet/?text=Check out this %23Python tutorial: Build%20a%20Tic-Tac-Toe%20Game%20Engine%20With%20an%20AI%20Player%20in%20Python by @realpython&url=https%3A//realpython.com/tic-tac-toe-ai-python/) [Share](https://facebook.com/sharer/sharer.php?u=https%3A//realpython.com/tic-tac-toe-ai-python/) [Email](mailto:?subject=Python article for you&body=Check out this Python tutorial:%0A%0ABuild%20a%20Tic-Tac-Toe%20Game%20Engine%20With%20an%20AI%20Player%20in%20Python%0A%0Ahttps%3A//realpython.com/tic-tac-toe-ai-python/)

Table of Contents

- [Demo: Tic-Tac-Toe AI Player in Python](https://realpython.com/tic-tac-toe-ai-python/#demo-tic-tac-toe-ai-player-in-python)
- [Project Overview](https://realpython.com/tic-tac-toe-ai-python/#project-overview)
- [Prerequisites](https://realpython.com/tic-tac-toe-ai-python/#prerequisites)
- [Step 1: Model the Tic-Tac-Toe Game Domain](https://realpython.com/tic-tac-toe-ai-python/#step-1-model-the-tic-tac-toe-game-domain)
    - [Enumerate the Players’ Marks](https://realpython.com/tic-tac-toe-ai-python/#enumerate-the-players-marks)
    - [Represent the Square Grid of Cells](https://realpython.com/tic-tac-toe-ai-python/#represent-the-square-grid-of-cells)
    - [Take a Snapshot of the Player’s Move](https://realpython.com/tic-tac-toe-ai-python/#take-a-snapshot-of-the-players-move)
    - [Determine the Game State](https://realpython.com/tic-tac-toe-ai-python/#determine-the-game-state)
    - [Introduce a Separate Validation Layer](https://realpython.com/tic-tac-toe-ai-python/#introduce-a-separate-validation-layer)
    - [Discard Incorrect Game States](https://realpython.com/tic-tac-toe-ai-python/#discard-incorrect-game-states)
    - [Simulate Moves by Producing New Game States](https://realpython.com/tic-tac-toe-ai-python/#simulate-moves-by-producing-new-game-states)
- [Step 2: Scaffold a Generic Tic-Tac-Toe Game Engine](https://realpython.com/tic-tac-toe-ai-python/#step-2-scaffold-a-generic-tic-tac-toe-game-engine)
    - [Pull the Players’ Moves to Drive the Game](https://realpython.com/tic-tac-toe-ai-python/#pull-the-players-moves-to-drive-the-game)
    - [Let the Computer Pick a Random Move](https://realpython.com/tic-tac-toe-ai-python/#let-the-computer-pick-a-random-move)
    - [Make an Abstract Tic-Tac-Toe Grid Renderer](https://realpython.com/tic-tac-toe-ai-python/#make-an-abstract-tic-tac-toe-grid-renderer)
- [Step 3: Build a Game Front End for the Console](https://realpython.com/tic-tac-toe-ai-python/#step-3-build-a-game-front-end-for-the-console)
    - [Render the Grid With ANSI Escape Codes](https://realpython.com/tic-tac-toe-ai-python/#render-the-grid-with-ansi-escape-codes)
    - [Create an Interactive Console Player](https://realpython.com/tic-tac-toe-ai-python/#create-an-interactive-console-player)
    - [Add a Command-Line Interface (CLI)](https://realpython.com/tic-tac-toe-ai-python/#add-a-command-line-interface-cli)
- [Step 4: Equip the Computer With Artificial Intelligence](https://realpython.com/tic-tac-toe-ai-python/#step-4-equip-the-computer-with-artificial-intelligence)
    - [Evaluate the Score of a Finished Game](https://realpython.com/tic-tac-toe-ai-python/#evaluate-the-score-of-a-finished-game)
    - [Propagate the Score With the Minimax Algorithm](https://realpython.com/tic-tac-toe-ai-python/#propagate-the-score-with-the-minimax-algorithm)
    - [Make an Undefeatable Minimax Computer Player](https://realpython.com/tic-tac-toe-ai-python/#make-an-undefeatable-minimax-computer-player)
- [Conclusion](https://realpython.com/tic-tac-toe-ai-python/#conclusion)
- [Next Steps](https://realpython.com/tic-tac-toe-ai-python/#next-steps)

[Remove ads](https://realpython.com/account/join/)

When you’re a child, you learn to play [tic-tac-toe](https://en.wikipedia.org/wiki/Tic-tac-toe), which some people know as naughts and crosses. The game remains fun and challenging until you enter your teenage years. Then, you learn to program and discover the joy of coding a virtual version of this two-player game. As an adult, you may still appreciate the simplicity of the game by using Python to create an opponent with **artificial intelligence (AI)**.

By completing this detailed step-by-step adventure, you’ll build an extensible **game engine** with an **unbeatable computer player** that uses the **minimax algorithm** to play tic-tac-toe. Along the way, you’ll dive into immutable class design, generic plug-in architecture, and modern Python code practices and patterns.

**In this tutorial, you’ll learn how to:**

- Create a reusable **Python library** with the tic-tac-toe game engine
- Model the **domain** of tic-tac-toe following Pythonic code style
- Implement artificial players including one based on the **minimax algorithm**
- Build a text-based **console front end** for the game with a human player
- Explore strategies for **performance optimizations**

Click the link below to download the complete source code for this project:

**Source Code:** [Click here to download the free source code](https://realpython.com/bonus/tic-tac-toe-ai-python-code/) that you’ll use to build a tic-tac-toe game engine and AI player with Python.

## Demo: Tic-Tac-Toe AI Player in Python[](https://realpython.com/tic-tac-toe-ai-python/#demo-tic-tac-toe-ai-player-in-python "Permanent link")

By the end of this tutorial, you’ll have a highly reusable and extensible **Python library** with an abstract [game engine](https://realpython.com/top-python-game-engines/) for tic-tac-toe. It’ll encapsulate universal game rules and computer players, including one that never loses due to bare-bones artificial intelligence support. In addition, you’ll create a sample **console front end** that builds on top of your library and implements a text-based interactive tic-tac-toe game running in the terminal.

Here’s what actual gameplay between two players might look like:

Console Front End

Generally, you may mix and choose the players from among a human player, a dummy computer player making moves at random, and a smart computer player sticking to the optimal strategy. You can also specify which player should make the first move, increasing their chances of winning or tying.

Later, you’ll be able to adapt your generic tic-tac-toe library for different platforms, such as a **windowed desktop environment** or a **web browser**. While you’ll only follow instructions on building a console application in this tutorial, you can find [Tkinter](https://realpython.com/python-gui-tkinter/) and [PyScript](https://realpython.com/pyscript-python-in-browser/) front end examples in the supporting materials.

**Note:** These front ends aren’t covered here because implementing them requires considerable familiarity with [threading](https://realpython.com/intro-to-python-threading/), [asyncio](https://realpython.com/async-io-python/), and [queues](https://realpython.com/queue-in-python/) in Python, which is beyond the scope of this tutorial. But feel free to study and play around with the sample code on your own.

The Tkinter front end is a streamlined version of the same game that’s described in a [separate tutorial](https://realpython.com/tic-tac-toe-python/), which only serves as a demonstration of the library in a desktop environment:

Tkinter Front End

Unlike the original, it doesn’t look as slick, nor does it allow you to restart the game easily. However, it adds the option to play against the computer or another human player if you want to.

The PyScript front end lets you or your friends play the game in a web browser even when they don’t have [Python installed on their computer](https://realpython.com/installing-python/), which is a notable benefit:

PyScript Front End

If you’re adventurous and know a little bit of PyScript or [JavaScript](https://realpython.com/python-vs-javascript/), then you could extend this front end by adding the ability to play online with another human player through the network. To facilitate the communication, you’d need to implement a remote web server using the [WebSocket](https://en.wikipedia.org/wiki/WebSocket) protocol, for instance. Take a look at a working [WebSocket client and server example](https://realpython.com/python-xml-parser/#bind-xml-data-to-python-objects) in another tutorial to get an idea of how that might work.

It’s worth noting that each of the three front ends demonstrated in this section merely implement a different **presentation layer** for the same Python library, which provides the underlying game logic and players. There’s no unnecessary redundancy or code duplication across them, thanks to the clear [separation of concerns](https://en.wikipedia.org/wiki/Separation_of_concerns) and other programming principles that you’ll practice in this tutorial.

[Remove ads](https://realpython.com/account/join/)

## Project Overview[](https://realpython.com/tic-tac-toe-ai-python/#project-overview "Permanent link")

The project that you’re going to build consists of two high-level components depicted in the diagram below:

[![Tic-Tac-Toe Architecture Diagram](https://files.realpython.com/media/diagram.4802afdb24e3.png)](https://files.realpython.com/media/diagram.4802afdb24e3.png)

Tic-Tac-Toe Architecture Diagram

The first component is an abstract tic-tac-toe Python library, which remains agnostic about the possible ways of presenting the game to the user in a graphical form. Instead, it contains the core logic of the game and two artificial players. However, the library can’t stand on its own, so you’re also going to create a sample front end to collect user input from the keyboard and visualize the game in the console using plain text.

You’ll start by implementing the low-level details of the tic-tac-toe library, and then you’ll use those to implement a higher-level game front end in a bottom-up fashion. When you finish this tutorial, the complete file structure resulting will look like this:

```
tic-tac-toe/
│
├── frontends/
│   │
│   └── console/
│       ├── __init__.py
│       ├── __main__.py
│       ├── args.py
│       ├── cli.py
│       ├── players.py
│       └── renderers.py
│
└── library/
    │
    ├── src/
    │   │
    │   └── tic_tac_toe/
    │       │
    │       ├── game/
    │       │   ├── __init__.py
    │       │   ├── engine.py
    │       │   ├── players.py
    │       │   └── renderers.py
    │       │
    │       ├── logic/
    │       │   ├── __init__.py
    │       │   ├── exceptions.py
    │       │   ├── minimax.py
    │       │   ├── models.py
    │       │   └── validators.py
    │       │
    │       └── __init__.py
    │
    └── pyproject.toml
```

The `frontends/` folder is meant to house one or more concrete game implementations, such as your text-based console one, while `library/` is the home folder for the game library. You can think of both top-level folders as related yet separate projects.

Notice that your console front end contains the `__main__.py` file, making it a [runnable Python package](https://docs.python.org/3/library/__main__.html#main-py-in-python-packages) that you’ll be able to invoke from the command line using Python’s `-m` option. Assuming that you changed the current working directory to `frontends/` after downloading the complete source code that you’ll be writing in this tutorial, you can start the game with the following command:

`(venv) $ python -m console`

Remember that Python must be able to find the tic-tac-toe library, which your front end depends on, on the module search path. The best practice for ensuring this is by creating and activating a shared [virtual environment](https://realpython.com/python-virtual-environments-a-primer/) and installing the library with [`pip`](https://realpython.com/what-is-pip/). You’ll find detailed instructions on how to do this in the README file in the supporting materials.

The tic-tac-toe library is a Python package named `tic_tac_toe` consisting of two subpackages:

1. `tic_tac_toe.game`: A scaffolding designed to be extended by front ends
2. `tic_tac_toe.logic`: The building blocks of the tic-tac-toe game

You’ll dive deeper into each of them soon. The [`pyproject.toml`](https://realpython.com/pypi-publish-python-package/) file contains the metadata necessary for building and packaging the library. To install the downloaded library or the finished code that you’ll build in this tutorial into an active virtual environment, try this command:

`(venv) $ python -m pip install --editable library/`

During development, you can make an [editable install](https://setuptools.pypa.io/en/latest/userguide/development_mode.html) using `pip` with the `-e` or `--editable` flag to mount the library’s source code instead of the built package in your virtual environment. This will prevent you from having to repeat the installation after making changes to the library to reflect them in your front end.

Okay, that’s what you’re going to build! But before you get started, check out the prerequisites.

## Prerequisites[](https://realpython.com/tic-tac-toe-ai-python/#prerequisites "Permanent link")

This is an advanced tutorial touching on a wide range of Python concepts that you should be comfortable with in order to move on smoothly. Please use the following resources to familiarize yourself with or refresh your memory on a few important topics:

- [Object-oriented programming (OOP)](https://realpython.com/python3-object-oriented-programming/)
- [Inheritance and composition](https://realpython.com/inheritance-composition-python/)
- [Abstract classes](https://realpython.com/python-interface/)
- [Data classes](https://realpython.com/python-data-classes/)
- [Type hints](https://realpython.com/python-type-checking/)
- [Regular expressions](https://realpython.com/regex-python/)
- [Caching](https://realpython.com/lru-cache-python/)
- [Recursion](https://realpython.com/python-recursion/)

The project that you’re going to build relies solely on Python’s **standard library** and has no external dependencies. That said, you’ll need at least [Python 3.10](https://realpython.com/python310-new-features/) or later to take advantage of the latest syntax and features leveraged in this tutorial. If you’re currently using an older Python release, then you can install and [manage multiple Python versions with `pyenv`](https://realpython.com/intro-to-pyenv/) or [try the latest Python release in Docker](https://realpython.com/python-versions-docker/).

Lastly, you should know the rules of the game that you’ll be implementing. The classic [tic-tac-toe](https://en.wikipedia.org/wiki/Tic-tac-toe) is played on a three-by-three grid of cells or squares where each player places their mark, an X or an O, in an empty cell. The first player to place three of their marks in a row horizontally, vertically, or diagonally wins the game.

[Remove ads](https://realpython.com/account/join/)

## Step 1: Model the Tic-Tac-Toe Game Domain[](https://realpython.com/tic-tac-toe-ai-python/#step-1-model-the-tic-tac-toe-game-domain "Permanent link")

In this step, you’ll identify the parts that make up a tic-tac-toe game and implement them using an **object-oriented** approach. By modeling the [domain](https://en.wikipedia.org/wiki/Domain_(software_engineering)) of the game with **immutable objects**, you’ll end up with modular and composable code that’s easier to test, maintain, debug, and reason about, among several other advantages.

For starters, open the [code editor](https://realpython.com/python-ides-code-editors-guide/) of your choice, such as [Visual Studio Code](https://realpython.com/python-development-visual-studio-code/) or [PyCharm](https://realpython.com/pycharm-guide/), and create a new project called `tic-tac-toe`, which will also become the name of your project folder. Nowadays, most code editors will give you the option to create a **virtual environment** for your project automatically, so go ahead and follow suit. If yours doesn’t, then make the virtual environment manually from the command line:

`$ cd tic-tac-toe/ $ python3 -m venv venv/`

This will create a folder named `venv/` under `tic-tac-toe/`. You don’t have to activate your new virtual environment unless you plan to continue working in the current command-line session.

Next, scaffold this basic structure of files and folders in your new project, remembering to use underscores (`_`) instead of dashes (`-`) for the Python package in the `src/` subfolder:

```
tic-tac-toe/
│
├── frontends/
│   │
│   └── console/
│       ├── __init__.py
│       └── __main__.py
│
└── library/
    │
    ├── src/
    │   │
    │   └── tic_tac_toe/
    │       │
    │       ├── game/
    │       │   └── __init__.py
    │       │
    │       ├── logic/
    │       │   └── __init__.py
    │       │
    │       └── __init__.py
    │
    └── pyproject.toml
```

All of the files in the file tree above should be empty at this point. You’ll successively fill them with content and add more files as you go through this tutorial. Start by editing the `pyproject.toml` file located next to your `src/` subfolder. You can paste this fairly minimal packaging configuration for your tic-tac-toe library into it:

`# pyproject.toml  [build-system] requires = ["setuptools>=64.0.0", "wheel"] build-backend = "setuptools.build_meta"  [project] name = "tic-tac-toe" version = "1.0.0"`

You specify the required build tools, which Python will download and install if necessary, along with some metadata for your project. Adding the `pyproject.toml` file to the library lets you build and install it as a [Python package](https://realpython.com/python-modules-packages/) into your active virtual environment.

**Note:** The `pyproject.toml` file is a standard configuration file using the [TOML](https://realpython.com/python-toml/) format for specifying minimum build system requirements for Python projects. The concept was introduced in [PEP 518](https://peps.python.org/pep-0518/) and is now the recommended way of adding packaging metadata and configuration in Python. You’re going to need this to install the tic-tac-toe library into your virtual environment.

Open the [terminal](https://realpython.com/terminal-commands/) window and issue the following commands to activate your virtual environment if you haven’t already, and install the tic-tac-toe library using the editable mode:

`$ source venv/bin/activate (venv) $ python -m pip install --editable library/`

Even though there’s no Python code in your library yet, installing it now with the `--editable` flag will let the Python interpreter import the functions and classes that you’ll be adding shortly straight from your project. Otherwise, every single time you made a change in your source code and wanted to test it, you’d have to remember to build and install the library into your virtual environment again.

Now that you have a general structure for your project, you can start implementing some code. By the end of this step, you’ll have all the essential pieces of a tic-tac-toe game in place, including the game logic and state validation, so you’ll be ready to combine them in an abstract game engine.

### Enumerate the Players’ Marks[](https://realpython.com/tic-tac-toe-ai-python/#enumerate-the-players-marks "Permanent link")

At the start of the game, each tic-tac-toe player gets assigned one of two symbols, either **cross (X)** or **naught (O)**, which they use to mark locations on the game board. Since there are only two symbols belonging to a fixed set of discrete values, you can define them within an [enumerated type](https://en.wikipedia.org/wiki/Enumerated_type) or [enum](https://realpython.com/python-enum/). Using enums is preferable over [constants](https://realpython.com/python-constants/) due to their enhanced type safety, common namespace, and programmatic access to their members.

Create a new Python module called `models` in the `tic_tac_toe.logic` package:

```
tic-tac-toe/
│
└── library/
    │
    ├── src/
    │   │
    │   └── tic_tac_toe/
    │       │
    │       ├── game/
    │       │   └── __init__.py
    │       │
    │       ├── logic/
    │       │   ├── __init__.py
    │       │   └── models.py
    │       │
    │       └── __init__.py
    │
    └── pyproject.toml
```

You’ll use this file throughout the rest of this step to define tic-tac-toe [domain model](https://en.wikipedia.org/wiki/Domain_model) objects.

Now, import the [`enum`](https://docs.python.org/3/library/enum.html#module-enum) module from Python’s standard library and define a new data type in your models:

```
# tic_tac_toe/logic/models.py

import enum

class Mark(enum.Enum):
    CROSS = "X"
    NAUGHT = "O"
```

The two [singleton](https://en.wikipedia.org/wiki/Singleton_pattern) instances of the `Mark` class, the enum members `Mark.CROSS` and `Mark.NAUGHT`, represent the players’ symbols. By default, you can’t compare a member of a Python enum against its value. For instance, comparing `Mark.CROSS == "X"` will give you `False`. This is by design to avoid confusing identical values defined in different places and having unrelated semantics.

However, it may sometimes be more convenient to think about the player marks in terms of strings instead of enum members. To make that happen, define `Mark` as a [mixin class](https://realpython.com/inheritance-composition-python/#mixing-features-with-mixin-classes) of the `str` and `enum.Enum` types:

```
# tic_tac_toe/logic/models.py

import enum

class Mark(str, enum.Enum):
    CROSS = "X"
    NAUGHT = "O"
```

This is known as a [derived enum](https://docs.python.org/3/library/enum.html#derived-enumerations), whose members can be compared to instances of the mixed-in type. In this case, you can now compare `Mark.NAUGHT` and `Mark.CROSS` to string values.

**Note:** Python 3.10 was the latest release at the time of writing this tutorial, but if you’re using a newer release, then you can directly extend [`enum.StrEnum`](https://docs.python.org/3.11/library/enum.html#enum.StrEnum), which was added to the standard library in Python 3.11:

`import enum  class Mark(enum.StrEnum):     CROSS = "X"     NAUGHT = "O"`

Members of `enum.StrEnum` are also strings, which means that you can use them almost anywhere that a regular string is expected.

Once you assign a given mark to the first player, the second player must be assigned the only remaining and unassigned mark. Because enums are glorified classes, you’re free to put ordinary methods and [properties](https://realpython.com/python-property/) into them. For example, you can define a property of a `Mark` member that’ll return the other member:

```
# tic_tac_toe/logic/models.py

import enum

class Mark(str, enum.Enum):
    CROSS = "X"
    NAUGHT = "O"

    @property
    def other(self) -> "Mark":
        return Mark.CROSS if self is Mark.NAUGHT else Mark.NAUGHT
```

The body of your property is a single line of code that uses a [conditional expression](https://realpython.com/python-conditional-statements/#conditional-expressions-pythons-ternary-operator) to determine the correct mark. The quotation marks around the [return type](https://en.wikipedia.org/wiki/Return_type) in your property’s signature are mandatory to make a [forward declaration](https://en.wikipedia.org/wiki/Forward_declaration) and avoid an error due to an unresolved name. After all, you claim to return a `Mark`, which hasn’t been fully defined yet.

**Note:** Alternatively, you can [postpone the evaluation of annotations](https://peps.python.org/pep-0563/) until after they’ve been defined:

`# tic_tac_toe/logic/models.py  from __future__ import annotations import enum  class Mark(str, enum.Enum):     CROSS = "X"     NAUGHT = "O"      @property     def other(self) -> Mark:        return Mark.CROSS if self is Mark.NAUGHT else Mark.NAUGHT`

Adding a special `__future__` import, which must appear at the beginning of your file, enables the lazy evaluation of type hints. You’ll use this pattern later to avoid the [circular reference](https://en.wikipedia.org/wiki/Circular_reference) problem when importing cross-referencing modules.

In Python 3.11, you can also use a universal [`typing.Self`](https://realpython.com/python311-tomllib/#self-type) type to avoid the forward declaration in type hints in the first place.

To reveal a few practical examples of using the `Mark` enum, expand the collapsible section below:

You now have a way to represent the available markings that players will leave on the board to advance the game. Next, you’ll implement an abstract game board with well defined locations for those markings.

[Remove ads](https://realpython.com/account/join/)

### Represent the Square Grid of Cells[](https://realpython.com/tic-tac-toe-ai-python/#represent-the-square-grid-of-cells "Permanent link")

While some people play variants of tic-tac-toe with different numbers of players or different sizes of grids, you’ll stick with the most basic and classic rules. Recall that the game’s board is represented by a three-by-three grid of cells in the classic tic-tac-toe. Each cell can be empty or marked with either a cross or a naught.

Because you represent marks with a single character, you can implement the grid using a string of precisely **nine characters** corresponding to the cells. A cell can be empty, in which case you’ll fill it with the space character (`" "`), or it can contain the player’s mark. In this tutorial, you’ll store the grid in [row-major order](https://en.wikipedia.org/wiki/Row-_and_column-major_order) by concatenating the rows from top to bottom.

For example, with such a representation, you could express the [three gameplays demonstrated before](https://realpython.com/tic-tac-toe-ai-python/#demo-tic-tac-toe-ai-player-in-python) with the following string literals:

- `"XXOXO O "`
- `"OXXXXOOOX"`
- `"OOOXXOXX "`

To better visualize them, you can whip up and run this short function in an interactive Python interpreter session:

`>>> def preview(cells): ...     print(cells[:3], cells[3:6], cells[6:], sep="\n")  >>> preview("XXOXO O  ") XXO XO O  >>> preview("OXXXXOOOX") OXX XXO OOX  >>> preview("OOOXXOXX ") OOO XXO XX`

The function takes a string of cells as an argument and prints it onto the screen in the form of three separate rows carved out with the [slice operator](https://realpython.com/python-strings/#string-slicing) from the input string.

While using strings to represent the grid of cells is pretty straightforward, it falls short in terms of validating its shape and content. Other than that, plain strings can’t provide some extra, grid-specific properties that you might be interested in. For these reasons, you’ll create a new `Grid` data type on top of a string wrapped in an attribute:

`# tic_tac_toe/logic/models.py  import enum from dataclasses import dataclass # ...  @dataclass(frozen=True) class Grid:     cells: str = " " * 9`

You define `Grid` as a [frozen data class](https://realpython.com/python-data-classes/#immutable-data-classes) to make its instances immutable so that once you create a grid object, you won’t be able to alter its cells. This may sound limiting and wasteful at first because you’ll be forced to make many instances of the `Grid` class instead of just reusing one object. However, the [benefits of immutable objects](https://hackernoon.com/5-benefits-of-immutable-objects-worth-considering-for-your-next-project-f98e7e85b6ac), including fault tolerance and improved code readability, far outweigh the costs in modern computers.

By default, when you don’t specify any value for the `.cells` attribute, it’ll assume a string of exactly nine spaces to reflect an **empty grid**. However, you can still initialize the grid with the wrong value for cells, ultimately crashing the program. You can prevent this by allowing your objects only to exist if they’re in a valid state. Otherwise, they won’t be created at all, following the [fail-fast](https://en.wikipedia.org/wiki/Fail-fast) and [always-valid domain model](https://enterprisecraftsmanship.com/posts/always-valid-domain-model/) principles.

Data classes take control of object initialization, but they also let you run a [post-initialization hook](https://docs.python.org/3/library/dataclasses.html#post-init-processing) to set derived properties based on the values of other fields, for example. You’ll take advantage of this mechanism to perform **cell validation** and potentially discard invalid strings before instantiating a grid object:

`# tic_tac_toe/logic/models.py  import enum import re from dataclasses import dataclass  # ...  @dataclass(frozen=True) class Grid:     cells: str = " " * 9      def __post_init__(self) -> None:        if not re.match(r"^[\sXO]{9}$", self.cells):            raise ValueError("Must contain 9 cells of: X, O, or space")`

Your special `.__post_init__()` method uses a [regular expression](https://realpython.com/regex-python/) to check whether the given value of the `.cells` attribute is exactly nine characters long and contains only the expected characters—that is, `"X"`, `"O"`, or `" "`. There are other ways to validate strings, but regular expressions are very compact and will remain consistent with the future validation rules that you’ll add later.

**Note:** The grid is only responsible for validating the syntactical correctness of a string of cells, but it doesn’t understand the higher-level rules of the game. You’ll implement the validation of a particular cell combination’s semantics elsewhere once you gain additional context.

At this point, you can add a few **extra properties** to your `Grid` class, which will become handy when determining the state of the game:

`# tic_tac_toe/logic/models.py  import enum import re from dataclasses import dataclass from functools import cached_property # ...  @dataclass(frozen=True) class Grid:     cells: str = " " * 9      def __post_init__(self) -> None:         if not re.match(r"^[\sXO]{9}$", self.cells):             raise ValueError("Must contain 9 cells of: X, O, or space")      @cached_property    def x_count(self) -> int:        return self.cells.count("X")     @cached_property    def o_count(self) -> int:        return self.cells.count("O")     @cached_property    def empty_count(self) -> int:        return self.cells.count(" ")`

The three properties return the current number of crosses, naughts, and empty cells, respectively. Because your data class is immutable, its state will never change, so you can [cache the computed property values](https://realpython.com/python-property/#caching-computed-attributes) with the help of the `@cached_property` decorator from the `functools` module. This will ensure that their code will run at most once, no matter how many times you access these properties, for example during validation.

To reveal a few practical examples of using the `Grid` class, expand the collapsible section below:

Using Python code, you modeled a three-by-three grid of cells, which can contain a particular combination of players’ marks. Now, it’s time to model the player’s move so that artificial intelligence can evaluate and choose the best option.

[Remove ads](https://realpython.com/account/join/)

### Take a Snapshot of the Player’s Move[](https://realpython.com/tic-tac-toe-ai-python/#take-a-snapshot-of-the-players-move "Permanent link")

An object representing the player’s move in tic-tac-toe should primarily answer the following two questions:

1. **Player’s Mark:** What mark did the player place?
2. **Mark’s Location:** Where was it placed?

However, in order to have the complete picture, one must also know about the **state of the game** before making a move. After all, it can be a good or a bad move, depending on the current situation. You may also find it convenient to have the resulting state of the game at hand so that you can assign it a score. By **simulating that move**, you’ll be able to compare it with other possible moves.

**Note:** A move object can’t validate itself without knowing some of the game details, such as the starting player’s mark, which aren’t available to it. You’ll check whether a given move is valid, along with validating a specific grid cell combination, in a class responsible for managing the game’s state.

Based on these thoughts, you can add another immutable data class to your models:

`# tic_tac_toe/logic/models.py  # ...  class Mark(str, enum.Enum):     ...  @dataclass(frozen=True) class Grid:     ...  @dataclass(frozen=True) class Move:     mark: Mark    cell_index: int    before_state: "GameState"    after_state: "GameState"`

Please ignore the two forward declarations of the `GameState` class for the moment. You’ll define that class in the next section, using the type hint as a temporary placeholder.

Your new class is strictly a [data transfer object (DTO)](https://en.wikipedia.org/wiki/Data_transfer_object) whose main purpose is to carry data, as it doesn’t provide any behavior through methods or dynamically computed properties. Objects of the `Move` class consist of the mark identifying the player who made a move, a numeric zero-based index in the string of cells, and the two states before and after making a move.

The `Move` class will be instantiated, populated with values, and manipulated by the missing `GameState` class. Without it, you won’t be able to correctly create the move objects yourself. It’s time to fix that now!

### Determine the Game State[](https://realpython.com/tic-tac-toe-ai-python/#determine-the-game-state "Permanent link")

A tic-tac-toe game can be in one of several states, including three possible outcomes:

1. The game hasn’t started yet.
2. The game is still going on.
3. The game has finished in a tie.
4. The game has finished with player X winning.
5. The game has finished with player O winning.

You can determine the current state of a tic-tac-toe game based on two parameters:

1. The combination of cells in the grid
2. The mark of the starting player

Without knowing who started the game, you won’t be able to tell whose turn it is now and whether the given move is valid. Ultimately, you can’t properly assess the situation so that the artificial intelligence can make the right decision.

To fix that, begin by specifying the **game state** as another immutable data class consisting of the grid of cells and the starting player’s mark:

`# tic_tac_toe/logic/models.py  # ...  class Mark(str, enum.Enum):     ...  @dataclass(frozen=True) class Grid:     ...  @dataclass(frozen=True) class Move:     ...  @dataclass(frozen=True) class GameState:     grid: Grid    starting_mark: Mark = Mark("X")`

By convention, the player who marks the cells with crosses starts the game, hence the default value of `Mark("X")` for the starting player’s mark. However, you can change it according to your preference by supplying a different value at runtime.

Now, add a cached property returning the mark of the player who should make the next move:

`# tic_tac_toe/logic/models.py  # ...  @dataclass(frozen=True) class GameState:     grid: Grid     starting_mark: Mark = Mark("X")      @cached_property    def current_mark(self) -> Mark:        if self.grid.x_count == self.grid.o_count:            return self.starting_mark        else:            return self.starting_mark.other`

The **current player’s mark** will be the same as the starting player’s mark when the grid is empty or when both players have marked an equal number of cells. In practice, you only need to check the latter condition because a blank grid implies that both players have zero marks in the grid. To determine the other player’s mark, you can take advantage of your `.other` property in the `Mark` enum.

Next up, you’ll add some properties for evaluating the **current state** of the game. For example, you can tell that the game hasn’t started yet when the grid is blank, or contains exactly nine empty cells:

`# tic_tac_toe/logic/models.py  # ...  @dataclass(frozen=True) class GameState:     # ...      @cached_property     def current_mark(self) -> Mark:         ...      @cached_property    def game_not_started(self) -> bool:        return self.grid.empty_count == 9`

This is where your grid’s properties come in handy. Conversely, you can conclude that the **game has finished** when there’s a clear winner or there’s a tie:

`# tic_tac_toe/logic/models.py  # ...  @dataclass(frozen=True) class GameState:     # ...      @cached_property     def current_mark(self) -> Mark:         ...      @cached_property     def game_not_started(self) -> bool:         ...      @cached_property    def game_over(self) -> bool:        return self.winner is not None or self.tie`

The `.winner` property, which you’ll implment in a bit, will return a `Mark` instance or `None`, whereas the `.tie` property will be a [Boolean](https://realpython.com/python-boolean/) value. A **tie** is when neither player has won, which means there’s no winner, and all of the squares are filled, leaving zero empty cells:

`# tic_tac_toe/logic/models.py  # ...  @dataclass(frozen=True) class GameState:     # ...      @cached_property     def current_mark(self) -> Mark:         ...      @cached_property     def game_not_started(self) -> bool:         ...      @cached_property     def game_over(self) -> bool:         ...      @cached_property    def tie(self) -> bool:        return self.winner is None and self.grid.empty_count == 0`

Both the `.game_over` and `.tie` properties rely on the `.winner` property, which they delegate to. Finding a **winner** is slightly more difficult, though. You can, for example, try to match the current grid of cells against a predefined collection of winning patterns with regular expressions:

`# tic_tac_toe/logic/models.py  # ...  WINNING_PATTERNS = (     "???......",    "...???...",    "......???",    "?..?..?..",    ".?..?..?.",    "..?..?..?",    "?...?...?",    "..?.?.?..", ) class Mark(str, enum.Enum):     ...  class Grid:     ...  class Move:     ...  @dataclass(frozen=True) class GameState:     # ...      @cached_property     def current_mark(self) -> Mark:         ...      @cached_property     def game_not_started(self) -> bool:         ...      @cached_property     def game_over(self) -> bool:         ...      @cached_property     def tie(self) -> bool:         ...      @cached_property    def winner(self) -> Mark | None:        for pattern in WINNING_PATTERNS:            for mark in Mark:                if re.match(pattern.replace("?", mark), self.grid.cells):                    return mark        return None`

There are eight winning patterns for each of the two players, which you define using templates resembling regular expressions. The templates contain question-mark placeholders for the concrete player’s mark. You iterate over those templates and replace the question marks with both players’ marks to synthesize two regular expressions per pattern. When the cells match a winning pattern, you return the corresponding mark. Otherwise, you return `None`.

Knowing the winner is one thing, but you may also want to know the matched **winning cells** to differentiate them visually. In this case, you can add a similar property, which uses a [list comprehension](https://realpython.com/list-comprehension-python/) to return a list of integer indices of the winning cells:

`# tic_tac_toe/logic/models.py  # ...  WINNING_PATTERNS = (     "???......",     "...???...",     "......???",     "?..?..?..",     ".?..?..?.",     "..?..?..?",     "?...?...?",     "..?.?.?..", )  class Mark(str, enum.Enum):     ...  class Grid:     ...  class Move:     ...  @dataclass(frozen=True) class GameState:     # ...      @cached_property     def current_mark(self) -> Mark:         ...      @cached_property     def game_not_started(self) -> bool:         ...      @cached_property     def game_over(self) -> bool:         ...      @cached_property     def tie(self) -> bool:         ...      @cached_property     def winner(self) -> Mark | None:         ...      @cached_property    def winning_cells(self) -> list[int]:        for pattern in WINNING_PATTERNS:            for mark in Mark:                if re.match(pattern.replace("?", mark), self.grid.cells):                    return [                        match.start()                        for match in re.finditer(r"\?", pattern)                    ]        return []`

You might be concerned about having a bit of code duplication between `.winner` and `.winnning_cells`, which violates the [Don’t Repeat Yourself (DRY)](https://en.wikipedia.org/wiki/Don't_repeat_yourself) principle, but that’s okay. The [Zen of Python](https://realpython.com/zen-of-python/) says that _practicality beats purity_, and indeed, extracting the common denominator would provide little value here while making the code less readable.

**Note:** It usually makes sense to start thinking about [refactoring](https://en.wikipedia.org/wiki/Code_refactoring) your code when there are at least three instances of a duplicated code fragment. There’s a high chance that you’ll need to reuse the same piece of code even more.

Your `GameState` is starting to look pretty good. It can correctly recognize all possible game states, but it lacks proper validation, making it prone to runtime errors. In the next few sections, you’ll rectify that by codifying and enforcing a few tic-tac-toe rules.

[Remove ads](https://realpython.com/account/join/)

### Introduce a Separate Validation Layer[](https://realpython.com/tic-tac-toe-ai-python/#introduce-a-separate-validation-layer "Permanent link")

As with the grid, creating an instance of the `GameState` class should fail when the supplied combination of cells and the starting player’s mark don’t make sense. For example, it’s currently possible to create an invalid game state that doesn’t reflect genuine gameplay. You can test it yourself.

Start an interactive Python interpreter session in the virtual environment where you had previously installed your library, and then run the following code:

`>>> from tic_tac_toe.logic.models import GameState, Grid >>> GameState(Grid("XXXXXXXXX")) GameState(grid=Grid(cells='XXXXXXXXX'), starting_mark=<Mark.CROSS: 'X'>)`

Here, you initialize a new game state using a grid comprising a _syntactically_ correct string with the right characters and length. However, such a cell combination is _semantically_ incorrect because one player isn’t allowed to fill the entire grid with their mark.

Because validating the game state is relatively involved, implementing it in the domain model would violate the [single-responsibility principle](https://en.wikipedia.org/wiki/Single-responsibility_principle) and make your code less readable. Validation belongs to a separate layer in your architecture, so you should keep the domain model and its validation logic in two different Python modules without mixing their code. Go ahead and create two new files in your project:

`tic-tac-toe/ │ └── library/     │     ├── src/     │   │     │   └── tic_tac_toe/     │       │     │       ├── game/     │       │   └── __init__.py     │       │     │       ├── logic/     │       │   ├── __init__.py     │       │   ├── exceptions.py    │       │   ├── models.py     │       │   └── validators.py    │       │     │       └── __init__.py     │     └── pyproject.toml`

You’ll store various helper functions in `validators.py` and a few exception classes in the `exceptions.py` file to [decouple](https://en.wikipedia.org/wiki/Coupling_(computer_programming)) game state validation from the model.

For improved **code consistency**, you can extract the grid validation that you defined earlier in the `__post_init__()` method, move it into the newly created Python module, and wrap it in a new function:

`# tic_tac_toe/logic/validators.py  import re  from tic_tac_toe.logic.models import Grid  def validate_grid(grid: Grid) -> None:     if not re.match(r"^[\sXO]{9}$", grid.cells):         raise ValueError("Must contain 9 cells of: X, O, or space")`

Note that you replaced `self.cells` with `grid.cells` because you’re now referring to a grid instance through the function’s argument.

If you’re using PyCharm, then it might have started highlighting an unresolved reference to `tic_tac_toe`, which isn’t present on the search path for Python modules and packages. PyCharm doesn’t seem to recognize editable installs correctly, but you can fix that by right-clicking on your `src/` folder and marking it as the so-called _sources root_ in the project view:

Mark Directory as Sources Root in PyCharm

You can have as many folders marked as sources roots as you want. Doing so will append their absolute paths to the [`PYTHONPATH`](https://docs.python.org/3/using/cmdline.html#envvar-PYTHONPATH) environment variable managed by PyCharm. However, this won’t affect your environment outside of PyCharm, so running a script through the system’s terminal won’t benefit from marking those folders. Instead, you can activate the virtual environment with your library installed to import its code.

After extracting the grid validation logic, you should update the corresponding part in your `Grid` model by delegating the validation to an appropriate abstraction:

 `# tic_tac_toe/logic/models.py   import enum  import re  from dataclasses import dataclass  from functools import cached_property  +from tic_tac_toe.logic.validators import validate_grid  # ...   @dataclass(frozen=True)  class Grid:      cells: str = " " * 9       def __post_init__(self) -> None: -        if not re.match(r"^[\sXO]{9}$", self.cells): -            raise ValueError("Must contain 9 cells of: X, O, or space") +        validate_grid(self)      @cached_property      def x_count(self) -> int:          return self.cells.count("X")       @cached_property      def o_count(self) -> int:          return self.cells.count("O")       @cached_property      def empty_count(self) -> int:          return self.cells.count(" ")   # ...`

You import the new helper function and call it in your grid’s post-initialization hook, which now uses a higher-level vocabulary to communicate its intent. Previously, some low-level details, such as the use of regular expressions, were leaking into your model, and it wasn’t immediately clear what the `.__post_init__()` method does.

Unfortunately, this change now creates the notorious **circular-reference problem** between your model and validator layers, which mutually depend on each other’s bits. When you try to import `Grid`, you’ll get this error:

`Traceback (most recent call last):   ... ImportError: cannot import name 'Grid' from partially initialized module 'tic_tac_toe.logic.models' (most likely due to a circular import) (.../tic_tac_toe/logic/models.py)`

That’s because Python reads the source code from top to bottom. As soon as it encounters an [`import`](https://realpython.com/python-import/) statement, it’ll jump to the imported file and start reading it. However, in this case, the imported `validators` module wants to import the `models` module, which hasn’t been fully processed yet. This is a very common problem in Python when you start using type hints.

The only reason you need to import `models` is because of a type hint in your validating function. You could get away without the import statement by surrounding the type hint with quotes (`"Grid"`) to make a forward declaration like before. However, you’ll follow a different idiom this time. You can combine the postponed evaluation of annotations with a special [`TYPE_CHECKING`](https://docs.python.org/3/library/typing.html#typing.TYPE_CHECKING) constant:

 `# tic_tac_toe/logic/validators.py  +from __future__ import annotations +from typing import TYPE_CHECKING +if TYPE_CHECKING: +    from tic_tac_toe.logic.models import Grid  import re  -from tic_tac_toe.logic.models import Grid   def validate_grid(grid: Grid) -> None:      if not re.match(r"^[\sXO]{9}$", grid.cells):          raise ValueError("Must contain 9 cells of: X, O, or space")`

You import `Grid` conditionally. The `TYPE_CHECKING` constant is false at [runtime](https://en.wikipedia.org/wiki/Runtime_(program_lifecycle_phase)), but third-party tools, such as [mypy](https://github.com/python/mypy), will pretend it’s true when performing static type checking to allow the import statement to run. However, because you no longer import the required type at runtime, you must now use forward declarations or take advantage of `from __future__ import annotations`, which will implicitly turn annotations into string literals.

**Note:** The `__future__` import was originally intended to make the migration from Python 2 to Python 3 more seamless. Today, you can use it to enable various language features planned for future releases. Once a feature becomes part of the standard Python distribution and you don’t need to support older language versions, you can remove that import.

With all this plumbing in place, you’re finally ready to constrain the game state to comply with the tic-tac-toe rules. Next up, you’ll add a few `GameState` validation functions to your new `validators` module.

[Remove ads](https://realpython.com/account/join/)

### Discard Incorrect Game States[](https://realpython.com/tic-tac-toe-ai-python/#discard-incorrect-game-states "Permanent link")

In order to reject invalid game states, you’ll implement a familiar post-initialization hook in your `GameState` class that delegates the processing to another function:

`# tic_tac_toe/logic/models.py  import enum import re from dataclasses import dataclass from functools import cached_property  from tic_tac_toe.logic.validators import validate_game_state, validate_grid # ...  @dataclass(frozen=True) class GameState:     grid: Grid     starting_mark: Mark = Mark("X")      def __post_init__(self) -> None:        validate_game_state(self)     # ...`

The validating function, `validate_game_state()`, receives an instance of the game state, which in turn contains the grid of cells and the starting player. You’re going to use this information, but first, you’ll split the validation into a few smaller and more focused stages by delegating bits of the state further down in your `validators` module:

`# tic_tac_toe/logic/validators.py  from __future__ import annotations  from typing import TYPE_CHECKING  if TYPE_CHECKING:     from tic_tac_toe.logic.models import GameState, Grid import re  def validate_grid(grid: Grid) -> None:     ...  def validate_game_state(game_state: GameState) -> None:     validate_number_of_marks(game_state.grid)    validate_starting_mark(game_state.grid, game_state.starting_mark)    validate_winner(        game_state.grid, game_state.starting_mark, game_state.winner    )`

Your new helper function serves as an entry point to the game state validation by calling a few subsequent functions that you’ll define in just a bit.

To prevent instantiating a game state with an incorrect **number of a player’s marks** in the grid, such as the one you stumbled on before, you must take the proportion of naughts to crosses into account:

`# tic_tac_toe/logic/validators.py  from __future__ import annotations  from typing import TYPE_CHECKING  if TYPE_CHECKING:     from tic_tac_toe.logic.models import GameState, Grid  import re  from tic_tac_toe.logic.exceptions import InvalidGameState def validate_grid(grid: Grid) -> None:     ...  def validate_game_state(game_state: GameState) -> None:     ...  def validate_number_of_marks(grid: Grid) -> None:     if abs(grid.x_count - grid.o_count) > 1:        raise InvalidGameState("Wrong number of Xs and Os")`

At any time, the number of marks left by one player must be either the same or greater by exactly one compared to the number of marks left by the other player. Initially, there are no marks, so the number of Xs and Os is equal to zero. When the first player makes a move, they’ll have one more mark than their opponent. But, as soon as the other player makes their first move, the proportion evens out again, and so on.

To signal an invalid state, you raise a custom exception defined in another module:

`# tic_tac_toe/logic/exceptions.py  class InvalidGameState(Exception):     """Raised when the game state is invalid."""`

It’s customary to have empty classes extend the built-in `Exception` type in Python without specifying any methods or attributes in them. Such classes exist solely for their names, which convey enough information about the error that occurred at runtime. Notice that you don’t need to use the [`pass` statement](https://realpython.com/python-pass/) or the [ellipsis literal (`...`)](https://realpython.com/python-ellipsis/) as a class body placeholder if you use a [docstring](https://realpython.com/documenting-python-code/), which can provide additional documentation.

Another game state inconsistency related to the number of marks left on the grid has to do with the **starting player’s mark**, which may be wrong:

`# tic_tac_toe/logic/validators.py  from __future__ import annotations  from typing import TYPE_CHECKING  if TYPE_CHECKING:     from tic_tac_toe.logic.models import GameState, Grid  import re  from tic_tac_toe.logic.exceptions import InvalidGameState  def validate_grid(grid: Grid) -> None:     ...  def validate_game_state(game_state: GameState) -> None:     ...  def validate_number_of_marks(grid: Grid) -> None:     ...  def validate_starting_mark(grid: Grid, starting_mark: Mark) -> None:     if grid.x_count > grid.o_count:        if starting_mark != "X":            raise InvalidGameState("Wrong starting mark")    elif grid.o_count > grid.x_count:        if starting_mark != "O":            raise InvalidGameState("Wrong starting mark")`

The player who left more marks on the grid is guaranteed to be the starting player. If not, then you know that something must have gone wrong. Because you defined `Mark` as an enum derived from `str`, you can directly compare the starting player’s mark to a string literal.

Finally, there can only be one **winner**, and depending on who started the game, the ratio of Xs ans Os left on the grid will be different:

`# tic_tac_toe/logic/validators.py  from __future__ import annotations  from typing import TYPE_CHECKING  if TYPE_CHECKING:     from tic_tac_toe.logic.models import GameState, Grid, Mark import re  from tic_tac_toe.logic.exceptions import InvalidGameState  def validate_grid(grid: Grid) -> None:     ...  def validate_game_state(game_state: GameState) -> None:     ...  def validate_number_of_marks(grid: Grid) -> None:     ...  def validate_starting_mark(grid: Grid, starting_mark: Mark) -> None:     ...  def validate_winner(     grid: Grid, starting_mark: Mark, winner: Mark | None ) -> None:     if winner == "X":        if starting_mark == "X":            if grid.x_count <= grid.o_count:                raise InvalidGameState("Wrong number of Xs")        else:            if grid.x_count != grid.o_count:                raise InvalidGameState("Wrong number of Xs")    elif winner == "O":        if starting_mark == "O":            if grid.o_count <= grid.x_count:                raise InvalidGameState("Wrong number of Os")        else:            if grid.o_count != grid.x_count:                raise InvalidGameState("Wrong number of Os")`

A starting player has an advantage, so when they win, they’ll have left more marks than their opponent. Conversely, the second player is at a disadvantage, so they can only win the game by making an equal number of moves as the starting player.

You’re almost done with encapsulating the tic-tac-toe game’s rules in Python code, but there’s still one more important piece missing. In the next section, you’ll write code to systematically produce new game states by simulating players’ moves.

### Simulate Moves by Producing New Game States[](https://realpython.com/tic-tac-toe-ai-python/#simulate-moves-by-producing-new-game-states "Permanent link")

The last property that you’ll add to your `GameState` class is a fixed list of possible moves, which you can find by filling the remaining empty cells in the grid with the current player’s mark:

`# tic_tac_toe/logic/models.py  # ...  @dataclass(frozen=True) class GameState:     # ...      @cached_property    def possible_moves(self) -> list[Move]:        moves = []        if not self.game_over:            for match in re.finditer(r"\s", self.grid.cells):                moves.append(self.make_move_to(match.start()))        return moves`

If the game’s over, then you return an empty list of moves. Otherwise, you identify the locations of empty cells using a regular expression, and then make a move to each of those cells. Making a move creates a new `Move` object, which you append to the list without mutating the game state.

This is how you construct a `Move` object:

`# tic_tac_toe/logic/models.py  import enum import re from dataclasses import dataclass from functools import cached_property  from tic_tac_toe.logic.exceptions import InvalidMove from tic_tac_toe.logic.validators import validate_game_state, validate_grid  # ...  @dataclass(frozen=True) class GameState:     # ...      def make_move_to(self, index: int) -> Move:        if self.grid.cells[index] != " ":            raise InvalidMove("Cell is not empty")        return Move(            mark=self.current_mark,            cell_index=index,            before_state=self,            after_state=GameState(                Grid(                    self.grid.cells[:index]                    + self.current_mark                    + self.grid.cells[index + 1:]                ),                self.starting_mark,            ),        )`

A move isn’t allowed if the target cell is already occupied by either your or your opponent’s mark, in which case you raise an `InvalidMove` exception. On the other hand, if the cell is empty, then you take a snapshot of the current player’s mark, the target cell’s index, and the current game state while synthesizing the following state.

Don’t forget to define the new exception type that you imported:

`# tic_tac_toe/logic/exceptions.py  class InvalidGameState(Exception):     """Raised when the game state is invalid."""  class InvalidMove(Exception):     """Raised when the move is invalid."""`

That’s it! You’ve just gotten yourself a pretty solid **domain model** of the tic-tac-toe game, which you can use to build interactive games for various front ends. The model encapsulates the game’s rules and enforces its constraints.

In the next section, you’ll build an abstract **game engine** and your first **artificial player**.

[Remove ads](https://realpython.com/account/join/)

## Step 2: Scaffold a Generic Tic-Tac-Toe Game Engine[](https://realpython.com/tic-tac-toe-ai-python/#step-2-scaffold-a-generic-tic-tac-toe-game-engine "Permanent link")

At this point, you should have all the domain models defined for your tic-tac-toe library. Now, it’s time to build a **game engine** that’ll take advantage of these model classes to facilitate tic-tac-toe gameplay.

Go ahead and create three more Python modules inside the `tic_tac_toe.game` package now:

`tic-tac-toe/ │ └── library/     │     ├── src/     │   │     │   └── tic_tac_toe/     │       │     │       ├── game/     │       │   ├── __init__.py     │       │   ├── engine.py    │       │   ├── players.py    │       │   └── renderers.py    │       │     │       ├── logic/     │       │   ├── __init__.py     │       │   ├── exceptions.py     │       │   ├── models.py     │       │   └── validators.py     │       │     │       └── __init__.py     │     └── pyproject.toml`

The `engine` module is the centerpiece of the virtual gameplay, where you’ll implement the game’s main loop. You’ll define abstract interfaces that the game engine uses, along with a sample computer player, in the `players` and `renderers` modules. By the end of this step, you’ll be set to write a tangible front end for the tic-tac-toe library.

### Pull the Players’ Moves to Drive the Game[](https://realpython.com/tic-tac-toe-ai-python/#pull-the-players-moves-to-drive-the-game "Permanent link")

At the very minimum, to play a tic-tac-toe game, you need to have two players, something to draw on, and a set of rules to follow. Fortunately, you can express these elements as immutable data classes, which take advantage of the existing domain model from your library. First, you’ll create the `TicTacToe` class in the `engine` module:

`# tic_tac_toe/game/engine.py  from dataclasses import dataclass  from tic_tac_toe.game.players import Player from tic_tac_toe.game.renderers import Renderer  @dataclass(frozen=True) class TicTacToe:     player1: Player     player2: Player     renderer: Renderer`

Both `Player` and `Renderer` will be implemented in the following sections as Python’s [abstract base classes](https://docs.python.org/3/library/abc.html), which only describe the high-level interface for your game engine. However, they’ll eventually get replaced with concrete classes, some of which may come from an externally defined front end. The player will know what move to make, and the renderer will be responsible for visualizing the grid.

To play the game, you must decide which player should make the **first move**, or you can assume the default one, which is the player with crosses. You should also begin with a **blank grid** of cells and an **initial game state**:

`# tic_tac_toe/game/engine.py  from dataclasses import dataclass  from tic_tac_toe.game.players import Player from tic_tac_toe.game.renderers import Renderer from tic_tac_toe.logic.exceptions import InvalidMove from tic_tac_toe.logic.models import GameState, Grid, Mark @dataclass(frozen=True) class TicTacToe:     player1: Player     player2: Player     renderer: Renderer      def play(self, starting_mark: Mark = Mark("X")) -> None:        game_state = GameState(Grid(), starting_mark)        while True:            self.renderer.render(game_state)            if game_state.game_over:                break            player = self.get_current_player(game_state)            try:                game_state = player.make_move(game_state)            except InvalidMove:                pass`

The engine requests that the renderer update the view and then uses a **pull strategy** to advance the game by asking both players to make their moves in alternating rounds. These steps are repeated in an [infinite loop](https://en.wikipedia.org/wiki/Infinite_loop) until the game is over.

`GameState` only knows about the current player’s mark, which can be either X or O, but it doesn’t know about the specific player objects that were assigned those marks. Therefore, you need to map the current mark to a player object using this helper method:

`# tic_tac_toe/game/engine.py  from dataclasses import dataclass  from tic_tac_toe.game.players import Player from tic_tac_toe.game.renderers import Renderer from tic_tac_toe.logic.exceptions import InvalidMove from tic_tac_toe.logic.models import GameState, Grid, Mark  @dataclass(frozen=True) class TicTacToe:     player1: Player     player2: Player     renderer: Renderer      def play(self, starting_mark: Mark = Mark("X")) -> None:         game_state = GameState(Grid(), starting_mark)         while True:             self.renderer.render(game_state)             if game_state.game_over:                 break             player = self.get_current_player(game_state)             try:                 game_state = player.make_move(game_state)             except InvalidMove:                 pass      def get_current_player(self, game_state: GameState) -> Player:        if game_state.current_mark is self.player1.mark:            return self.player1        else:            return self.player2`

Here, you compare enum members by their identities using Python’s `is` operator. If the current player’s mark determined by the game state is the same as the mark assigned to the first player, then that’s the player who should be making the next move.

Both players supplied to the `TicTacToe` object should have opposite marks. Otherwise, you wouldn’t be able to play the game without violating its rules. So, it’s reasonable to validate the players’ marks when instantiating the `TicTacToe` class:

`# tic_tac_toe/game/engine.py  from dataclasses import dataclass  from tic_tac_toe.game.players import Player from tic_tac_toe.game.renderers import Renderer from tic_tac_toe.logic.exceptions import InvalidMove from tic_tac_toe.logic.models import GameState, Grid, Mark from tic_tac_toe.logic.validators import validate_players @dataclass(frozen=True) class TicTacToe:     player1: Player     player2: Player     renderer: Renderer      def __post_init__(self):        validate_players(self.player1, self.player2)     def play(self, starting_mark: Mark = Mark("X")) -> None:         game_state = GameState(Grid(), starting_mark)         while True:             self.renderer.render(game_state)             if game_state.game_over:                 break             player = self.get_current_player(game_state)             try:                 game_state = player.make_move(game_state)             except InvalidMove:                 pass      def get_current_player(self, game_state: GameState) -> Player:         if game_state.current_mark is self.player1.mark:             return self.player1         else:             return self.player2`

You add a post-initialization hook to your data class and call another validation function that you have to add in your `validators` module:

`# tic_tac_toe/logic/validators.py  from __future__ import annotations  from typing import TYPE_CHECKING  if TYPE_CHECKING:     from tic_tac_toe.game.players import Player    from tic_tac_toe.logic.models import GameState, Grid, Mark  import re  from tic_tac_toe.logic.exceptions import InvalidGameState  def validate_grid(grid: Grid) -> None:     ...  def validate_game_state(game_state: GameState) -> None:     ...  def validate_number_of_marks(grid: Grid) -> None:     ...  def validate_starting_mark(grid: Grid, starting_mark: Mark) -> None:     ...  def validate_winner(     grid: Grid, starting_mark: Mark, winner: Mark | None ) -> None:     ...  def validate_players(player1: Player, player2: Player) -> None:     if player1.mark is player2.mark:        raise ValueError("Players must use different marks")`

You use the identity comparison again to check both players’ marks and prevent the game from starting when both players use the same mark.

There’s one more thing that can go wrong. Because it’s up to the players, including human players, to decide what move they make, their choice could be invalid. Currently, your `TicTacToe` class catches the `InvalidMove` exception but doesn’t do anything useful with it other than ignore such a move and ask the player to make a different choice. It would probably help to let the front end handle errors by, for example, showing a suitable message:

`# tic_tac_toe/game/engine.py  from dataclasses import dataclass from typing import Callable, TypeAlias from tic_tac_toe.game.players import Player from tic_tac_toe.game.renderers import Renderer from tic_tac_toe.logic.exceptions import InvalidMove from tic_tac_toe.logic.models import GameState, Grid, Mark from tic_tac_toe.logic.validators import validate_players  ErrorHandler: TypeAlias = Callable[[Exception], None] @dataclass(frozen=True) class TicTacToe:     player1: Player     player2: Player     renderer: Renderer     error_handler: ErrorHandler | None = None     def __post_init__(self):         validate_players(self.player1, self.player2)      def play(self, starting_mark: Mark = Mark("X")) -> None:         game_state = GameState(Grid(), starting_mark)         while True:             self.renderer.render(game_state)             if game_state.game_over:                 break             player = self.get_current_player(game_state)             try:                 game_state = player.make_move(game_state)             except InvalidMove as ex:                if self.error_handler:                    self.error_handler(ex)     def get_current_player(self, game_state: GameState) -> Player:         if game_state.current_mark is self.player1.mark:             return self.player1         else:             return self.player2`

To let the front end decide how to take care of an invalid move, you expose a hook in your class by introducing an optional `.error_handler` [callback](https://en.wikipedia.org/wiki/Callback_(computer_programming)), which will receive the exception. You define the callback’s type using a [type alias](https://realpython.com/python310-new-features/#type-unions-aliases-and-guards), making its type declaration more concise. The `TicTacToe` game will trigger this callback in case of an invalid move, as long as you provide the error handler.

Having implemented an abstract tic-tac-toe game engine, you can proceed to code an artificial player. You’ll define a generic player interface and implement it with a sample computer player that makes moves at random.

[Remove ads](https://realpython.com/account/join/)

### Let the Computer Pick a Random Move[](https://realpython.com/tic-tac-toe-ai-python/#let-the-computer-pick-a-random-move "Permanent link")

First, define an abstract `Player`, which will be the base class for concrete players to extend:

`# tic_tac_toe/game/players.py  import abc  from tic_tac_toe.logic.models import Mark  class Player(metaclass=abc.ABCMeta):     def __init__(self, mark: Mark) -> None:         self.mark = mark`

An **abstract class** is one that you can’t instantiate because its objects wouldn’t stand on their own. Its only purpose is to provide the skeleton for concrete subclasses. You can mark a class as abstract in Python by setting its [metaclass](https://realpython.com/python-metaclasses/) to `abc.ABCMeta` or extending the `abc.ABC` ancestor.

**Note:** Using the `metaclass` argument instead of extending the base class is slightly more flexible, as it doesn’t affect your [inheritance](https://realpython.com/inheritance-composition-python/) hierarchy. This is less important in languages like Python, which support multiple inheritance. Anyway, as a rule of thumb, you should favor [composition over inheritance](https://en.wikipedia.org/wiki/Composition_over_inheritance) whenever possible.

The player gets assigned a `Mark` instance that they’ll be using during the game. The player also exposes a public method to make a move, given a certain game state:

`# tic_tac_toe/game/players.py  import abc  from tic_tac_toe.logic.exceptions import InvalidMove from tic_tac_toe.logic.models import GameState, Mark, Move class Player(metaclass=abc.ABCMeta):     def __init__(self, mark: Mark) -> None:         self.mark = mark      def make_move(self, game_state: GameState) -> GameState:        if self.mark is game_state.current_mark:            if move := self.get_move(game_state):                return move.after_state            raise InvalidMove("No more possible moves")        else:            raise InvalidMove("It's the other player's turn")     @abc.abstractmethod    def get_move(self, game_state: GameState) -> Move | None:        """Return the current player's move in the given game state."""`

Notice how the public `.make_move()` method defines a universal algorithm for making a move, but the individual step of getting the move is delegated to an abstract method, which you must implement in concrete subclasses. Such a design is known as the [template method pattern](https://en.wikipedia.org/wiki/Template_method_pattern) in object-oriented programming.

Making a move entails checking if it’s the given player’s turn and whether the move exists. The `.get_move()` method returns `None` to indicate that no more moves are possible, and the abstract `Player` class uses the [Walrus operator (`:=`)](https://realpython.com/python-walrus-operator/) to simplify the calling code.

To make the game feel more natural, you can introduce a short delay for the **computer player** to wait before choosing their move. Otherwise, the computer would make its moves instantly, unlike a human player. You can define another, slightly more specific abstract base class to represent computer players:

`# tic_tac_toe/game/players.py  import abc import time from tic_tac_toe.logic.exceptions import InvalidMove from tic_tac_toe.logic.models import GameState, Mark, Move  class Player(metaclass=abc.ABCMeta):     ...  class ComputerPlayer(Player, metaclass=abc.ABCMeta):     def __init__(self, mark: Mark, delay_seconds: float = 0.25) -> None:        super().__init__(mark)        self.delay_seconds = delay_seconds     def get_move(self, game_state: GameState) -> Move | None:        time.sleep(self.delay_seconds)        return self.get_computer_move(game_state)     @abc.abstractmethod    def get_computer_move(self, game_state: GameState) -> Move | None:        """Return the computer's move in the given game state."""`

`ComputerPlayer` extends `Player` by adding an additional member, `.delay_seconds`, to its instances, which by default is equal to 250 milliseconds. It also implements the `.get_move()` method to simulate a certain wait time, and then calls another abstract method specific to computer players.

Having an abstract computer player data type enforces a uniform interface, which you can conveniently satisfy with a few lines of code. For example, you can implement a computer player picking moves at random in the following way:

`# tic_tac_toe/game/players.py  import abc import random import time  from tic_tac_toe.logic.exceptions import InvalidMove from tic_tac_toe.logic.models import GameState, Mark, Move  class Player(metaclass=abc.ABCMeta):     ...  class ComputerPlayer(Player, metaclass=abc.ABCMeta):     ...  class RandomComputerPlayer(ComputerPlayer):     def get_computer_move(self, game_state: GameState) -> Move | None:        try:            return random.choice(game_state.possible_moves)        except IndexError:            return None`

You use `choice()` to pick a random element from a list of possible moves. If there are no more moves in the given game state, then you’ll get an `IndexError` because of an empty list, so you catch it and return `None` instead.

You now have two abstract base classes, `Player` and `ComputerPlayer`, as well as one concrete `RandomComputerPlayer`, which you’ll be able to use in your games. The only remaining element of the equation before you can put those classes into action is the abstract renderer, which you’ll define next.

### Make an Abstract Tic-Tac-Toe Grid Renderer[](https://realpython.com/tic-tac-toe-ai-python/#make-an-abstract-tic-tac-toe-grid-renderer "Permanent link")

Giving the tic-tac-toe grid a visual form is entirely up to the front end, so you’ll only define an abstract interface in your library:

`# tic_tac_toe/game/renderers.py  import abc  from tic_tac_toe.logic.models import GameState  class Renderer(metaclass=abc.ABCMeta):     @abc.abstractmethod     def render(self, game_state: GameState) -> None:         """Render the current game state."""`

This could’ve been implemented as a regular function because the renderer exposes only a single operation while getting the whole state through an argument. However, concrete subclasses may need to maintain an additional state, such as the application’s window, so having a class may come in handy at some point.

Okay, you have the tic-tac-toe library with a robust domain model, an engine encapsulating the game rules, a mechanism to simulate moves, and even a concrete computer player. In the next section, you’ll combine all the pieces together and build a game front end, letting you finally see some action!

[Remove ads](https://realpython.com/account/join/)

## Step 3: Build a Game Front End for the Console[](https://realpython.com/tic-tac-toe-ai-python/#step-3-build-a-game-front-end-for-the-console "Permanent link")

So far, you’ve been working on an abstract tic-tac-toe game engine library, which provides the building blocks for the game. In this section, you’ll bring it to life by coding a separate project that relies on this library. It’s going to be a bare-bones game running in the text-based console.

### Render the Grid With ANSI Escape Codes[](https://realpython.com/tic-tac-toe-ai-python/#render-the-grid-with-ansi-escape-codes "Permanent link")

The most important aspect of any game front end is providing visual feedback to the players through a **graphical interface**. Because you’re constrained to the text-based console in this example, you’ll take advantage of [ANSI escape codes](https://en.wikipedia.org/wiki/ANSI_escape_code) to control things like text formatting or placement.

Create the `renderers` module in your console front end and define a concrete class that extends the tic-tac-toe’s abstract renderer in it:

`# frontends/console/renderers.py  from tic_tac_toe.game.renderers import Renderer from tic_tac_toe.logic.models import GameState  class ConsoleRenderer(Renderer):     def render(self, game_state: GameState) -> None:         clear_screen()`

In case you’re using [Visual Studio Code](https://realpython.com/advanced-visual-studio-code-python/), and it doesn’t resolve the imports, try closing and reopening the editor. The `ConsoleRenderer` class overrides `.render()`, the only abstract method responsible for visualizing the game’s current state. In this case, you start by clearing the screen’s content using a helper function, which you can define below the class:

`# frontends/console/renderers.py  from tic_tac_toe.game.renderers import Renderer from tic_tac_toe.logic.models import GameState  class ConsoleRenderer(Renderer):     def render(self, game_state: GameState) -> None:         clear_screen()  def clear_screen() -> None:     print("\033c", end="")`

The string literal `"\033"` represents a non-printable Esc character, which starts a special **code sequence**. The letter `c` that follows encodes the command to clear the screen. Note that the [`print()`](https://realpython.com/python-print/) function automatically ends the text with a newline character. To avoid adding an unnecessary blank line, you must disable this by setting the `end` argument.

When there’s a winner, you’ll want to distinguish their winning marks with **blinking text**. You can define another helper function to encode blinking text using the relevant ANSI escape code:

`# frontends/console/renderers.py  from tic_tac_toe.game.renderers import Renderer from tic_tac_toe.logic.models import GameState  class ConsoleRenderer(Renderer):     def render(self, game_state: GameState) -> None:         clear_screen()  def clear_screen() -> None:     print("\033c", end="")  def blink(text: str) -> str:     return f"\033[5m{text}\033[0m"`

Here, you wrap the supplied text with opening and closing ANSI escape codes in [Python’s f-string](https://realpython.com/python-f-strings/).

To render the tic-tac-toe grid filled with players’ marks, you’ll format a multiline template string and use the [`textwrap`](https://docs.python.org/3/library/textwrap.html#module-textwrap) module to remove the indentation:

`# frontends/console/renderers.py  import textwrap from typing import Iterable from tic_tac_toe.game.renderers import Renderer from tic_tac_toe.logic.models import GameState  class ConsoleRenderer(Renderer):     def render(self, game_state: GameState) -> None:         clear_screen()         print_solid(game_state.grid.cells) def clear_screen() -> None:     print("\033c", end="")  def blink(text: str) -> str:     return f"\033[5m{text}\033[0m"  def print_solid(cells: Iterable[str]) -> None:     print(        textwrap.dedent(            """\             A   B   C           ------------        1 ┆  {0} │ {1} │ {2}          ┆ ───┼───┼───        2 ┆  {3} │ {4} │ {5}          ┆ ───┼───┼───        3 ┆  {6} │ {7} │ {8}    """        ).format(*cells)    )`

The `print_solid()` function takes a sequence of cells and prints them with an additional gutter around the top-left corner. It contains numbered rows and columns indexed by letters. For example, a partially filled tic-tac-toe grid may look like this on the screen:

     `A   B   C    ------------ 1 ┆  X │ O │ X   ┆ ───┼───┼─── 2 ┆  O │ O │   ┆ ───┼───┼─── 3 ┆    │ X │`

The gutter will make it easier for the player to specify the coordinates of the target cell where they want to put their mark.

If there’s a **winner**, you’ll want to blink some of their cells and print a message stating who won the game. Otherwise, you’ll print a solid grid of cells and optionally inform the players that there are no winners in case of a **tie**:

`# frontends/console/renderers.py  import textwrap from typing import Iterable  from tic_tac_toe.game.renderers import Renderer from tic_tac_toe.logic.models import GameState  class ConsoleRenderer(Renderer):     def render(self, game_state: GameState) -> None:         clear_screen()         if game_state.winner:            print_blinking(game_state.grid.cells, game_state.winning_cells)            print(f"{game_state.winner} wins \N{party popper}")        else:            print_solid(game_state.grid.cells)            if game_state.tie:                print("No one wins this time \N{neutral face}") def clear_screen() -> None:     print("\033c", end="")  def blink(text: str) -> str:     return f"\033[5m{text}\033[0m"  def print_solid(cells: Iterable[str]) -> None:     print(         textwrap.dedent(             """\              A   B   C            ------------         1 ┆  {0} │ {1} │ {2}           ┆ ───┼───┼───         2 ┆  {3} │ {4} │ {5}           ┆ ───┼───┼───         3 ┆  {6} │ {7} │ {8}     """         ).format(*cells)     )`

Your messages contain special syntax for [name aliases](https://www.unicode.org/Public/11.0.0/ucd/NameAliases.txt) of Unicode characters, including [emojis](https://en.wikipedia.org/wiki/Emoji), in order to make the output look more colorful and exciting. For example, `"\N{party popper}"` will render the 🎉 emoji. Note that you call yet another helper function, `print_blinking()`, which you must define now:

`# frontends/console/renderers.py  import textwrap from typing import Iterable  from tic_tac_toe.game.renderers import Renderer from tic_tac_toe.logic.models import GameState  class ConsoleRenderer(Renderer):     def render(self, game_state: GameState) -> None:         clear_screen()         if game_state.winner:             print_blinking(game_state.grid.cells, game_state.winning_cells)             print(f"{game_state.winner} wins \N{party popper}")         else:             print_solid(game_state.grid.cells)             if game_state.tie:                 print("No one wins this time \N{neutral face}")  def clear_screen() -> None:     print("\033c", end="")  def blink(text: str) -> str:     return f"\033[5m{text}\033[0m"  def print_blinking(cells: Iterable[str], positions: Iterable[int]) -> None:     mutable_cells = list(cells)    for position in positions:        mutable_cells[position] = blink(mutable_cells[position])    print_solid(mutable_cells) def print_solid(cells: Iterable[str]) -> None:     print(         textwrap.dedent(             """\              A   B   C            ------------         1 ┆  {0} │ {1} │ {2}           ┆ ───┼───┼───         2 ┆  {3} │ {4} │ {5}           ┆ ───┼───┼───         3 ┆  {6} │ {7} │ {8}     """         ).format(*cells)     )`

This new function takes the sequence of cells and the numeric positions of those which should be rendered using blinking text. Then, it makes a mutable copy of the cells, overwrites the specified cells with blinking ANSI escape codes, and delegates the rendering to `print_solid()`.

At this point, you can test your custom renderer using two computer players built into the tic-tac-toe library. Save the following code in a file named `play.py` located in the `frontends/` folder:

`# frontends/play.py  from tic_tac_toe.game.engine import TicTacToe from tic_tac_toe.game.players import RandomComputerPlayer from tic_tac_toe.logic.models import Mark  from console.renderers import ConsoleRenderer  player1 = RandomComputerPlayer(Mark("X")) player2 = RandomComputerPlayer(Mark("O"))  TicTacToe(player1, player2, ConsoleRenderer()).play()`

When you [run this script](https://realpython.com/run-python-scripts/), you’ll see two artificial players making random moves, leading to different outcomes each time:

Random Moves of Two Computer Players

While it’s interesting to look at their gameplay, there’s no interactivity whatsoever. You’re going to change that now by letting human players decide what moves to make.

[Remove ads](https://realpython.com/account/join/)

### Create an Interactive Console Player[](https://realpython.com/tic-tac-toe-ai-python/#create-an-interactive-console-player "Permanent link")

At the end of this section, you’ll be able to play a tic-tac-toe match between a human and a computer player or two **human players**, in addition to the two **computer players** you just saw. A human player will use the keyboard interface to specify their moves.

You can define a new concrete player class in your console front end, which will implement the abstract `.get_move()` method specified in the library. Create the front end’s `players` module and fill it with the following content:

`# frontends/console/players.py  from tic_tac_toe.game.players import Player from tic_tac_toe.logic.exceptions import InvalidMove from tic_tac_toe.logic.models import GameState, Move  class ConsolePlayer(Player):     def get_move(self, game_state: GameState) -> Move | None:         while not game_state.game_over:             try:                 index = grid_to_index(input(f"{self.mark}'s move: ").strip())             except ValueError:                 print("Please provide coordinates in the form of A1 or 1A")             else:                 try:                     return game_state.make_move_to(index)                 except InvalidMove:                     print("That cell is already occupied.")         return None`

If the game has finished, then you return `None` to indicate that no moves were possible. Otherwise, you keep asking the player for a valid move until they provide one and make that move. Because the human player types cell coordinates like `A1` or `C3`, you must convert such text to a numeric index with the help of the `grid_to_index()` function:

`# frontends/console/players.py  import re from tic_tac_toe.game.players import Player from tic_tac_toe.logic.exceptions import InvalidMove from tic_tac_toe.logic.models import GameState, Move  class ConsolePlayer(Player):     def get_move(self, game_state: GameState) -> Move | None:         while not game_state.game_over:             try:                 index = grid_to_index(input(f"{self.mark}'s move: ").strip())             except ValueError:                 print("Please provide coordinates in the form of A1 or 1A")             else:                 try:                     return game_state.make_move_to(index)                 except InvalidMove:                     print("That cell is already occupied.")         return None  def grid_to_index(grid: str) -> int:     if re.match(r"[abcABC][123]", grid):        col, row = grid    elif re.match(r"[123][abcABC]", grid):        row, col = grid    else:        raise ValueError("Invalid grid coordinates")    return 3 * (int(row) - 1) + (ord(col.upper()) - ord("A"))`

The function uses regular expressions to extract the numeric row and column so that you can calculate the corresponding index in the flat sequence of cells.

You can now modify your test script by importing and instantiating `ConsolePlayer`:

`# frontends/play.py  from tic_tac_toe.game.engine import TicTacToe from tic_tac_toe.game.players import RandomComputerPlayer from tic_tac_toe.logic.models import Mark  from console.players import ConsolePlayer from console.renderers import ConsoleRenderer  player1 = ConsolePlayer(Mark("X")) player2 = RandomComputerPlayer(Mark("O"))  TicTacToe(player1, player2, ConsoleRenderer()).play()`

Running this script will allow you to play as X against the computer. Unfortunately, there’s no convenient way of changing the players or stating who should start the game, because this information is baked into the code. Next up, you’ll add a command-line interface to fix that.

### Add a Command-Line Interface (CLI)[](https://realpython.com/tic-tac-toe-ai-python/#add-a-command-line-interface-cli "Permanent link")

You’re almost done building your tic-tac-toe front end. However, it’s time to add the finishing touches and turn it into a playable game by implementing a useful [command-line interface](https://en.wikipedia.org/wiki/Command-line_interface) using the [`argparse`](https://realpython.com/command-line-interfaces-python-argparse/) module. That way, you’ll be able to choose the player types and the starting mark before running the game.

The entry point to your console front end is the special `__main__.py` module, which makes the containing package runnable through the `python` command. Because it’s [customary](https://docs.python.org/3/library/__main__.html#id1) to put minimal **wrapper code** in it, you’ll keep the module lightweight by delegating the processing to a function imported from another module:

`# frontends/console/__main__.py  from .cli import main  main()`

This makes the code that’s defined in `cli.py` more reusable across many places and easier to test in isolation. Here’s how that code might look:

`# frontends/console/cli.py  from tic_tac_toe.game.engine import TicTacToe  from .args import parse_args from .renderers import ConsoleRenderer  def main() -> None:     player1, player2, starting_mark = parse_args()     TicTacToe(player1, player2, ConsoleRenderer()).play(starting_mark)`

You import the game engine, your new console renderer, and a helper function, `parse_argse()`, which will be able to read command-line arguments and, based on them, return two player objects and the starting player’s mark.

To implement the parsing of arguments, you can start by defining the available player types as a [Python dictionary](https://realpython.com/python-dicts/), which associates everyday names like _human_ with concrete classes extending the abstract `Player`:

`# frontends/console/args.py  from tic_tac_toe.game.players import RandomComputerPlayer  from .players import ConsolePlayer  PLAYER_CLASSES = {     "human": ConsolePlayer,     "random": RandomComputerPlayer, }`

This will make it more straightforward to add more player types in the future. Next, you can write a function that’ll use the `argparse` module to get the expected arguments from the command line:

`# frontends/console/args.py  import argparse from tic_tac_toe.game.players import Player, RandomComputerPlayer from tic_tac_toe.logic.models import Mark from .players import ConsolePlayer  PLAYER_CLASSES = {     "human": ConsolePlayer,     "random": RandomComputerPlayer, }  def parse_args() -> tuple[Player, Player, Mark]:     parser = argparse.ArgumentParser()    parser.add_argument(        "-X",        dest="player_x",        choices=PLAYER_CLASSES.keys(),        default="human",    )    parser.add_argument(        "-O",        dest="player_o",        choices=PLAYER_CLASSES.keys(),        default="random",    )    parser.add_argument(        "--starting",        dest="starting_mark",        choices=Mark,        type=Mark,        default="X",    )    args = parser.parse_args()`

The code above translates to the following three optional arguments, all of which have default values:

|Argument|Default Value|Description|
|---|---|---|
|`-X`|`human`|Assigns X to the specified player|
|`-O`|`random`|Assigns O to the specified player|
|`--starting`|`X`|Determines the starting player’s mark|

At this point, the function parses those arguments and stores their values as strings in a special [NameSpace](https://docs.python.org/3/library/argparse.html#argparse.Namespace) object under the attributes named `.player_x`, `.player_o`, and `.starting_mark`, respectively. However, the function is expected to return a tuple consisting of custom data types instead of strings. To make the function’s body comply with its signature, you can map strings provided by the user to the respective classes using your dictionary:

`# frontends/console/args.py  import argparse  from tic_tac_toe.game.players import Player, RandomComputerPlayer from tic_tac_toe.logic.models import Mark  from .players import ConsolePlayer  PLAYER_CLASSES = {     "human": ConsolePlayer,     "random": RandomComputerPlayer, }  def parse_args() -> tuple[Player, Player, Mark]:     parser = argparse.ArgumentParser()     parser.add_argument(         "-X",         dest="player_x",         choices=PLAYER_CLASSES.keys(),         default="human",     )     parser.add_argument(         "-O",         dest="player_o",         choices=PLAYER_CLASSES.keys(),         default="random",     )     parser.add_argument(         "--starting",         dest="starting_mark",         choices=Mark,         type=Mark,         default="X",     )     args = parser.parse_args()      player1 = PLAYER_CLASSES[args.player_x](Mark("X"))    player2 = PLAYER_CLASSES[args.player_o](Mark("O"))     if args.starting_mark == "O":        player1, player2 = player2, player1     return player1, player2, args.starting_mark`

You translate the user-supplied names to concrete player classes. If the starting player’s mark is different from the default one, then you swap the two players before returning them from the function.

To make the code slightly cleaner and more expressive, you may replace the generic tuple with a typed [named tuple](https://realpython.com/python-namedtuple/):

`# frontends/console/args.py  import argparse from typing import NamedTuple from tic_tac_toe.game.players import Player, RandomComputerPlayer from tic_tac_toe.logic.models import Mark  from .players import ConsolePlayer  PLAYER_CLASSES = {     "human": ConsolePlayer,     "random": RandomComputerPlayer, }  class Args(NamedTuple):     player1: Player    player2: Player    starting_mark: Mark def parse_args() -> Args:     parser = argparse.ArgumentParser()     parser.add_argument(         "-X",         dest="player_x",         choices=PLAYER_CLASSES.keys(),         default="human",     )     parser.add_argument(         "-O",         dest="player_o",         choices=PLAYER_CLASSES.keys(),         default="random",     )     parser.add_argument(         "--starting",         dest="starting_mark",         choices=Mark,         type=Mark,         default="X",     )     args = parser.parse_args()      player1 = PLAYER_CLASSES[args.player_x](Mark("X"))     player2 = PLAYER_CLASSES[args.player_o](Mark("O"))      if args.starting_mark == "O":         player1, player2 = player2, player1      return Args(player1, player2, args.starting_mark)`

First, you define a `typing.NamedTuple` subclass comprising precisely three named and typed elements. You then return an instance of your named tuple instead of a generic tuple. Doing so gives you additional type safety and access to the tuple’s elements by name as well as by index.

To play against another human, you can run your console front end with these arguments:

`(venv) $ cd frontends/ (venv) $ python -m console -X human -O human`

If you’d like to try your chances against the computer, then replace the value of either the `-X` or `-O` option with _random_, which is currently the only computer player type available. Unfortunately, it isn’t particularly challenging to play against a player making moves at random. In the next step, you’ll implement a more advanced computer player leveraging the **minimax algorithm**, which makes the computer practically undefeatable.

## Step 4: Equip the Computer With Artificial Intelligence[](https://realpython.com/tic-tac-toe-ai-python/#step-4-equip-the-computer-with-artificial-intelligence "Permanent link")

You’ve reached the final step in this tutorial, which involves creating another computer player, this one equipped with basic artificial intelligence. Specifically, it’ll use the [minimax algorithm](https://en.wikipedia.org/wiki/Minimax) under the surface to make the most optimal move in every possible situation in any turn-based [zero-sum game](https://en.wikipedia.org/wiki/Zero-sum_game) like tic-tac-toe.

**Note:** Mastering the details of the minimax algorithm isn’t your focus in this tutorial. But, if you’d like to learn more about it, then check out [Minimax in Python: Learn How to Lose the Game of Nim](https://realpython.com/python-minimax-nim/), which uses a more straightforward game of [Nim](https://en.wikipedia.org/wiki/Nim) as an example.

Before implementing the algorithm, you have to invent a way of assessing the game’s score, which will become the deciding factor behind choosing the best move. You’ll do that by introducing an absolute scale of numeric values indicating how well both players are doing.

### Evaluate the Score of a Finished Game[](https://realpython.com/tic-tac-toe-ai-python/#evaluate-the-score-of-a-finished-game "Permanent link")

For simplicity, you’ll consider **static evaluation** of a finished game. There are three possible outcomes of the game, which you can assign arbitrary numeric values, for example:

1. **Player loses:** `-1`
2. **Player ties:** `0`
3. **Player wins:** `1`

The protagonist player whose score you’ll evaluate is known as the **maximizing player** because they try to maximize the game’s overall score. Therefore, greater values should correspond to better outcomes, as viewed from their perspective. The **minimizing player**, on the other hand, is their opponent, who tries to lower the score as much as possible. After all, they win when your player loses, while a tie can be equally good or bad for both players.

Once you determine the maximizing and minimizing players, the scale remains absolute, meaning you don’t need to flip the sign when evaluating your opponent’s moves.

You can express this numeric scale in Python code by adding the following method to your `GameState` model in the tic-tac-toe library:

`# tic_tac_toe/logic/models.py  import enum import re from dataclasses import dataclass from functools import cached_property  from tic_tac_toe.logic.exceptions import InvalidMove, UnknownGameScore from tic_tac_toe.logic.validators import validate_game_state, validate_grid  # ...  @dataclass(frozen=True) class GameState:     # ...      def make_move_to(self, index: int) -> Move:         ...      def evaluate_score(self, mark: Mark) -> int:        if self.game_over:            if self.tie:                return 0            if self.winner is mark:                return 1            else:                return -1        raise UnknownGameScore("Game is not over yet")`

Because this is a static evaluation, you can only determine the score when the game is over. Otherwise, you raise an `UnknownGameScore` exception, which you must add to the `exceptions` module in the library:

`# tic_tac_toe/logic/exceptions.py  class InvalidGameState(Exception):     """Raised when the game state is invalid."""  class InvalidMove(Exception):     """Raised when the move is invalid."""  class UnknownGameScore(Exception):     """Raised when the game score is unknown."""`

Knowing the score of a finished game isn’t that helpful when you want to make an informed decision about choosing a move up front. However, it’s the first step toward finding the best possible sequence of moves leading up to winning—or tying the game, in the worst-case scenario. Next, you’ll use the minimax algorithm to calculate the score in any game state.

### Propagate the Score With the Minimax Algorithm[](https://realpython.com/tic-tac-toe-ai-python/#propagate-the-score-with-the-minimax-algorithm "Permanent link")

When you have several moves to choose from, you want to pick one that’ll increase your expected score. At the same time, you want to avoid moves that could potentially shift the game’s score in favor of your opponent. The minimax algorithm can help with that by using the [`min()` and `max()`](https://realpython.com/python-min-and-max/) functions to minimize your opponent’s maximum gain while maximizing your minimum payoff.

If that sounds complicated, then have a look at a graphical visualization of tic-tac-toe gameplay below.

When you imagine all possible game states as a [game tree](https://en.wikipedia.org/wiki/Game_tree), choosing the best move boils down to searching for the most optimal path in such a [weighted graph](https://en.wikipedia.org/wiki/Glossary_of_graph_theory#weighted_graph), starting from the current node. The minimax algorithm propagates the scores evaluated statically for the [leaf nodes](https://en.wikipedia.org/wiki/Glossary_of_graph_theory#leaf), which correspond to finished games, by bubbling them up in the game tree. Either the minimum or the maximum score gets propagated at each step, depending on whose turn it is.

You can visualize this process using a concrete example of the final three turns in a game of tic-tac-toe. Below, you’ll find a small segment of the tic-tac-toe game tree illustrating the possible moves of the maximizing player X, whose turns are depicted in green:

[![Tic-Tac-Toe Game Tree With Propagated Scores](https://files.realpython.com/media/game_tree.eb1646a73d08.png)](https://files.realpython.com/media/game_tree.eb1646a73d08.png)

Tic-Tac-Toe Game Tree With Propagated Scores

The minimax algorithm starts by recursively exploring the tree to look ahead and find all the possible game outcomes. Once those are found, it computes their scores and backtracks to the starting node. If it’s the maximizing player’s turn that leads to the next position, then the algorithm picks the maximum score at that level. Otherwise, it picks the minimum score, assuming the opponent will never make mistakes.

In the game tree above, the leftmost branch results in an immediate win for the maximizing player, so the connecting edge has the highest weight. Choosing the middle branch could also lead to a victory, but the minimax algorithm _pessimistically_ indicates the worst-case scenario, which is a tie. Finally, the branch on the right almost certainly represents a losing move.

Create a new `minimax` module in the tic-tac-toe library and implement the algorithm using the following sleek Python expression:

`# tic_tac_toe/logic/minimax.py  from tic_tac_toe.logic.models import Mark, Move  def minimax(     move: Move, maximizer: Mark, choose_highest_score: bool = False ) -> int:     if move.after_state.game_over:         return move.after_state.evaluate_score(maximizer)     return (max if choose_highest_score else min)(         minimax(next_move, maximizer, not choose_highest_score)         for next_move in move.after_state.possible_moves     )`

The `minimax()` function returns the score associated with the move passed as an argument for the indicated maximizing player. If the game has finished, then you calculate the score by performing the static evaluation of the grid. Otherwise, you choose either the maximum or the minimum score, which you find with recursion for all the possible moves at the current position.

**Note:** The placement of the `minimax` module in your project’s directory tree is somewhat subjective because it would work equally well when defined elsewhere. However, one could argue that it logically belongs to the game’s logic layer since it only depends on the domain model.

As long as you made an editable install of the tic-tac-toe library in your virtual environment, you’ll be able to test your new function in an interactive Python interpreter session:

`>>> from tic_tac_toe.logic.minimax import minimax >>> from tic_tac_toe.logic.models import GameState, Grid, Mark  >>> def preview(cells): ...     print(cells[:3], cells[3:6], cells[6:], sep="\n")  >>> game_state = GameState(Grid("XXO O X O"), starting_mark=Mark("X")) >>> for move in game_state.possible_moves: ...     print("Score:", minimax(move, maximizer=Mark("X"))) ...     preview(move.after_state.grid.cells) ...     print("-" * 10)  Score: 1 XXO XO X O ---------- Score: 0 XXO  OX X O ---------- Score: -1 XXO  O XXO ----------`

The computed scores correspond to the edge weights in the game tree that you saw before. Finding the best move is only a matter of choosing the one with the highest resulting score. Note that there can sometimes be multiple alternative paths to a winning outcome in the game tree.

In the next section, you’ll create another concrete computer player, which will leverage the minimax algorithm, and then you’ll use it in your console front end.

### Make an Undefeatable Minimax Computer Player[](https://realpython.com/tic-tac-toe-ai-python/#make-an-undefeatable-minimax-computer-player "Permanent link")

The minimax algorithm calculates the score associated with a particular move. To find the best move in a given game state, you can sort all possible moves by score and take the one with the highest value. By doing that, you’ll use AI to create an unbeatable tic-tac-toe player with Python.

Go ahead and define the following function in your tic-tac-toe library’s `minimax` module:

`# tic_tac_toe/logic/minimax.py  from functools import partial from tic_tac_toe.logic.models import GameState, Mark, Move def find_best_move(game_state: GameState) -> Move | None:     maximizer: Mark = game_state.current_mark    bound_minimax = partial(minimax, maximizer=maximizer)    return max(game_state.possible_moves, key=bound_minimax) def minimax(     move: Move, maximizer: Mark, choose_highest_score: bool = False ) -> int:     ...`

The `find_best_move()` function takes some game state and returns either the best move for the **current player** or `None` to indicate that no more moves are possible. Note the use of a [partial function](https://en.wikipedia.org/wiki/Partial_application) to freeze the value of the `maximizer` argument, which doesn’t change across `minimax()` invocations. This lets you use the `bound_minimax()` function, which expects exactly one argument, as the ordering key.

**Note:** Python’s `functools.partial()` is a factory that produces a new function with fewer parameters by prepopulating one or more of the original function’s arguments with concrete values. Unlike manually defining such a [wrapper function](https://en.wikipedia.org/wiki/Wrapper_function) when writing code, the factory can do this dynamically at runtime and offers much more concise syntax.

Next, add a new computer player in the tic-tac-toe library’s `players` module. This player will use the `find_best_move()` helper function that you’ve just created:

`# tic_tac_toe/game/players.py  import abc import random import time  from tic_tac_toe.logic.exceptions import InvalidMove from tic_tac_toe.logic.minimax import find_best_move from tic_tac_toe.logic.models import GameState, Mark, Move  class Player(metaclass=abc.ABCMeta):     ...  class ComputerPlayer(Player, metaclass=abc.ABCMeta):     ...  class RandomComputerPlayer(ComputerPlayer):     def get_computer_move(self, game_state: GameState) -> Move | None:         try:             return random.choice(game_state.possible_moves)         except IndexError:             return None  class MinimaxComputerPlayer(ComputerPlayer):     def get_computer_move(self, game_state: GameState) -> Move | None:        return find_best_move(game_state)`

This computer player will always try to find the best tic-tac-toe move with AI and Python. However, to make the game less predictable and reduce the amount of computation, you can let it pick the first move randomly before running the expensive minimax algorithm. You’ve already implemented the logic for [choosing a random move](https://realpython.com/tic-tac-toe-ai-python/#let-the-computer-pick-a-random-move) in `RandomComputerPlayer`, defined above. Now, it would help to extract that common logic into a reusable component.

Go ahead and modify the code of both the random and minimax computer players:

 `# tic_tac_toe/game/players.py   import abc -import random  import time   from tic_tac_toe.logic.exceptions import InvalidMove  from tic_tac_toe.logic.minimax import find_best_move  from tic_tac_toe.logic.models import GameState, Mark, Move   class Player(metaclass=abc.ABCMeta):      ...   class ComputerPlayer(Player, metaclass=abc.ABCMeta):      ...   class RandomComputerPlayer(ComputerPlayer):      def get_computer_move(self, game_state: GameState) -> Move | None: -        try: -            return random.choice(game_state.possible_moves) -        except IndexError: -            return None +        return game_state.make_random_move()  class MinimaxComputerPlayer(ComputerPlayer):      def get_computer_move(self, game_state: GameState) -> Move | None: -        return find_best_move(game_state) +        if game_state.game_not_started: +            return game_state.make_random_move() +        else: +            return find_best_move(game_state)`

You call the `.make_random_move()` method on the game state in both classes. You need to define this new method to choose one of the possible moves using Python’s [`random`](https://realpython.com/python-random/) module:

`# tic_tac_toe/logic/models.py  import enum import random import re from dataclasses import dataclass from functools import cached_property  from tic_tac_toe.logic.exceptions import InvalidMove from tic_tac_toe.logic.validators import validate_game_state, validate_grid  # ...  @dataclass(frozen=True) class GameState:     # ...      @cached_property     def possible_moves(self) -> list[Move]:         ...      def make_random_move(self) -> Move | None:        try:            return random.choice(self.possible_moves)        except IndexError:            return None     def make_move_to(self, index: int) -> Move:         ...      def evaluate_score(self, mark: Mark) -> int:         ...`

The final step is to use the new computer player in your front end. Open the `args` module in the console front end project, and import `MinimaxComputerPlayer`:

`# frontends/console/args.py  import argparse from typing import NamedTuple  from tic_tac_toe.game.players import (     Player,    RandomComputerPlayer,    MinimaxComputerPlayer, ) from tic_tac_toe.logic.models import Mark  from .players import ConsolePlayer  PLAYER_CLASSES = {     "human": ConsolePlayer,     "random": RandomComputerPlayer,     "minimax": MinimaxComputerPlayer, }  class Args(NamedTuple):     player1: Player     player2: Player     starting_mark: Mark  def parse_args() -> Args:     parser = argparse.ArgumentParser()     parser.add_argument(         "-X",         dest="player_x",         choices=PLAYER_CLASSES.keys(),         default="human",     )     parser.add_argument(         "-O",         dest="player_o",         choices=PLAYER_CLASSES.keys(),         default="minimax",    )      # ...`

You add the new player type to the mapping of names and use the minimax computer player as the default opponent of the human player.

Okay, you have three kinds of players to choose from now. You can take your console front end for the ultimate test drive by selecting different players to try their chances against each other. For example, you can pick two minimax computer players:

`(venv) $ cd frontends/ (venv) $ python -m console -X minimax -O minimax`

In this case, you should expect the game to _always_ end in a tie since both players use the optimal strategy.

One thing you may notice when requesting at least one minimax player is rather poor performance, especially at the beginning of the game. That’s because building the entire game tree, even for a game as relatively basic as tic-tac-toe, is very costly. You’ll explore a few performance optimization possibilities in the [Next Steps](https://realpython.com/tic-tac-toe-ai-python/#next-steps).

Congratulations! You’ve reached the end of this long journey. Don’t forget about the supporting materials, which contain additional code that wasn’t covered in the tutorial. The materials include two other front ends and some performance tricks, which make the minimax player make their moves instantly. You can download this code by clicking the link below:

**Source Code:** [Click here to download the free source code](https://realpython.com/bonus/tic-tac-toe-ai-python-code/) that you’ll use to build a tic-tac-toe game engine and AI player with Python.

## Conclusion[](https://realpython.com/tic-tac-toe-ai-python/#conclusion "Permanent link")

You did a fantastic job completing this detailed step-by-step tutorial! You’ve built a front-end-agnostic **tic-tac-toe library** with the game’s core logic and two artificial **computer players**, including an unbeatable one leveraging the **minimax algorithm**. You also created a sample **front end** that renders the game in the text-based console and takes input from a **human player**.

Along the way, you followed **good programming practices**, including **object-oriented** design with elements of the **functional paradigm**, and took advantage of the latest enhancements in the Python language.

**In this tutorial, you’ve learned how to:**

- Create a reusable **Python library** with the tic-tac-toe game engine
- Model the **domain** of tic-tac-toe following Pythonic code style
- Implement artificial players, including one based on the **minimax algorithm**
- Build a text-based **console front end** for the game with a human player
- Explore strategies for **performance optimizations**

If you haven’t already done so, click the link below to download the complete source and some bonus code for the project that you’ve been building in this tutorial:

**Source Code:** [Click here to download the free source code](https://realpython.com/bonus/tic-tac-toe-ai-python-code/) that you’ll use to build a tic-tac-toe game engine and AI player with Python.

## Next Steps[](https://realpython.com/tic-tac-toe-ai-python/#next-steps "Permanent link")

Having a generic Python **tic-tac-toe library** with the game’s core logic and AI lets you focus on building alternative **front ends** that can leverage different graphical interfaces. You’ve built a text-based console front end for tic-tac-toe in this tutorial, while the supporting materials contain examples of other presentation layers. Maybe you’ll want to make one for [Jupyter Notebook](https://realpython.com/jupyter-notebook-introduction/) or a mobile phone using [Kivy](https://realpython.com/mobile-app-kivy-python/) or another Python framework.

An important area for improvement is the performance bottleneck stemming from the [brute-force](https://en.wikipedia.org/wiki/Brute-force_search) nature of the **minimax algorithm**, which checks all possible game states. There are several ways in which you can cut down the number of computations and speed up the process:

- **A heuristic:** Instead of exploring the entire depth of the tree, you can stop at a designated level and estimate a rough score with a [heuristic](https://en.wikipedia.org/wiki/Heuristic). It’s worth noting that this may sometimes give suboptimal results.
- **Caching:** You can precompute the entire game tree up front, which would be a one-time effort requiring a lot of resources. Later, you’d be able to load the [lookup table (LUT)](https://en.wikipedia.org/wiki/Lookup_table) into the memory and get the score instantly for every possible game state.
- **Alpha-beta pruning:** It’s possible to dismiss a significant portion of the nodes in the game tree as bad choices when exploring it with the minimax algorithm. You can employ a slight modification to the minimax algorithm, known as the [alpha-beta pruning](https://realpython.com/python-minimax-nim/#optimize-minimax-with-alpha-beta-pruning) technique. In short, it keeps track of the better options already available without entering branches guaranteed to offer worse choices.

Do you have other ideas for using or extending the tic-tac-toe library? Share them in the comments below!

🐍 Python Tricks 💌

Get a short & sweet **Python Trick** delivered to your inbox every couple of days. No spam ever. Unsubscribe any time. Curated by the Real Python team.

![Python Tricks Dictionary Merge](https://realpython.com/static/pytrick-dict-merge.4201a0125a5e.png)

About **Bartosz Zaczyński**

[](https://realpython.com/team/bzaczynski/)[![Bartosz Zaczyński](https://robocrop.realpython.net/?url=https%3A//files.realpython.com/media/coders_lab_2109368.259b1599fbee.jpg&w=1694&h=1694&mode=crop&sig=de07b3f1b4a9c51d44ecaca8faf56c6211353f86)](https://realpython.com/team/bzaczynski/)

Bartosz is a bootcamp instructor, author, and polyglot programmer in love with Python. He helps his students get into software engineering by sharing over a decade of commercial experience in the IT industry.

[» More about Bartosz](https://realpython.com/team/bzaczynski/)

---

_Each tutorial at Real Python is created by a team of developers so that it meets our high quality standards. The team members who worked on this tutorial are:_

[![Aldren Santos](https://robocrop.realpython.net/?url=https%3A//files.realpython.com/media/PP.9b8b026f75b8.jpg&w=959&h=959&mode=crop&sig=70bedc2eab90a227eb9a657c415689c3eb1eca4f)](https://realpython.com/team/asantos/)

[

Aldren

](https://realpython.com/team/asantos/)

[![Geir Arne Hjelle](https://robocrop.realpython.net/?url=https%3A//files.realpython.com/media/gahjelle.470149ee709e.jpg&w=800&h=800&mode=crop&sig=e9b761c6cf1359953014dba05554f5424eb116e1)](https://realpython.com/team/gahjelle/)

[

Geir Arne

](https://realpython.com/team/gahjelle/)

[![Ian Currie](https://robocrop.realpython.net/?url=https%3A//files.realpython.com/media/5sK42VEQ_-_Copy_-_Copy.b8a1a4a9ca1f.jpeg&w=480&h=480&mode=crop&sig=79a608b4af0343081a2e28f28509c74db868ac56)](https://realpython.com/team/icurrie/)

[

Ian

](https://realpython.com/team/icurrie/)

[![Kate Finegan](https://robocrop.realpython.net/?url=https%3A//files.realpython.com/media/VZxEtUor_400x400.7169c68e3950.jpg&w=400&h=400&mode=crop&sig=dfa9b806107d5d44e9a4750b9618a2614153164b)](https://realpython.com/team/kfinegan/)

[

Kate

](https://realpython.com/team/kfinegan/)

Master Real-World Python Skills  
With Unlimited Access to Real Python

![](https://realpython.com/static/videos/lesson-locked.f5105cfd26db.svg)

**Join us and get access to thousands of tutorials, hands-on video courses, and a community of expert Pythonistas:**

What Do You Think?

**Rate this article:**

[Tweet](https://twitter.com/intent/tweet/?text=Check out this %23Python tutorial: Build%20a%20Tic-Tac-Toe%20Game%20Engine%20With%20an%20AI%20Player%20in%20Python by @realpython&url=https%3A//realpython.com/tic-tac-toe-ai-python/) [Share](https://facebook.com/sharer/sharer.php?u=https%3A//realpython.com/tic-tac-toe-ai-python/) [Share](https://www.linkedin.com/sharing/share-offsite/?url=https%3A//realpython.com/tic-tac-toe-ai-python/) [Email](mailto:?subject=Python article for you&body=Check out this Python tutorial:%0A%0ABuild%20a%20Tic-Tac-Toe%20Game%20Engine%20With%20an%20AI%20Player%20in%20Python%0A%0Ahttps%3A//realpython.com/tic-tac-toe-ai-python/)

What’s your #1 takeaway or favorite thing you learned? How are you going to put your newfound skills to use? Leave a comment below and let us know.

**Commenting Tips:** The most useful comments are those written with the goal of learning from or helping out other students. [Get tips for asking good questions](https://realpython.com/python-beginner-tips/#tip-9-ask-good-questions) and [get answers to common questions in our support portal](https://support.realpython.com).

---

Looking for a real-time conversation? Visit the [Real Python Community Chat](https://realpython.com/community/) or join the next [“Office Hours” Live Q&A Session](https://realpython.com/office-hours/). Happy Pythoning!

Keep Learning

Related Tutorial Categories: [advanced](https://realpython.com/tutorials/advanced/) [best-practices](https://realpython.com/tutorials/best-practices/) [gamedev](https://realpython.com/tutorials/gamedev/) [gui](https://realpython.com/tutorials/gui/) [projects](https://realpython.com/tutorials/projects/) [python](https://realpython.com/tutorials/python/)

[Remove ads](https://realpython.com/account/join/)

© 2012–2023 Real Python ⋅ [Newsletter](https://realpython.com/newsletter/) ⋅ [Podcast](https://realpython.com/podcasts/rpp/) ⋅ [YouTube](https://www.youtube.com/realpython) ⋅ [Twitter](https://twitter.com/realpython) ⋅ [Facebook](https://facebook.com/LearnRealPython) ⋅ [Instagram](https://www.instagram.com/realpython/) ⋅ [Python Tutorials](https://realpython.com/) ⋅ [Search](https://realpython.com/search) ⋅ [Privacy Policy](https://realpython.com/privacy-policy/) ⋅ [Energy Policy](https://realpython.com/energy-policy/) ⋅ [Advertise](https://realpython.com/sponsorships/) ⋅ [Contact](https://realpython.com/contact/)  
❤️ Happy Pythoning!