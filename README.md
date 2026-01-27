# CIS 374 - Algorithms Labs

Labs for CIS 374 (Algorithms) at Freed-Hardeman University.

**Framework:** .NET 9.0

## Lab0: WordSet

Implements the `IWordSet` interface, which provides operations on a collection of words:

- **Add / Remove / Contains** - set membership operations
- **Next / Prev** - find the immediate lexicographic successor or predecessor
- **Prefix(prefix, k)** - find up to *k* words starting with a given prefix, sorted
- **Range(lo, hi, k)** - find up to *k* words in the inclusive lexicographic range [lo, hi], sorted

`HashWordSet` is the reference implementation backed by a `HashSet<string>`.

## Build & Run

```bash
dotnet build            # build the solution
dotnet run --project Lab0   # run Lab0
dotnet test             # run all tests
dotnet test --filter "FullyQualifiedName~TestNext"  # run a specific test
```
