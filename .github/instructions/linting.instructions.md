---
description: Linting rules for code quality - unused variables, async/await patterns, and style enforcement.
---

# Linting Rules & Code Quality

This project uses `.editorconfig` with strict linting rules to maintain code quality.

## Enabled Rules

### Unused Variables & Parameters
These rules catch unreferenced or unread code that should be removed:

- **IDE0051 (warning)**: Remove unused private member
  ```csharp
  private int _unused = 5; // ⚠️ Warning - never used
  ```

- **IDE0052 (warning)**: Remove unread private member
  ```csharp
  private int _field; // ⚠️ Warning - assigned but never read
  ```

- **IDE0059 (warning)**: Unnecessary assignment
  ```csharp
  var x = 1;
  x = 2; // ⚠️ Warning if x is only used as 2
  ```

- **IDE0060 (warning)**: Remove unused parameter
  ```csharp
  public void Method(int unused) { } // ⚠️ Warning
  ```

- **dotnet_code_quality_unused_parameters**: Applied to all unused parameters

### Async/Await Usage
These rules enforce proper async patterns:

- **CS1998 (warning)**: Async method lacks await
  ```csharp
  public async Task DoSomething() { } // ⚠️ Warning - no await in method
  ```

- **CS4014 (warning)**: Call is not awaited
  ```csharp
  HttpClient.GetAsync(url); // ⚠️ Warning - result not awaited
  ```

- **csharp_style_prefer_async_over_sync (warning)**: Use async when available
  ```csharp
  // ⛔ Avoid
  private void LoadData() { _data = client.GetData(); }
  
  // ✅ Prefer
  private async Task LoadDataAsync() { _data = await client.GetDataAsync(); }
  ```

## Intentional Patterns

### Fire-and-Forget Tasks
When you intentionally ignore a task result, use the `_` discard pattern with a comment:

```csharp
// ✅ Correct - discard silences warnings
_ = SaveGameStateAsync(); // Fire and forget

// ⚠️ Causes CS4014 warning - unawaited call
SaveGameStateAsync();
```

This tells linters and readers that the omission is intentional, not a bug.

## Enforcing Rules in Build

To build with strict code style enforcement:

```bash
dotnet build SocOps/SocOps.csproj /p:EnforceCodeStyleInBuild=true
```

This treats style violations as warnings/errors rather than info messages.

## Configuration

All linting rules are defined in `.editorconfig` at the project root:

```ini
# Unused parameters - WARNING
dotnet_code_quality_unused_parameters = all:warning

# Async/await preference - WARNING
csharp_style_prefer_async_over_sync = true:warning

# IDE diagnostic severity mappings
dotnet_diagnostic.CS1998.severity = warning   # Async lacks await
dotnet_diagnostic.CS4014.severity = warning   # Call not awaited
```

## Best Practices

1. **Fix warnings in feature branches** - Don't let them accumulate
2. **Use the discard pattern** - When intentionally ignoring results, use `_ = ...`
3. **Make async all the way** - If a method is async, ensure all blocking calls are awaited
4. **Remove unused code** - Unused parameters and variables add cognitive load
5. **Document fire-and-forget** - Always add a comment explaining why the result is intentionally discarded

## Editor Integration

- **VS Code**: Automatically reads `.editorconfig` and shows violations
- **Visual Studio**: Built-in support with squiggly underlines
- **Rider**: Full support with inspections

No additional setup needed—the rules apply automatically when you open the project.
