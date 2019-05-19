``` ini

BenchmarkDotNet=v0.11.5, OS=Windows 10.0.18362
Intel Core i7-6700HQ CPU 2.60GHz (Skylake), 1 CPU, 8 logical and 4 physical cores
.NET Core SDK=3.0.100-preview5-011568
  [Host] : .NET Core 3.0.0-preview5-27626-15 (CoreCLR 4.6.27622.75, CoreFX 4.700.19.22408), 64bit RyuJIT
  Clr    : .NET Framework 4.7.2 (CLR 4.0.30319.42000), 64bit RyuJIT-v4.8.3801.0
  Core   : .NET Core 3.0.0-preview5-27626-15 (CoreCLR 4.6.27622.75, CoreFX 4.700.19.22408), 64bit RyuJIT

Jit=RyuJit  Platform=X64  

```
|     Method |  Job | Runtime |      N |   Type |       Mean |      Error |     StdDev | Ratio | RatioSD |    Gen 0 |    Gen 1 |    Gen 2 | Allocated |
|----------- |----- |-------- |------- |------- |-----------:|-----------:|-----------:|------:|--------:|---------:|---------:|---------:|----------:|
|  **StackPush** |  **Clr** |     **Clr** |   **1000** |    **Int** |   **3.762 us** |  **0.0524 us** |  **0.0490 us** |  **1.00** |    **0.00** |   **2.6855** |        **-** |        **-** |    **8459 B** |
| PooledPush |  Clr |     Clr |   1000 |    Int |   4.603 us |  0.0787 us |  0.0736 us |  1.22 |    0.02 |   0.0153 |        - |        - |      56 B |
|            |      |         |        |        |            |            |            |       |         |          |          |          |           |
|  StackPush | Core |    Core |   1000 |    Int |   2.958 us |  0.0559 us |  0.0523 us |  1.00 |    0.00 |   2.6817 |        - |        - |    8424 B |
| PooledPush | Core |    Core |   1000 |    Int |   2.478 us |  0.0356 us |  0.0333 us |  0.84 |    0.02 |   0.0153 |        - |        - |      56 B |
|            |      |         |        |        |            |            |            |       |         |          |          |          |           |
|  **StackPush** |  **Clr** |     **Clr** |   **1000** | **String** |   **6.168 us** |  **0.1126 us** |  **0.1053 us** |  **1.00** |    **0.00** |   **5.2872** |        **-** |        **-** |   **16662 B** |
| PooledPush |  Clr |     Clr |   1000 | String |   9.210 us |  0.0726 us |  0.0679 us |  1.49 |    0.03 |   0.0153 |        - |        - |      56 B |
|            |      |         |        |        |            |            |            |       |         |          |          |          |           |
|  StackPush | Core |    Core |   1000 | String |   5.478 us |  0.1083 us |  0.1064 us |  1.00 |    0.00 |   5.2872 |        - |        - |   16600 B |
| PooledPush | Core |    Core |   1000 | String |   6.891 us |  0.1037 us |  0.0970 us |  1.26 |    0.03 |   0.0153 |        - |        - |      56 B |
|            |      |         |        |        |            |            |            |       |         |          |          |          |           |
|  **StackPush** |  **Clr** |     **Clr** |  **10000** |    **Int** |  **38.790 us** |  **0.6131 us** |  **0.5735 us** |  **1.00** |    **0.00** |  **41.6260** |        **-** |        **-** |  **131606 B** |
| PooledPush |  Clr |     Clr |  10000 |    Int |  50.489 us |  0.9890 us |  0.9713 us |  1.30 |    0.03 |        - |        - |        - |      56 B |
|            |      |         |        |        |            |            |            |       |         |          |          |          |           |
|  StackPush | Core |    Core |  10000 |    Int |  27.448 us |  0.4812 us |  0.4501 us |  1.00 |    0.00 |  41.6565 |        - |        - |  131400 B |
| PooledPush | Core |    Core |  10000 |    Int |  22.580 us |  0.1909 us |  0.1786 us |  0.82 |    0.02 |        - |        - |        - |      56 B |
|            |      |         |        |        |            |            |            |       |         |          |          |          |           |
|  **StackPush** |  **Clr** |     **Clr** |  **10000** | **String** | **121.917 us** |  **2.2132 us** |  **2.0702 us** |  **1.00** |    **0.00** |  **41.5039** |  **41.5039** |  **41.5039** |  **262700 B** |
| PooledPush |  Clr |     Clr |  10000 | String | 109.168 us |  1.5204 us |  1.4222 us |  0.90 |    0.02 |        - |        - |        - |      57 B |
|            |      |         |        |        |            |            |            |       |         |          |          |          |           |
|  StackPush | Core |    Core |  10000 | String | 124.350 us |  2.1401 us |  2.0019 us |  1.00 |    0.00 |  41.5039 |  41.5039 |  41.5039 |  262456 B |
| PooledPush | Core |    Core |  10000 | String |  68.742 us |  1.2986 us |  1.3895 us |  0.55 |    0.01 |        - |        - |        - |      56 B |
|            |      |         |        |        |            |            |            |       |         |          |          |          |           |
|  **StackPush** |  **Clr** |     **Clr** | **100000** |    **Int** | **501.163 us** |  **5.1679 us** |  **4.8340 us** |  **1.00** |    **0.00** | **168.9453** | **127.9297** | **126.9531** | **1051559 B** |
| PooledPush |  Clr |     Clr | 100000 |    Int | 429.499 us |  1.9748 us |  1.5418 us |  0.86 |    0.01 |        - |        - |        - |      60 B |
|            |      |         |        |        |            |            |            |       |         |          |          |          |           |
|  StackPush | Core |    Core | 100000 |    Int | 440.168 us |  8.3184 us |  8.5423 us |  1.00 |    0.00 | 170.4102 | 127.9297 | 127.9297 | 1049588 B |
| PooledPush | Core |    Core | 100000 |    Int | 210.556 us |  1.3272 us |  1.1083 us |  0.48 |    0.01 |        - |        - |        - |      56 B |
|            |      |         |        |        |            |            |            |       |         |          |          |          |           |
|  **StackPush** |  **Clr** |     **Clr** | **100000** | **String** | **954.139 us** | **37.0706 us** | **36.4083 us** |  **1.00** |    **0.00** | **160.1563** | **119.1406** | **119.1406** | **2100279 B** |
| PooledPush |  Clr |     Clr | 100000 | String | 997.189 us | 18.6319 us | 19.1336 us |  1.05 |    0.05 |        - |        - |        - |      64 B |
|            |      |         |        |        |            |            |            |       |         |          |          |          |           |
|  StackPush | Core |    Core | 100000 | String | 927.488 us | 17.9152 us | 16.7579 us |  1.00 |    0.00 | 194.3359 | 153.3203 | 152.3438 | 2098426 B |
| PooledPush | Core |    Core | 100000 | String | 716.763 us |  6.2218 us |  5.8199 us |  0.77 |    0.02 |        - |        - |        - |      56 B |