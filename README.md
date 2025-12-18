# VelopackExtension.MirrorChyan

为 Velopack 添加Mirror酱更新源的支持。

## Getting Started

1. 从 [NuGet](https://www.nuget.org/packages/VelopackExtension.MirrorChyan) 安装库
2. 配置 [MirrorChyan.Net](https://github.com/d3ara1n/MirrorChyan.Net) 并将其加入到服务容器
3. 添加 MirrorChyan 更新源
4. 配置 Velopack 以在服务容器中使用 `UpdateManager`

```bash
dotnet add package VelopackExtension.MirrorChyan
```

```csharp
services.AddMirrorChyan("abb", "abbTauriGui", "v1.0.0");
services.AddVelopackMirrorChyanSource();
services.AddSingleton<UpdateManager>(sp => new UpdateManager(sp.GetRequiredService<IUpdateSource>()));
```

## Note

由于 Velopack 的增量包要求每个版本都有增量+最新版本有全量文件，而 MirrorChyan 无法实现最新版本没有获取相邻版本之间的增量版本集合能力，因此无法实现增量更新。
