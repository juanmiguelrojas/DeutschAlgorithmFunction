# 🔬 Algoritmos de Deutsch y Deutsch-Jozsa

Implementación completa de los algoritmos de Deutsch y Deutsch-Jozsa usando **Qiskit** y simulación en **IBM Quantum Computer (AerSimulator)**.

---

## 📋 Descripción

Este repositorio contiene la implementación y análisis de dos algoritmos fundamentales de la computación cuántica:

- **Algoritmo de Deutsch**: Determina si una función $f: \{0,1\} \rightarrow \{0,1\}$ es constante o balanceada con **una sola consulta cuántica**, mientras que clásicamente se requieren dos.
- **Algoritmo de Deutsch-Jozsa**: Generalización del algoritmo anterior para funciones $f: \{0,1\}^n \rightarrow \{0,1\}$, demostrando una ventaja exponencial sobre cualquier algoritmo clásico.

---

## 📁 Contenido del Repositorio

```
DeutschAlgorithmFunction/
│
├── DeutschAlgorithmFunction.ipynb   # Notebook principal con toda la implementación
├── deutsch_resultados.png           # Histogramas del Algoritmo de Deutsch (4 funciones)
├── deutsch_jozsa_resultados.png     # Histogramas del Algoritmo de Deutsch-Jozsa (3 funciones)
└── README.md                        # Este archivo
```

---

## 🧪 Experimentos Implementados

### Parte 1 — Algoritmo de Deutsch

| Función | f(0) | f(1) | Tipo | Resultado | Clasificación |
|---------|------|------|------|-----------|---------------|
| Constante Cero | 0 | 0 | Constante | `0` (100%) | ✅ Constante |
| Constante Uno | 1 | 1 | Constante | `0` (100%) | ✅ Constante |
| Identidad Balanceada | 0 | 1 | Balanceada | `1` (100%) | ✅ Balanceada |
| NOT Balanceada | 1 | 0 | Balanceada | `1` (100%) | ✅ Balanceada |

### Parte 2 — Algoritmo de Deutsch-Jozsa (3 qubits)

| Función | Definición | Tipo | Resultado | Clasificación |
|---------|-----------|------|-----------|---------------|
| $f_C(x) = 0$ | Siempre 0 | Constante | `000` (100%) | ✅ Constante |
| $f_{B1}(x) = x_0$ | Bit menos significativo | Balanceada | `001` (100%) | ✅ Balanceada |
| $f_{B2}(x) = x_2 \oplus x_1$ | XOR de bits MSB | Balanceada | `110` (100%) | ✅ Balanceada |

---

## ⚙️ Requisitos

```bash
pip install qiskit qiskit-aer matplotlib
```

| Librería | Versión recomendada |
|----------|-------------------|
| `qiskit` | >= 2.0.0 |
| `qiskit-aer` | >= 0.17.0 |
| `matplotlib` | >= 3.5.0 |
| `numpy` | >= 1.21.0 |

---

## 🚀 Cómo Ejecutar

### Opción 1 — Google Colab (recomendado)
Haz clic en el siguiente botón para abrir el notebook directamente en Google Colab:

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/juanmiguelrojas/DeutschAlgorithmFunction/blob/main/DeutschAlgorithmFunction.ipynb)

### Opción 2 — Localmente

```bash
# 1. Clonar el repositorio
git clone https://github.com/juanmiguelrojas/DeutschAlgorithmFunction.git
cd DeutschAlgorithmFunction

# 2. Instalar dependencias
pip install qiskit qiskit-aer matplotlib numpy

# 3. Abrir el notebook
jupyter notebook DeutschAlgorithmFunction.ipynb
```

---

## 🔑 Conceptos Clave

### Phase Kickback
El principio fundamental detrás de ambos algoritmos. Cuando el qubit auxiliar está en el estado $|-\rangle$, el oráculo "patea" una fase hacia los qubits de entrada:

$$U_f |x\rangle |-\rangle = (-1)^{f(x)} |x\rangle |-\rangle$$

### Ventaja Cuántica

| Algoritmo | Consultas clásicas | Consultas cuánticas |
|-----------|-------------------|---------------------|
| Deutsch ($n=1$) | 2 | **1** |
| Deutsch-Jozsa $n=3$ | 5 | **1** |
| Deutsch-Jozsa $n=10$ | 513 | **1** |
| Deutsch-Jozsa $n=n$ | $2^{n-1}+1$ | **1** |

### Regla de Clasificación (Deutsch-Jozsa)

```
Medir |000...0⟩  →  función CONSTANTE
Medir cualquier otro estado  →  función BALANCEADA
```

---

## 📐 Estructura del Circuito

### Algoritmo de Deutsch
```
q0: ─[H]─────[Uf]─[H]─[M]─
q1: ─[X]─[H]─[Uf]─────────
```

### Algoritmo de Deutsch-Jozsa (3 qubits)
```
q0: ─[H]──────[Uf]──[H]─[M]─
q1: ─[H]──���───[Uf]──[H]─[M]─
q2: ─[H]──────[Uf]──[H]─[M]─
q3: ─[X]─[H]──[Uf]──────────
```

---

## 📊 Resultados

Los histogramas generados muestran que:

- ✅ Las **funciones constantes** siempre producen el estado `|0...0⟩` con probabilidad del **100%**
- ✅ Las **funciones balanceadas** siempre producen un estado diferente a `|0...0⟩` con probabilidad del **100%**

Esto confirma la correcta implementación del algoritmo y la ventaja cuántica teórica.

---

## 📚 Referencias

- Deutsch, D. (1985). *Quantum Theory, the Church-Turing Principle and the Universal Quantum Computer*. Proceedings of the Royal Society of London.
- Deutsch, D. & Jozsa, R. (1992). *Rapid Solution of Problems by Quantum Computation*. Proceedings of the Royal Society of London.
- [Qiskit Documentation](https://docs.quantum.ibm.com/)
- [IBM Quantum](https://quantum.ibm.com/)

---

## 👨‍💻 Autor

**Juan Miguel Rojas**
- GitHub: [@juanmiguelrojas](https://github.com/juanmiguelrojas)

---

> *"La computación cuántica no es simplemente más rápida — es fundamentalmente diferente en la manera en que procesa la información."*
> — **David Deutsch**, 1985