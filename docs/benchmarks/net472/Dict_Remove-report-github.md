``` ini

BenchmarkDotNet=v0.11.3, OS=Windows 10.0.17763.292 (1809/October2018Update/Redstone5)
Intel Core i7-6700HQ CPU 2.60GHz (Skylake), 1 CPU, 8 logical and 4 physical cores
  [Host] : .NET Framework 4.7.2 (CLR 4.0.30319.42000), 64bit RyuJIT-v4.7.3324.0
  Clr    : .NET Framework 4.7.2 (CLR 4.0.30319.42000), 64bit RyuJIT-v4.7.3324.0

Job=Clr  Runtime=Clr  

```
|       Method |     N |         Mean |       Error |      StdDev | Ratio | Gen 0/1k Op | Gen 1/1k Op | Gen 2/1k Op | Allocated Memory/Op |
|------------- |------ |-------------:|------------:|------------:|------:|------------:|------------:|------------:|--------------------:|
|   **DictRemove** |    **10** |     **74.92 ns** |   **0.3636 ns** |   **0.3401 ns** |  **1.00** |           **-** |           **-** |           **-** |                   **-** |
| PooledRemove |    10 |     71.63 ns |   0.1545 ns |   0.1370 ns |  0.96 |           - |           - |           - |                   - |
|              |       |              |             |             |       |             |             |             |                     |
|   **DictRemove** |   **100** |    **762.16 ns** |   **1.5332 ns** |   **1.3591 ns** |  **1.00** |           **-** |           **-** |           **-** |                   **-** |
| PooledRemove |   100 |    713.53 ns |   2.1222 ns |   1.8813 ns |  0.94 |           - |           - |           - |                   - |
|              |       |              |             |             |       |             |             |             |                     |
|   **DictRemove** | **10000** | **77,378.74 ns** | **450.1810 ns** | **421.0996 ns** |  **1.00** |           **-** |           **-** |           **-** |                   **-** |
| PooledRemove | 10000 | 70,608.10 ns | 148.6903 ns | 131.8101 ns |  0.91 |           - |           - |           - |                   - |
