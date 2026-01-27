# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a C# project for CIS 374 (Algorithms course at Freed-Hardeman University). The labs contain data structure implementations, starting with Lab0 which implements a `WordSet` interface for efficient string lookup and lexicographic operations.

**Framework:** .NET 9.0

## Architecture

### Lab0: WordSet Implementation

**Core Concept:** The lab implements the `IWordSet` interface, which provides operations on a collection of words:

- **Basic operations:** `Add()`, `Remove()`, `Contains()` for set membership
- **Lexicographic neighbors:** `Next()` and `Prev()` to find immediate successors/predecessors in alphabetical order
- **Prefix queries:** `Prefix(prefix, k)` to find up to k words starting with a given prefix
- **Range queries:** `Range(lo, hi, k)` to find up to k words in a lexicographic range [lo, hi]

**Current Implementation:** `HashWordSet` uses a simple `HashSet<string>` backend. This provides O(1) basic operations but requires O(n log n) sorting for ordered operations like prefix/range queries.

**Key Files:**
- `Lab0/IWordSet.cs`: Interface definition
- `Lab0/HashWordSet.cs`: Reference implementation using HashSet
- `Lab0/Program.cs`: Entry point
- `Lab0.Tests/HashWordSetTests.cs`: MSTest unit tests

The comment block at the top of `HashWordSet.cs` (lines 2-4) shows sample data for testing.

**Test Framework:** MSTest (Microsoft.VisualStudio.TestTools.UnitTesting) with implicit usings enabled.

## Common Commands

### Build
```bash
dotnet build
```

Build the entire solution (all projects in labs.sln).

### Run
```bash
dotnet run --project Lab0
```

Run the Lab0 project.

### Clean
```bash
dotnet clean
```

Remove build artifacts (bin/ and obj/ directories).

### Restore Dependencies
```bash
dotnet restore
```

Restore NuGet packages if needed.

### Run Tests
```bash
dotnet test
```

Run all tests in the solution (uses MSTest framework).

### Run Specific Test
```bash
dotnet test --filter "FullyQualifiedName~TestNext"
```

Run tests matching a specific name pattern.

## Key Configuration

- **Solution file:** `labs.sln`
- **Target framework:** net9.0
- **Nullable reference types:** Enabled (`<Nullable>enable</Nullable>`)
- **Implicit usings:** Enabled (global `using` statements)
- **Output type:** Executable (Exe)

## Development Notes

- The project uses C# 12+ features (record types, nullable reference types, init accessors)
- `IWordSet` is designed to support multiple implementations (e.g., TreeSet-like structures for better ordered operation performance)
- Some methods in `HashWordSet` raise `NotImplementedException()` and will need to be completed as part of the lab work
