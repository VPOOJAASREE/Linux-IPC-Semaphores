# Linux-IPC-Semaphores
Ex05-Linux IPC-Semaphores

# AIM:
To Write a C program that implements a producer-consumer system with two processes using Semaphores.

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - Sempahores

### Step 3:

Execute the C Program for the desired output. 

# PROGRAM:
DEVELOPED BY

V. POOJAA SREE

212223040147
## Write a C program that implements a producer-consumer system with two processes using Semaphores.

```
#include <stdio.h>
#include <sys/ipc.h>
#include <sys/shm.h>

int main()
{
	// Generate a unique key using ftok
	key_t key = ftok("shmfile", 65);

	// Get an identifier for the shared memory segment using shmget
	int shmid = shmget(key, 1024, 0666 | IPC_CREAT);
      printf("Shared memory id = %d \n",shmid);
// Attach to the shared memory segment using shmat
	char* str = (char*)shmat(shmid, (void*)0, 0);
	
    printf("Write Data : ");
	fgets(str, 1024, stdin);

	printf("Data written in memory: %s\n", str);

	// Detach from the shared memory segment using shmdt
	shmdt(str);

	return 0;
}
```




## OUTPUT
![os](https://github.com/VPOOJAASREE/Linux-IPC-Semaphores/assets/155145525/75926efe-06b3-4586-a893-c38c434a2656)







# RESULT:
The program is executed successfully.
