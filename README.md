# topological-qubit-library

> **GALACTIC-UNION** · Topological Qubit Simulation & Algorithm Library

[![CI](https://github.com/GALACTIC-UNION/topological-qubit-library/actions/workflows/ci.yml/badge.svg)](https://github.com/GALACTIC-UNION/topological-qubit-library/actions/workflows/ci.yml)
[![Python 3.11+](https://img.shields.io/badge/python-3.11%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## Overview

`topological-qubit-library` (TQL) provides simulation, modeling, and algorithm tools for topological quantum computing — an approach to quantum computing that encodes information in global, topologically protected degrees of freedom, making it inherently resistant to local perturbations.

### What’s included

| Module | Description |
|--------|-------------|
| `tql.anyons` | Anyon model definitions (Ising, Fibonacci, Zₙ parafermions) |
| `tql.braiding` | Braid group generators, braid word compilation, unitary computation |
| `tql.codes` | Topological error-correcting codes (surface code, color code, toric code) |
| `tql.algorithms` | Topological quantum algorithms and circuit templates |
| `tql.simulation` | Anyonic system evolution and measurement simulation |
| `tql.noise` | Topological noise models and decoherence thresholds |

---

## Architecture

```
┌──────────────────────────────────────────────┐
│              TQL Framework                            │
├──────────────────────────────────────────────┤
│    Algorithms  │  Codes  │  Simulation Backend       │
├──────────────────────────────────────────────┤
│  Anyon Models │  Braiding Engine  │  Noise Models    │
└──────────────────────────────────────────────┘
```

---

## Directory Structure

```
topological-qubit-library/
├── src/
│   └── tql/
│       ├── anyons/         # Anyon model definitions & fusion rules
│       ├── braiding/       # Braid group algebra & unitary computation
│       ├── codes/          # Surface, toric, color code implementations
│       ├── algorithms/     # Topological quantum algorithm templates
│       ├── simulation/     # Anyonic system evolution & measurement
│       └── noise/          # Noise models & decoherence thresholds
├── docs/
│   ├── theory.md           # Topological QC background
│   ├── anyons.md           # Anyon model catalogue
│   ├── api/
│   └── tutorials/
├── tests/
│   ├── unit/
│   ├── integration/
│   └── braid_validation/   # Braid group identity and relation tests
├── config/
│   ├── default.yaml
│   ├── anyon_models.yaml
│   └── logging.yaml
├── .github/workflows/ci.yml
├── CONTRIBUTING.md
└── pyproject.toml
```

---

## Modules & API Surface

### `tql.anyons`

```python
from tql.anyons import IsingAnyon, FibonacciAnyon

# Define anyon model
model = IsingAnyon()
print(model.fusion_rules)    # F-matrices and R-matrices
print(model.quantum_dim)     # √2 for Ising anyons

# Fibonacci anyons (universal for topological QC)
fib = FibonacciAnyon()
print(fib.is_universal)      # True
```

### `tql.braiding`

```python
from tql.braiding import BraidGroup, BraidCompiler

bg   = BraidGroup(n_strands=4)
braid = bg.word(["+1", "-2", "+1"])   # σ₁ σ₂⁻¹ σ₁
U    = braid.to_unitary(model=FibonacciAnyon())

compiler = BraidCompiler(model=FibonacciAnyon())
braid    = compiler.compile_gate(target_unitary=U_T, epsilon=1e-4)
```

### `tql.codes`

```python
from tql.codes import SurfaceCode, ToricCode

# Distance-5 surface code
sc  = SurfaceCode(distance=5)
syn = sc.syndrome(error_pattern)    # Stabilizer measurements
cor = sc.decode(syn)                 # MWPM decoder
print(f"Logical error rate: {sc.logical_error_rate(p=0.01):.4e}")
```

### `tql.simulation`

```python
from tql.simulation import AnyonicSystem

sys = AnyonicSystem(model=IsingAnyon(), n_anyons=4)
sys.create_pair(0, 1)
sys.braid(1, 2)
result = sys.measure_topological_charge(0, 1)
```

---

## Installation

```bash
git clone https://github.com/GALACTIC-UNION/topological-qubit-library.git
cd topological-qubit-library
pip install -e ".[dev]"
```

---

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

MIT — see [LICENSE](LICENSE).
