An Operating System (OS) is a/an:
- Interface between a computer user and computer hardware.
- Software that enables applications to interact with a computer's hardware.
	- The software that contains the core components of the operating system is called the **kernel**.

```mermaid
%% Interaction bewteen the OS, an application and hardware
flowchart TD
	subgraph Software
	A1[Application Software] --> B[System Libraries]
	A2[System Software] --> B[System Libraries]
    subgraph OS
    subgraph Shell
    C[Kernel]
    end
    B --> C
    C --> D[Device Drivers]
    end
	end
	subgraph Hardware
	E[CPU]
	F[RAM]
	I/O
	end
	D --> Hardware
```

- The shell takes commands from the user and executes kernel's functions.