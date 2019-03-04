This repository is forked from user PotatoDrug under the MIT general licensing agreement. 
Within this repository, there are Python3 scripts for Shor's Algorithm and Grover's Algorithm used for quantum cryptography. 

Quantum cryptography in this particular setting refers to decrypting RSA (or other prime number based encryption systems) using prime factorization via quantum computer. While there are no quantum computer exists today that is capable of decoding golden standard scale RSA, the application of Quantum Fourier Transform in Shor’s algorithm will be able to reliably deduce the correct keys based on the theory of complex analysis. 

Qubits based quantum computer can perform exponentially more calculations than a bit-based classical computer due to the super positioning principle (i.e. 20 qubits can store 2^20 values). However, super positioning collapses on the instant a sequence of 0s and 1s are outputted. This means the classical factorization code (i.e. the one we seen in weekly challenge 4) does not make the calculation more manageable. Namely, if a million calculations are needed to find one answer, classical computer preforms a million calculations in sequence, whereas quantum computer can process all of them at once while only yielding one answer at random. Thus, the probability of yielding the correct answer is one of a million. In the words of computer scientist Scott Aaronson, “quantum computers would not solve hard search problems instantaneously by simply trying all the possible solutions at once.”

This is where Quantum Fourier Transform comes in (as seen in classical_shor.py). Using this mathematical manipulation, each probable solution is “assigned an error score”, and it destructively interferes with wrong answers, and amplify the probability of yielding the correct answer. In the case of cryptography, Quantum Fourier Transformed based approach can easily find the period of mod N, which is the most computation intensive step of decrypting a RSA lock. Here, N is the large number used to generate RSA keys. 






# The Following notes are from the original author of the repository

'''
# Quantum Cryptography

## Shor's Algorithm

Please do not actually use classical_shor.py to try to factorize large numbers, it is a really inefficient way of factorization for a classical computer.

```bash
python3 -m timeit -s 'import classical_shor' 'classical_shor.solve(80609)'
100 loops, best of 3: 3.11 msec per loop ((3.11 * 10^-3) seconds)
```

pure_factorizatrion.py is a much better algorithm for finding primes on a classical computer.

```bash
python3 -m timeit -s 'import pure_factorization' 'pure_factorization.factorize(80609)'
100000 loops, best of 3: 3.56 usec per loop ((3.56 * 10^-6) seconds)
```

* classical_shor.py
  * Shor's algorithm implemented purely with classical algorithm
* pure_factorization.py
  * Classical way of finding prime factors

## Grover's Algorithm

Reduces the time complexity of finding the input to a black box(Oracle) function that produces a particular output from O(N) to O(sqrt(N)).


'''
