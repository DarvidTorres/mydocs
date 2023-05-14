- A modern computer has four levels of the [memory hierarchy](https://en.wikipedia.org/wiki/Memory_hierarchy).

```mermaid
%% Memory hierarchy
flowchart TB
    subgraph Motherboard
    subgraph CPU
	A[Registers]<-->B[Cache]
    end
    end
    B<-->C[RAM]
    C <--> D[Disk Drive]
```
- The Central Processing Unit (CPU) is basically a huge network of logic gates.
	- It is also known as a processor or microprocessor.
	- Inside a CPU there are thousands of microscopic transistors.
- The CPU chip contains two separate modules: registers and a memory cache.
- Data transfer occurs between adjacent memory levels.
- The CPU process data from its registers.
	- This is the only place where the processor can take data for calculations.
If the CPU needs data from the disk drive, the following data transfers happen:

```mermaid
flowchart TD
A[Disk drive] --> B[RAM]
B --> C[Processor cache]
C --> D[Processor registers]
```

