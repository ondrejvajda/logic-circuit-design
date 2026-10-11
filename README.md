# logic-circuit-design

Interactive web tools for learning digital logic design. They were made for the course *Základy digitálních systémů* and follow the notation used in its lectures.

The project covers the typical workflow: describe a function in a **truth table**, simplify it with a **Karnaugh map**, then build it from **NAND and NOT gates** as a schematic and on a model of a real breadboard. A landing page (`index.html`) lets you pick the tool you want.

There is nothing to install or build. Everything is plain HTML, CSS and JavaScript that runs in the browser.

> The interface is in Czech.

## Table of contents

- [Tools](#tools)
- [Getting started](#getting-started)
- [Project structure](#project-structure)
- [Contributing](#contributing)
- [Contributors](#contributors)
- [License](#license)
- [Acknowledgments](#acknowledgments)

## Tools

### Pravdivostní tabulka (Truth table)

An editable truth table for 2 to 5 input variables and up to 6 output functions.

- Click a cell to cycle its value between `0`, `1` and `X` (don't-care).
- Rename inputs and outputs, and optionally show the column weights.
- Each function is also written in index notation, as a list of row numbers where it equals 1 (and where it is `X`).
- **Hotová** mode shows the finished table. **Cvičit** mode lets you fill in the table yourself, then use *Zkontrolovat* to check it or *Ukázat řešení* to reveal the answer.
- *Načíst ukázku* loads an example, *Vymazat hodnoty* clears the table, and *Vyfotit tabulku* exports it as a PNG.

### Karnaughovy mapy (Karnaugh maps)

Karnaugh maps for 2 to 5 variables, one map per function.

- The maps use the lecture notation. Bars on the edges mark where a variable is 1, and each cell shows its index.
- Click a cell to cycle `0`, `1` and `X`.
- Mark groups (loops) of cells, which are colour-coded and listed with the term each one gives. Invalid groups are flagged.
- Build the resulting expression and check it against the map.
- The *Zákony* panel lists the Boolean algebra laws and supports step-by-step algebraic simplification.
- *Vyfotit mapy* exports the maps as a PNG.

### Logické obvody (Logic circuits)

Build a 4-variable function (`x3 x2 x1 x0`) using only NAND and NOT gates.

- **Function strip:** pick a function and see its 16-cell truth table. Click a cell to set the inputs to that combination. After a check, each cell shows ✓ or ✗. An optional estimate shows the minimum form.
- **Schéma:** a canvas where you add NAND and NOT gates, drag them around and wire them by clicking an output and then an input. Live values on the wires are optional. *Zkontrolovat všech 16 kombinací* tests the circuit against the function.
- **Deska:** the same circuit wired on a model of the real board with one 7404 (6× NOT), two 7400 (8× NAND with 2 inputs in total), two 7420 (4× NAND with 4 inputs in total) and one 7430 (NAND with 8 inputs). *Zapojit napájení* connects the power supply to the modules in use.
- A usage panel counts the gates against what the chips provide.

## Getting started

### Requirements

A modern web browser. The only external resource is the IBM Plex font from Google Fonts. Without a connection the pages still work and fall back to system fonts.

### Run locally

```bash
git clone https://github.com/ondrejvajda/logic-circuit-design.git
cd logic-circuit-design
```

Then open `index.html` in your browser (double-click it, or drag it into a browser window) and choose a tool.

If you prefer to serve the files over HTTP, any static server works, for example:

```bash
python -m http.server 8000
```

and then visit `http://localhost:8000`.

## Project structure

```
logic-circuit-design/
├── index.html                  # Landing page: choose which tool to open
├── pravdivostni-tabulka.html   # Truth table editor and practice mode
├── karnaughovy-mapy.html       # Karnaugh maps and simplification
├── logicke-obvody.html         # NAND/NOT schematic and breadboard
└── README.md
```

`index.html` links to the three tools. The tools are independent of each other: each is a single self-contained page with its own markup, styles and script. They share the same look (the light or dark theme follows your system setting) and the same notation, where input `x0` is the lowest bit and rows and cells are numbered from 0.

## Contributing

Contributions, bug reports and ideas are welcome.

1. **Report a problem or suggest a feature** by opening an [issue](https://github.com/ondrejvajda/logic-circuit-design/issues). For bugs, say which tool you were using and what you did, and include a screenshot if you can.
2. **Fork** the repository and create a branch for your change (`git checkout -b my-change`).
3. **Make your change** and test it by opening the affected page in a browser, including the light and dark themes and a narrow (phone-width) window.
4. **Open a pull request** against `main` with a short description of what changed and why.

Please keep to the project's conventions: no build step and no dependencies to install, each tool stays a self-contained page, and the interface stays in Czech with the lecture notation.

By contributing, you agree that your contributions will be licensed under the [MIT License](#license).

## Contributors

- [@ondrejvajda](https://github.com/ondrejvajda): author and maintainer
- [@jakubkubza](https://github.com/jakubkubza): contributor

Want to see your name here? See [Contributing](#contributing).

## License

This project is licensed under the [MIT License](LICENSE). You are free to use, copy, modify and distribute it, as long as the copyright and license notice are kept.

## Acknowledgments

- The notation and exercises follow the course *Základy digitálních systémů*.
- Fonts: [IBM Plex](https://www.ibm.com/plex/) via Google Fonts.
- Developed with the help of [Claude](https://claude.ai) by Anthropic.
