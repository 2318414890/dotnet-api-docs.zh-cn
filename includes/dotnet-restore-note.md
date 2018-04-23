> [!NOTE]
> 从 .NET Core 2.0 开始，无需运行 [`dotnet restore`](~/docs/core/tools/dotnet-restore.md)，因为它由需有还原的所有命令隐式运行，如 `dotnet build` 和 `dotnet run`。 在执行显式还原有意义的某些情况下，它仍然是有效的命令，例如 [Visual Studio Team Services 中的持续集成生成](/vsts/build-release/apps/aspnet/build-aspnet-core)中，或在需要显式控制还原发生时间的生成系统中。
