# 64-bit Operating System Kernel

## One-line build instructions
To stand up the reproducible Docker build environment and produce the kernel, run the following command in the root of the repository:

`docker run --rm -v "$(pwd):/root/env" buildenv --> make build-x86_64`
`qemu-system-x86_64 -cdrom dist/x86_64/kernel.iso`

## Demonstration Video
https://drive.google.com/drive/folders/1fsqrKYIJzeO4xMnkBvbKN26bZEhesbWh?usp=drive_link
