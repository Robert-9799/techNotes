# CUDA notes

## Tutorials

1. https://devblogs.nvidia.com/parallelforall/even-easier-introduction-cuda/
2. https://devblogs.nvidia.com/parallelforall/easy-introduction-cuda-c-and-c/
3. http://docs.nvidia.com/cuda/cusolver/index.html


## Error Handle

### unified memory profiling failed

参考http://blog.csdn.net/u010837794/article/details/64443679

```
nvprof --unified-memory-profiling off ./add_cuda
```

### Strange Output

Pay attention to the size of vectors when running `cudaMemcpy()` .

and don't mess up the order of dimensions.


### cudaMemcpy fails

check whether the order of destination and source variables.

### cudaDeviceReset

think twice before adding the following code
```
cudaDeviceReset
```

### free(): invalid next size (fast/normal)

http://blog.sina.com.cn/s/blog_77f1e27f01019qq9.html

### Error [an illegal memory access was encountered]

多半数组越界，另外，注意对于double的数值型指针，

DO NOT

```
double *pone;
```

and DO NOT

```
double one;
double *pone = &one;
```
YOU MUST
```
double *pone = (double*)malloc(sizeof(double));
*pone = 1.0;
```

## 问题1

1. 重复运行结果不一样
2. 关于两个for循环
3.

## help

1. [Element-by-element vector multiplication with CUDA](https://stackoverflow.com/questions/16899237/element-by-element-vector-multiplication-with-cuda)
2. [Is there a cuda function to copy a row from a Matrix in column major?](https://stackoverflow.com/questions/21002621/is-there-a-cuda-function-to-copy-a-row-from-a-matrix-in-column-major)
3. [“invalid configuration argument ” error for the call of CUDA kernel?](http://blog.csdn.net/dcrmg/article/details/54850766)
虽然block每行每列的thread最大值为512，高的thread最大值为62;但是行列高的乘积最大为768（有些硬件为1024）
http://blog.csdn.net/dcrmg/article/details/54850766
4. [Incomplete output from printf() called on device](https://stackoverflow.com/questions/15421626/incomplete-output-from-printf-called-on-device)
5. [关于CUDA中__threadfence的理解](http://blog.csdn.net/yutianzuijin/article/details/8507355)
6. [
Call cublas API from kernel](https://devtalk.nvidia.com/default/topic/902074/call-cublas-api-from-kernel/?offset=3)
7. [CUDA Memory Hierarchy](https://graphics.cg.uni-saarland.de/fileadmin/cguds/courses/ss14/pp_cuda/slides/02_-_CUDA_Memory_Hierarchy.pdf)
8. [In a CUDA kernel, how do I store an array in “local thread memory”?](https://stackoverflow.com/questions/10297067/in-a-cuda-kernel-how-do-i-store-an-array-in-local-thread-memory)
9. [cublas handle reuse](https://devtalk.nvidia.com/default/topic/941557/gpu-accelerated-libraries/cublas-handle-reuse/)
10. [Does __syncthreads() synchronize all threads in the grid?](https://stackoverflow.com/questions/15240432/does-syncthreads-synchronize-all-threads-in-the-grid)
11. [How to call __device__ function in CUDA with fewer threads](https://stackoverflow.com/questions/15483903/how-to-call-device-function-in-cuda-with-fewer-threads)
12. [CUDA threads for inner loop](https://stackoverflow.com/questions/12816137/cuda-threads-for-inner-loop?rq=1)
13. [CUDA printf() crashes when large number of threads and blocks are launched](https://stackoverflow.com/questions/25365614/cuda-printf-crashes-when-large-number-of-threads-and-blocks-are-launched/25366346)
14. [Intro to image processing with CUDA](http://supercomputingblog.com/cuda/intro-to-image-processing-with-cuda/2/)
15. [CUDA parallelizing a nested for loop](https://stackoverflow.com/questions/13215614/cuda-parallelizing-a-nested-for-loop?noredirect=1&lq=1)
16. [CUDA kernel - nested for loop](https://stackoverflow.com/questions/5306117/cuda-kernel-nested-for-loop)
17. [For nested loops with CUDA](https://stackoverflow.com/questions/9921873/for-nested-loops-with-cuda?noredirect=1&lq=1)
18. [CUDA kernel - nested for loop](https://stackoverflow.com/questions/5306117/cuda-kernel-nested-for-loop)
19. [Converting “for” loops into cuda parallelized code](https://stackoverflow.com/questions/22062770/converting-for-loops-into-cuda-parallelized-code)
20. [What does “Misaligned address error” mean?](https://stackoverflow.com/questions/28727914/what-does-misaligned-address-error-mean)
21. [memory allocation inside a CUDA kernel](https://stackoverflow.com/questions/9806299/memory-allocation-inside-a-cuda-kernel)
22. [NCSA GPU programming tutorial](http://www.ncsa.illinois.edu/People/kindr/projects/hpca/files/NCSA_GPU_tutorial_d3.pdf)
23. [Complicated for loop to be ported to a CUDA kernel](https://stackoverflow.com/questions/6564835/complicated-for-loop-to-be-ported-to-a-cuda-kernel)
24. [CUDA error message : unspecified launch failure](https://stackoverflow.com/questions/9901803/cuda-error-message-unspecified-launch-failure)
25. [Extracting matrix columns with CUDA?](https://stackoverflow.com/questions/31127484/extracting-matrix-columns-with-cuda)
26. [Is there a cuda function to copy a row from a Matrix in column major?](https://stackoverflow.com/questions/21002621/is-there-a-cuda-function-to-copy-a-row-from-a-matrix-in-column-major?newreg=8625eba8f07142728d2b53b8e8899348)
27. [Element-by-element vector multiplication with CUDA](https://stackoverflow.com/questions/16899237/element-by-element-vector-multiplication-with-cuda)
28. [
Converting C/C++ for loops into CUDA](https://stackoverflow.com/questions/6613106/converting-c-c-for-loops-into-cudas)
29. [GPU学习笔记系列](http://blog.csdn.net/MySniper11/article/category/1200645)
30. [多线程有什么用？](https://www.zhihu.com/question/19901763)
31. [CUDA常见问题与解答](http://blog.csdn.net/wufenxia/article/details/7601254)
32. [cudaStreamSynchronize vs CudaDeviceSynchronize vs cudaThreadSynchronize](https://stackoverflow.com/questions/13485018/cudastreamsynchronize-vs-cudadevicesynchronize-vs-cudathreadsynchronize/13485891)