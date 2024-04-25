# C++ Implementation of the Binary Feasible Triplet Algorithm

This code is an implementation of the Binary Feasible Triplet Algorithm as defined in the paper "Improved Lower Bounds for the Chvátal-Sankoff
Constants", written by George T. Heineman, Chase Miller, Daniel Reichman, Andrew Salls, Gábor Sárközy, and Duncan Soiffer. We include a brief summary below, but for a further explanation of the code, please read this paper.

The Chvatal-Sankoff constants $\gamma_{\sigma, d}$ are a set of constants such that 

$\gamma_{\sigma, d} = \lim\limits_{n \to \infty} \frac{E[LCS_{\sigma, d}]}{n}$

where $LCS_{\sigma, d}$ is the $d$-LCS for $d$ random strings, where each string is of length $n$ and each character in the string is one of $\sigma$ possible characters, chosen with equal chances for each character randomly. Essentially, this constant describes the expected length of the LCS when compared to the original strings as long as the strings are long enough.

The goal of this code is to calculate a lower bound on the specific case $\gamma_{2, 2}$, since its exact value is currently unknown. We specify this specific constant because the binary nature allows for additional improvements, and because a majority of prior work in the area has focused on this constant.

# How to run
All code necessary should be included in this repository. First, download the repository. Keep in mind that this algorithm is highly exponential, creating and modifying multiple $2^{2*length}$ vectors of doubles. Be careful not to set alphabet_size, string_count, or length too large. We define two C++ files: `Binary-RAMOnly.cpp` and `Binary-ExtnMem.cpp`. The first file stores all data in RAM, while the second file stores currently-unused data to external memory. The RAM only file should be used for smaller values, as it runs faster, while the external memory file should be used for larger values, as a typical computer does not have the RAM necessary to run the code for large length strings.

To compile the program, open the terminal where one of these files is saved, and run

`g++ -O3 -pthread -I EIGEN_PATH ./#FILENAME#.cpp -o #FILENAME#`

where `EIGEN_PATH` is the path to the Eigen C++ library, version 3.4.0, and `#FILENAME#` is either `Binary-RAMOnly` or `Binary-ExtnMem`. If you cloned this repository off GitHub, the path should be ./eigen-3.4.0/

This compilation command assumes you have g++ installed, but a slightly modified command should work with gcc or any other standard C++ compiler.

This should have created the file `#FILENAME#` in the same folder where ParallelMulti.cpp is saved. With the terminal still in this folder, run

`./#FILENAME#`

to run the algorithm.

# Credits
This code is based on the definition of the Feasible Triplet algorithm developed by Kiwi and Soto. See their paper at https://www.cambridge.org/core/journals/combinatorics-probability-and-computing/article/abs/on-a-speculated-relation-between-chvatalsankoff-constants-of-several-sequences/7982322390D3236DC7BC96E42855768A

Learn more about Eigen at https://eigen.tuxfamily.org/index.php?title=Main_Page