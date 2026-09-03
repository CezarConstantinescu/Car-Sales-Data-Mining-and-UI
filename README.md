# Car Sales Data Mining and UI

A Data Mining Windows desktop application made using C# for exploring a car sales data mining model. The project contains a custom-made desktop UI and data mining modules for visualizing results.

## Short summary

-	The app connects to Microsoft Analysis Services via AdomdConnection and discovers deployed mining models (querying `$system.DMSCHEMA_MINING_MODELS`).
-	It inspects model contents by querying `SELECT FLATTENED NODE_NAME, NODE_CAPTION, NODE_SUPPORT, NODE_TYPE FROM [<ModelName>].CONTENT` to read mining nodes and their metrics.
-	It filters nodes (the code ignores nodes with `NODE_TYPE >= 100` and supports user filtering by NodeType) and exposes node details in a dataGridView.
-	It visualizes node metrics (`NODE_SUPPORT`) — MainForm.cs uses a column chart; MainForm.cs uses a pie chart — to compare/support analysis results.
-	The UI is a custom desktop viewer for exploring model outputs (example model name: Predict Owner); actual preprocessing and mining (clustering, classification, association, etc.) have been run inside Analysis Services models, which this project queries and visualizes.

## Tools and Technologies
- `Microsoft Analysis Services` and `AdomdClient` for querying mining models
- `C#` and `.NET` (desktop application)
- Custom-made UI implemented in the `UI\UI` project (WinForms/WPF desktop interface)
- Data mining and viewer components in `DM\DMViewer` and `DM\AlternateDMViewer`

Note: The UI is custom-built for this project (not generated from templates) and focuses on interactive, user-driven exploration of datasets and mining results.

## Features

- Connect to Microsoft Analysis Services mining models using `AdomdClient` (`AdomdConnection`) and discover deployed models.
- Inspect model contents by querying model `CONTENT` (reads `NODE_NAME`, `NODE_CAPTION`, `NODE_SUPPORT`, `NODE_TYPE`).
- Filter and browse mining nodes (the apps ignore `NODE_TYPE >= 100` and provide user filtering by node type).
- Visualize node metrics (`NODE_SUPPORT`) with built-in charts:
  - `DM\DMViewer\MainForm.cs` — column chart for support values
  - `DM\AlternateDMViewer\MainForm.cs` — pie chart alternative
- Present node details in a `DataGridView` for quick inspection and selection.
- Custom-made desktop UI (hand-crafted WinForms/WPF) focused on interactive, user-driven exploration of deployed mining models — the project is an inspection and visualization tool; preprocessing and training of mining models occur within Analysis Services.
- Attempts to select a sensible default model (example: `Predict Owner`) when available and lets the user switch between available models in the catalog.

## Structure

- `UI\UI` — custom user interface project (desktop)
- `DM\DMViewer` — primary data-mining viewer based on clusters
- `DM\AlternateDMViewer` — alternate pie chart viewer implementation

## Quickstart

1. Clone repository.
2. Open `Car Sales Data Mining and UI.sln` in Visual Studio.
3. Restore NuGet packages and build the solution.
4. Set `UI` as the startup project and run. Use the UI to load datasets and run analyses.
