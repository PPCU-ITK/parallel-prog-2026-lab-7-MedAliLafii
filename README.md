[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/JdNTJJYf)
# assignment-7
module load nvhpc

module load cuda

module load craype-accel-nvidia80

nvc++ -mp=gpu -gpu=cc80 -Ofast laplace2d.cpp -o laplace -Minfo=accel,mp

srun -p gpu --gres=gpu:1 --ntasks=1 --time=00:05:00 --mem=40G ./laplace

##	CPU	GPU
Default	0.760s	0.819s
4x	3.044s	0.974s
8x	6.038s	1.128s
16x	12.162s	2.237s
