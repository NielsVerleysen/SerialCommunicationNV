# Copilot instructions for SerialCommunicationNV

## Build / Run / Test / Lint
- Build in Visual Studio (recommended): open SerialCommunication.slnx and build (Debug/Release).
- CLI build (msbuild):
  - msbuild SerialCommunication.slnx /p:Configuration=Debug
  - msbuild SerialCommunication.slnx /p:Configuration=Release
- Run (Debug): use Visual Studio F5 or run the exe at SerialCommunication\bin\Debug\SerialCommunication.exe
- Tests: none exist in this repo.
- Linting: no lint/formatter configured in repo.

## High-level architecture
- Single Visual Studio WinForms application in project `SerialCommunication`.
- Entry point: Program.Main -> Application.Run(new Form1()).
- UI: Form1 (partial class split across Form1.cs and Form1.Designer.cs) drives the app.
- Serial I/O: uses System.IO.Ports.SerialPort (see Form1.cs). The app enumerates COM ports and exposes baud selection.
- Project targets .NET Framework 4.7.2 (see SerialCommunication.csproj). Resources (images, settings) live under Properties and Resources/.

## Key repository conventions & notes for Copilot
- Work on the C# source files (Form1.cs, Program.cs, Properties/*). Compiled binaries and obj/bin folders are present in the repo but should not be edited.
- UI code follows Windows Forms partial-class pattern: keep UI designer changes in Designer.cs and resource (.resx) edits via the designer when possible.
- App settings are defined in Properties/Settings.settings. Use ConfigurationManager or Properties.Settings.Default to access them.
- Target framework is .NET Framework 4.7.2; prefer Visual Studio/msbuild for builds. `dotnet` CLI may not behave consistently for legacy csproj formats.

## AI assistant / other tooling files to watch for
- No README, CONTRIBUTING, or AI-assistant config files were detected. If adding Copilot/Claude/Cursor config, place it at repo root or under .github so future sessions can discover it.

## Quick pointers for edits
- For serial-related changes, search Form1.cs for `SerialPort` usages and combo box setup for ports/baudrates.
- When adding tests, create a separate test project (e.g., MSTest/NUnit) targeting .NET Framework 4.7.2 and run via Test Explorer or `vstest.console.exe`.

---
(Generated from inspection of: SerialCommunication\SerialCommunication.csproj, Program.cs, Form1.cs)
