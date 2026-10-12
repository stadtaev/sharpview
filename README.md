# Sharpview

C# analysis solution targeting .NET 10.

- `src/Sharpview.Core`: Roslyn-independent semantic facts and call-chain queries.
- `src/Sharpview.Roslyn`: project loading and semantic extraction; references Core.
- `src/Sharpview.Cli`: console harness; references Core and Roslyn.

## Build and run

```sh
dotnet build sharpview.slnx
dotnet run --project src/Sharpview.Cli
```

The scaffold contains no analysis implementation yet. Keep analysis logic in
the libraries and use the CLI to exercise it. Builds and execution use the .NET
SDK; Visual Studio is not required.

## Implementation plan

Follow the [C# call-chain research plan](docs/superpowers/plans/2026-10-12-csharp-call-chain-research-plan.md)
for stages 1–5. Preserve the existing `sharpview.slnx` and project names.
The earlier foundation plan is retained as superseded background material.

On this machine, the SDK is installed at `~/.dotnet/dotnet`. If `dotnet` is
not on PATH, use that executable for the commands above.
