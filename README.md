
## KubeCon NA, Atlanta, US, Nov 2025

### Deep Dive: Handling Kubernetes Memory Pressure & Achieving Workload Stability With NodeSwap 
slides here:  [[PUBLIC] Deep Dive_ Handling Kubernetes Memory Pressure & Achieving Workload Stability With NodeSwap.pptx.pdf](https://github.com/user-attachments/files/23554082/PUBLIC.Deep.Dive_.Handling.Kubernetes.Memory.Pressure.Achieving.Workload.Stability.With.NodeSwap.pptx.pdf)



### Linux Kernel Memory Buffer

```
// From a 1.32 GKE node -- 8GB ubuntu 
$ sysctl vm.min_free_kbytes
vm.min_free_kbytes = 67584 // ~68MB
```

Linux kernel will set this value based on RAM size and thp pagesizes - a good explanation of how it gets [68MB in x86 systems is here](https://unix.stackexchange.com/a/525457).

From kernel bits --
1. Initial kernel calculation (lowmem bytes) -- setting default `linux/mm /page_alloc.c:calculate_min_free_kbytes` [here](https://github.com/torvalds/linux/blob/master/mm/page_alloc.c#L6204).
2. Huge-table adjustment [here](https://elixir.bootlin.com/linux/v5.0.17/source/mm/khugepaged.c#L1862)   



