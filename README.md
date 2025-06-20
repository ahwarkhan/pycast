**PyCastX** is a Python package that provides:

- Secure **Elliptic Curve Cryptography (ECC)** utilities
- A **Genetic Algorithm-based AES S-Box** optimizer for enhanced cryptographic strength
- High-entropy key generation using Shannon entropy

## 📦 Installation

Install directly from [PyPI](https://pypi.org/project/pycastx):

```bash
pip install pycastx
````

## 🔐 Features

### 🔸 Elliptic Curve Cryptography (ECC)

* Define a custom elliptic curve over a finite field.
* Generate secure private/public key pairs.
* Validate whether a point lies on the curve.
* Generate high-entropy keys based on Shannon entropy.

### 🔸 Genetic AES S-Box Optimizer

* Generate substitution boxes (S-boxes) using Genetic Algorithms.
* Optimize S-boxes for:

  * **Non-linearity**
  * **Avalanche Effect**
* Useful in block cipher research and analysis.

## 🚀 Usage Examples

### ✅ ECC Key Generation

```python
from pycastx.ecc import EllipticCurve, KeyEntropyCalculator

# Define custom curve parameters
a = 56698187605326110043627228396178346077120614539475214109386828188763884139993
b = 17577232497321838841075697789794520262950426058923084567046852300633325438902
p = 76884956397045344220809746629001649093037950200943055203735601445031516197751
Gx = 63243729749562333355292243550312970334778175571054726587095381623627144114786
Gy = 38218615093753523893122277964030810387585405539772602581557831887485717997975
n = 0xA9FB57DBA1EEA9BC3E660A909D838D718AFCED59

# Initialize curve
curve = EllipticCurve(a, b, p, Gx, Gy, n)

# Key entropy calculator
entropy_calc = KeyEntropyCalculator(curve)
private_key, entropy = entropy_calc.generate_high_entropy_key(num_trials=100)
public_key = curve.public_key_from_private(private_key)

print("Private Key:", private_key)
print("Entropy:", entropy)
print("Public Key:", public_key)
print("Is Public Key Valid?", curve.is_point_on_curve(public_key))
```

### ✅ AES S-Box Generation Using Genetic Algorithm

```python
from pycastx.sbox import DynamicAESSBoxGA

# Initialize Genetic Algorithm
ga = DynamicAESSBoxGA(population_size=50, generations=10, mutation_rate=0.05)

# Generate optimized S-box
optimized_sbox = ga.apply_ga()

print("Optimized S-Box:")
print(optimized_sbox)
```

## 🧪 Running Tests

To run all tests using `unittest`:

```bash
python -m unittest discover tests
```

## 📚 API Reference

### `class EllipticCurve(a, b, p, Gx, Gy, n)`

Represents an elliptic curve over a finite field.

#### Methods:

* `point_addition(P, Q)`
* `scalar_multiplication(k, P)`
* `generate_private_key()`
* `public_key_from_private(private_key)`
* `is_point_on_curve(P)`


### `class KeyEntropyCalculator(curve)`

Computes entropy and generates high-entropy ECC keys.

#### Methods:

* `shannon_entropy(data)`
* `private_key_to_byte_array(private_key)`
* `generate_high_entropy_key(num_trials=100)`


### `class DynamicAESSBoxGA(population_size, generations, mutation_rate)`

Optimizes AES S-boxes using a genetic algorithm.

#### Methods:

* `generate_sbox()`
* `evaluate_sbox(sbox)`
* `apply_ga()`


## 📜 License

This project is licensed under the **MIT License**.
See the [LICENSE](./LICENSE) file for details.


## 🤝 Contributing

Pull requests are welcome! For major changes, please open an issue first to discuss.


## 🧠 Acknowledgements

This package was built to support research in:

* Lightweight cryptography
* ECC-based key generation
* AES S-box design optimization


## 🔗 Links

* [PyPI Project](https://pypi.org/project/pycastx/)
* [GitHub Repository](https://github.com/ahwarkhan/pycastx)