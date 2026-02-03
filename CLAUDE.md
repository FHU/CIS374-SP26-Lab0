# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

C# project for CIS 374 (Algorithms) at Freed-Hardeman University. Implements data structure labs with a focus on efficient string lookup and lexicographic operations.

**Framework:** .NET 9.0

## Architecture

### IWordSet Interface

The `IWordSet` interface defines operations on a word collection:

- **Basic operations:** `Add()`, `Remove()`, `Contains()` for O(1) or O(log n) set membership
- **Lexicographic neighbors:** `Next()` and `Prev()` to find immediate successors/predecessors
- **Prefix queries:** `Prefix(prefix, k)` returns up to k words starting with a given prefix, sorted
- **Range queries:** `Range(lo, hi, k)` returns up to k words in lexicographic range [lo, hi], sorted

### Implementations

- **`HashWordSet`** - Uses `HashSet<string>`. O(1) basic ops, O(n log n) for ordered ops (scans and sorts).
- **`SortedWordSet`** - Uses `SortedSet<string>`. O(log n) basic ops, O(k) for prefix/range via `GetViewBetween()`.

Both implementations normalize input (trim + lowercase) and use the same sample test data in their header comments.

### Key Files

- `Lab0/IWordSet.cs` - Interface definition
- `Lab0/HashWordSet.cs` - Reference implementation (some methods throw `NotImplementedException`)
- `Lab0/SortedWordSet.cs` - Alternative implementation using sorted data structure
- `Lab0.Tests/HashWordSetTests.cs` and `SortedWordSetTests.cs` - MSTest unit tests

## Common Commands

```bash
# Build
dotnet build

# Run
dotnet run --project Lab0

# Run all tests
dotnet test

# Run specific test by name pattern
dotnet test --filter "FullyQualifiedName~TestNext"

# Run tests for specific class
dotnet test --filter "FullyQualifiedName~SortedWordSetTests"
```

## Configuration

- **Solution file:** `Lab0.sln`
- **Target framework:** net9.0
- **Nullable reference types:** Enabled
- **Implicit usings:** Enabled
- **Test framework:** MSTest

## Development Notes

- Methods marked with `// TODO` or throwing `NotImplementedException()` are lab exercises to complete
- The `SortedWordSet.Prefix()` method has hardcoded test values that need to be replaced with actual logic
- `MAX_STRING` constant (`"\uFFFF\uFFFF\uFFFF"`) in SortedWordSet is used as an upper bound for `GetViewBetween()` range queries
