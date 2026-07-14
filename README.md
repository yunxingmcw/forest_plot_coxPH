# forest_plot_coxPH
Simple example showing how to create a forest plot from Cox PH hazard-ratio results.

This repository includes a working notebook (`forestplot_hazardRatio.ipynb`) and sample data (`fplot_sample_data.xlsx`) demonstrating the `forestplot` package.
The original package is at https://github.com/LSYS/forestplot (examples).

**What's included**
- `forestplot_hazardRatio.ipynb` — runnable notebook that builds and saves the forest plot.
- `fplot_sample_data.xlsx` — synthetic example data used by the notebook.
- `requirements.txt` — Python packages used to run the notebook.
- `fonts/` — local font files copied into the repository (DejaVu, Noto placeholders, etc.).

**Quick start**
1. Create and activate a virtual environment (recommended):
	```bash
	python -m venv .venv
	source .venv/bin/activate
	```
2. Install dependencies:
	```bash
	pip install -r requirements.txt
	```
3. Open and run the notebook `forestplot_hazardRatio.ipynb` in Jupyter or VS Code.

**Changing the display font**
- The notebook registers any `.ttf` files placed in the `fonts/` folder and exposes a `chosen_font` variable in the plotting cell. Edit `chosen_font` (e.g. `"Noto Sans"`, `"Liberation Sans"`) and re-run the cell to render the plot with that font.
- If you want system fonts instead, install them on your machine (or copy the TTF into `fonts/`) and re-run the registration cell.

**Preserving table alignment**
- The notebook uses a monospace font for numeric/CI annotation cells so their column alignment remains unchanged when you swap the display font for labels. By default the monospace font is `fonts/DejaVuSansMono.ttf`. To change it, edit the `mono_fp` filename in the plotting cell.

**Saving plots**
- `fp.forestplot(...)` returns a Matplotlib `Axes` object. Save images with the underlying `Figure`:
  ```python
  fig = ax.get_figure()
  fig.savefig('myplot.png', bbox_inches='tight')
  ```

**Fonts and licensing**
- The repo includes open-source fonts (DejaVu, Noto placeholders). If you want Microsoft fonts (Arial/Times New Roman), install them on your system or copy licensed TTFs into `fonts/`.

** Issues with the original forestplot package
1. p-values astericks - default threshold was 0.1, 0.05, and 0.01; changed to 0.05, 0.01 and 0.001;
2. annotation issues - duplicates in 'label' will result in the annotation table header to fail; avoid duplicates in 'label'

