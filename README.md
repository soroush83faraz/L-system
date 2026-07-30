# L-system

**Interactive demo:** https://soroush83faraz.github.io/L-system/

L-systems (Lindenmayer systems) are string-rewriting grammars: starting from an
axiom, rewrite rules are applied over and over, and the resulting string is drawn
by a turtle that reads each symbol as a command (draw, turn, branch). A handful
of rules is enough to generate all of the fractals below.

## The fractals

Each Python script draws one classic fractal. The scripts implement them
directly (recursion or a chaos game); the table shows the equivalent L-system
grammar for each — the same grammars power the
[interactive explorer](https://soroush83faraz.github.io/L-system/).

| Script | Fractal | Axiom | Rules | Angle | Python technique |
|---|---|---|---|---|---|
| `DragonCurve.py` | Dragon curve | `FX` | `X → X+YF+` · `Y → -FX-Y` | 90° | recursive turtle (depth 10) |
| `koch_curve.py` | Koch snowflake | `F--F--F` | `F → F+F--F+F` | 60° | recursive turtle (depth 4, 3 edges) |
| `FractalTree.py` | Fractal tree | `X` | `X → F[-X][+X]` | 20° | recursive turtle, shrinking branches |
| `FractalPlant.py` | Fractal plant / Barnsley fern | `X` | `X → F+[[X]-X]-F[-FX]+X` · `F → FF` | 25° | chaos-game IFS (100,000 points) |
| `SierpinskiTriagle.py` | Sierpinski triangle | `F-G-G` | `F → F-G+F+G-F` · `G → GG` | 120° | recursive midpoint subdivision |
| `Sprinski2.py` | Sierpinski triangle (arrowhead variant) | `A` | `A → B-A-B` · `B → A+B+A` | 60° | chaos game (10,000 points) |

In the grammar column `F G A B` draw a line, `+`/`-` turn left/right by the
angle, and `[`/`]` push/pop the turtle state (branching).

## Running the Python scripts

Every script uses the standard-library `turtle` module, except
`FractalPlant.py`, which uses matplotlib:

```sh
pip install matplotlib   # only needed for FractalPlant.py
python DragonCurve.py    # or any other script
```

## Interactive explorer

[`docs/index.html`](docs/index.html) is a single self-contained page (no
dependencies, works offline) with the six presets above, an iteration slider,
angle and line-width controls, a progressive draw animation, and auto-fit
canvas rendering. It is served with GitHub Pages:
https://soroush83faraz.github.io/L-system/

## Credits

Group project — built together with
[Saeed Geshani](https://github.com/SaeedGeshani); pair-programmed, commits
don't reflect individual contributions. Original repo:
https://github.com/SaeedGeshani/L-system. The interactive web demo was added
in this fork of the project.
