``` ini

BenchmarkDotNet=v0.11.3, OS=Windows 10.0.17763.292 (1809/October2018Update/Redstone5)
Intel Core i7-6700HQ CPU 2.60GHz (Skylake), 1 CPU, 8 logical and 4 physical cores
.NET Core SDK=3.0.100-preview-009812
  [Host] : .NET Core 2.2.1 (CoreCLR 4.6.27207.03, CoreFX 4.6.27207.03), 64bit RyuJIT
  Core   : .NET Core 2.2.1 (CoreCLR 4.6.27207.03, CoreFX 4.6.27207.03), 64bit RyuJIT

Job=Core  Runtime=Core  InvocationCount=1  
UnrollFactor=1  

```
|                              Method | CountToIntersect | InitialSetSize |      Mean |     Error |    StdDev |    Median | Ratio | RatioSD | Gen 0/1k Op | Gen 1/1k Op | Gen 2/1k Op | Allocated Memory/Op |
|------------------------------------ |----------------- |--------------- |----------:|----------:|----------:|----------:|------:|--------:|------------:|------------:|------------:|--------------------:|
|     **HashSet_SymmetricExcept_Hashset** |            **32000** |        **8000000** |  **1.681 ms** | **0.1386 ms** | **0.4087 ms** |  **1.486 ms** |  **1.00** |    **0.00** |           **-** |           **-** |           **-** |                   **-** |
| PooledSet_SymmetricExcept_PooledSet |            32000 |        8000000 |  1.349 ms | 0.1128 ms | 0.3325 ms |  1.415 ms |  0.85 |    0.31 |           - |           - |           - |                   - |
|        HashSet_SymmetricExcept_Enum |            32000 |        8000000 |  3.845 ms | 0.1070 ms | 0.3105 ms |  3.846 ms |  2.45 |    0.63 |           - |           - |           - |             25176 B |
|      PooledSet_SymmetricExcept_Enum |            32000 |        8000000 |  3.116 ms | 0.1452 ms | 0.4236 ms |  3.132 ms |  1.98 |    0.57 |           - |           - |           - |             25096 B |
|       HashSet_SymmetricExcept_Array |            32000 |        8000000 |  3.927 ms | 0.1150 ms | 0.3318 ms |  3.907 ms |  2.50 |    0.63 |           - |           - |           - |             25168 B |
|     PooledSet_SymmetricExcept_Array |            32000 |        8000000 |  2.877 ms | 0.1371 ms | 0.4000 ms |  2.812 ms |  1.81 |    0.43 |           - |           - |           - |             25056 B |
|                                     |                  |                |           |           |           |           |       |         |             |             |             |                     |
|     **HashSet_SymmetricExcept_Hashset** |           **320000** |        **8000000** |  **3.936 ms** | **0.1389 ms** | **0.4074 ms** |  **3.983 ms** |  **1.00** |    **0.00** |           **-** |           **-** |           **-** |                   **-** |
| PooledSet_SymmetricExcept_PooledSet |           320000 |        8000000 |  3.474 ms | 0.1207 ms | 0.3558 ms |  3.527 ms |  0.89 |    0.12 |           - |           - |           - |                   - |
|        HashSet_SymmetricExcept_Enum |           320000 |        8000000 | 18.690 ms | 0.3701 ms | 0.7560 ms | 18.747 ms |  5.07 |    0.50 |           - |           - |           - |             25176 B |
|      PooledSet_SymmetricExcept_Enum |           320000 |        8000000 | 17.154 ms | 0.3525 ms | 0.5167 ms | 17.116 ms |  4.46 |    0.37 |           - |           - |           - |             25096 B |
|       HashSet_SymmetricExcept_Array |           320000 |        8000000 | 18.895 ms | 0.4219 ms | 0.6813 ms | 18.898 ms |  4.98 |    0.44 |           - |           - |           - |             25168 B |
|     PooledSet_SymmetricExcept_Array |           320000 |        8000000 | 14.962 ms | 0.2952 ms | 0.6722 ms | 14.918 ms |  4.01 |    0.37 |           - |           - |           - |             25056 B |