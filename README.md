<!-- Improved compatibility of back to top link: See: https://github.com/othneildrew/Best-README-Template/pull/73 -->
<a name="readme-top"></a>

<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
-->
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

<!-- PROJECT LOGO -->
<br />
<div align="center">
  <!-- <a href="https://github.com/marcotallone/latex">
    <img src="images/colilogo.png" alt="Logo" width="80" height="80">
  </a> -->

<h3 align="center">Modeling of MPI Collective Operations</h3>

  <p align="center">
    A case study of the MPI Broadcast and MPI Reduce collective operations.
    <br />
    <a href="https://github.com/marcotallone/collective-operations-latency"><strong>Explore the docs »</strong></a>
    <br>
    <a href="./mpi-collective-op-marco-tallone.pdf"><strong>Read the official report »</strong></a>
    <br />
    <br />
    <a href="./apps/example.py">View Demo</a>
    ·
    <a href="https://github.com/marcotallone/collective-operations-latency/issues">Report Bug</a>
    ·
    <a href="https://github.com/marcotallone/collective-operations-latency/issues">Request Feature</a>
  </p>
</div>

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#references">References</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>

<!-- ABOUT THE PROJECT -->
## About The Project

<!-- [![Product Name Screen Shot][product-screenshot]](https://example.com) -->

This repository contains collected data and analysis of the latencies for the `MPI_Bcast` and `MPI_Reduce` collective operations. This study has been conducted as part of the final exam for the High Performance Computing (HPC) corse held at the University of Trieste (**U**ni**TS**) during the academic year 2023-2024.\
The data have been mainly collected on `EPYC` nodes on the **ORFEO** cluster at AREA Science Park, Basovizza (TS) in January/February 2024 using the well known `OSU` benchmark and are available in the `datasets/` folder. These nodes are equipped with AMD EPYC 7H12 (Rome) processors.\
More in depth informations and further details are available in the [attached report](./mpi-collective-op-marco-tallone.pdf) you can find in this repository.\
This repository also contains a `Python` package named `epyc` containing a small simulative model for `EPYC` nodes that has been used to conduct the necessary computations for the analysis.
The module is essentially a collection of classes and methods that allows the user to simulate MPI core allocation on a real `EPYC` machine. The module, in fact, allows to create `Node` objects and to initialize a certain number of processes on them according to different mapping policies, as done by the `map-by` option of the `mpirun` command of the MPI library.\
The module is also able to simulate the latency of the `MPI_Broadcast` and `MPI_Reduce` collective operations on the `EPYC` nodes, using the data collected on the **ORFEO** cluster. The latency is predicted based on a point-to-point communication model. Once more, further details on the model are available on the report in this repository. The data have been collected through the submission of several jobs that can be found in the `jobs/` folder.\
The module also offers few utility functions to plot and to perform statistical analysis on the collected data collected for the latencies.\
The majority of the implemented functions and classes are documented, hence further info about inputs and usage can be obtained with the `help` function in Python.\
Some usage examples can be found in the `apps/` folder or in the Jupiter notebooks in the `notebooks/` folder.

### Built With

![C](https://img.shields.io/badge/C-CBF9DA?style=for-the-badge&logo=c&logoColor=darkblue)
![Python](https://img.shields.io/badge/Python-3DD2CC?style=for-the-badge&logo=python&logoColor=white)
![NeoVim](https://img.shields.io/badge/NeoVim-3E6B89?style=for-the-badge&logo=neovim&logoColor=white)
![Bash](https://img.shields.io/badge/Bash-122D42?style=for-the-badge&logo=gnu-bash&logoColor=white)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- GETTING STARTED -->
## Getting Started

If you want to use the implemented `epyc` module you can follow these steps. It is anyway recommended to take a look at the scripts in the `apps/` folder for eventual [usage examples](./apps/example.py).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Prerequisites

Prerequisites needed to repeat the measurements and the data analysis:

* `Python 3.10` or higher
* `OSU MPI Benchmarks` installed on the target machine (version 7.3)
* `OpenMPI` library installed on the target machine
* Access to **ORFEO** cluster or any equivalent HPC platform with **SLURM** scheduler

### Installation

The module comes with a `setup.py` file in the root directory, hence it can be installed with the following command:

```bash
pip install -e .
```

from the root directory of the project.
After that, the module can be imported in any Python script or notebook with the following command:

```python
import epyc
```

Or, alternatively to also use the utilities functions one can import:

```python
from epyc import *
from utils import *
```

Alternatively the modules can be used by manually updating the `PYTHONPATH` environment before running the scripts or notebooks.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Usage

The `example.py` script in the `apps/` folder contains some [usage examples](apps/example.py) of the implemented classes and methods. The script can be run with the following command:

```bash
python apps/examples.py
```

from the root directory. Running the script will produce the following output:

```terminal
Now these nodes are empty:

Node 0:
┌──────────────────┐  ┌──────────────────┐
│ ⬛⬛⬛⬛⬛⬛⬛⬛ │  │ ⬛⬛⬛⬛⬛⬛⬛⬛ │
│ ⬛⬛⬛⬛⬛⬛⬛⬛ │  │ ⬛⬛⬛⬛⬛⬛⬛⬛ │
│ ⬛⬛⬛⬛⬛⬛⬛⬛ │  │ ⬛⬛⬛⬛⬛⬛⬛⬛ │
│ ⬛⬛⬛⬛⬛⬛⬛⬛ │  │ ⬛⬛⬛⬛⬛⬛⬛⬛ │
│ ⬛⬛⬛⬛⬛⬛⬛⬛ │  │ ⬛⬛⬛⬛⬛⬛⬛⬛ │
│ ⬛⬛⬛⬛⬛⬛⬛⬛ │  │ ⬛⬛⬛⬛⬛⬛⬛⬛ │
│ ⬛⬛⬛⬛⬛⬛⬛⬛ │  │ ⬛⬛⬛⬛⬛⬛⬛⬛ │
│ ⬛⬛⬛⬛⬛⬛⬛⬛ │  │ ⬛⬛⬛⬛⬛⬛⬛⬛ │
└──────────────────┘  └──────────────────┘

Node 1:
┌──────────────────┐  ┌──────────────────┐
│ ⬛⬛⬛⬛⬛⬛⬛⬛ │  │ ⬛⬛⬛⬛⬛⬛⬛⬛ │
│ ⬛⬛⬛⬛⬛⬛⬛⬛ │  │ ⬛⬛⬛⬛⬛⬛⬛⬛ │
│ ⬛⬛⬛⬛⬛⬛⬛⬛ │  │ ⬛⬛⬛⬛⬛⬛⬛⬛ │
│ ⬛⬛⬛⬛⬛⬛⬛⬛ │  │ ⬛⬛⬛⬛⬛⬛⬛⬛ │
│ ⬛⬛⬛⬛⬛⬛⬛⬛ │  │ ⬛⬛⬛⬛⬛⬛⬛⬛ │
│ ⬛⬛⬛⬛⬛⬛⬛⬛ │  │ ⬛⬛⬛⬛⬛⬛⬛⬛ │
│ ⬛⬛⬛⬛⬛⬛⬛⬛ │  │ ⬛⬛⬛⬛⬛⬛⬛⬛ │
│ ⬛⬛⬛⬛⬛⬛⬛⬛ │  │ ⬛⬛⬛⬛⬛⬛⬛⬛ │
└──────────────────┘  └──────────────────┘
Now we initialize the nodes with 2 processes each and mapby node:

Node 0:
┌──────────────────┐  ┌──────────────────┐
│ ✅⬛⬛⬛⬛⬛⬛⬛ │  │ ⬛⬛⬛⬛⬛⬛⬛⬛ │
│ ⬛⬛⬛⬛⬛⬛⬛⬛ │  │ ⬛⬛⬛⬛⬛⬛⬛⬛ │
│ ⬛⬛⬛⬛⬛⬛⬛⬛ │  │ ⬛⬛⬛⬛⬛⬛⬛⬛ │
│ ⬛⬛⬛⬛⬛⬛⬛⬛ │  │ ⬛⬛⬛⬛⬛⬛⬛⬛ │
│ ⬛⬛⬛⬛⬛⬛⬛⬛ │  │ ⬛⬛⬛⬛⬛⬛⬛⬛ │
│ ⬛⬛⬛⬛⬛⬛⬛⬛ │  │ ⬛⬛⬛⬛⬛⬛⬛⬛ │
│ ⬛⬛⬛⬛⬛⬛⬛⬛ │  │ ⬛⬛⬛⬛⬛⬛⬛⬛ │
│ ⬛⬛⬛⬛⬛⬛⬛⬛ │  │ ⬛⬛⬛⬛⬛⬛⬛⬛ │
└──────────────────┘  └──────────────────┘

Node 1:
┌──────────────────┐  ┌──────────────────┐
│ ✅⬛⬛⬛⬛⬛⬛⬛ │  │ ⬛⬛⬛⬛⬛⬛⬛⬛ │
│ ⬛⬛⬛⬛⬛⬛⬛⬛ │  │ ⬛⬛⬛⬛⬛⬛⬛⬛ │
│ ⬛⬛⬛⬛⬛⬛⬛⬛ │  │ ⬛⬛⬛⬛⬛⬛⬛⬛ │
│ ⬛⬛⬛⬛⬛⬛⬛⬛ │  │ ⬛⬛⬛⬛⬛⬛⬛⬛ │
│ ⬛⬛⬛⬛⬛⬛⬛⬛ │  │ ⬛⬛⬛⬛⬛⬛⬛⬛ │
│ ⬛⬛⬛⬛⬛⬛⬛⬛ │  │ ⬛⬛⬛⬛⬛⬛⬛⬛ │
│ ⬛⬛⬛⬛⬛⬛⬛⬛ │  │ ⬛⬛⬛⬛⬛⬛⬛⬛ │
│ ⬛⬛⬛⬛⬛⬛⬛⬛ │  │ ⬛⬛⬛⬛⬛⬛⬛⬛ │
└──────────────────┘  └──────────────────┘
Now we re-allocate the processes with socket mapping and going up to 132 processes
Let's see where each process is:

Node 0:
┌─────────────────────────────────┐  ┌─────────────────────────────────┐
│   0   2   4   6   8  10  12  14 │  │   1   3   5   7   9  11  13  15 │
│  16  18  20  22  24  26  28  30 │  │  17  19  21  23  25  27  29  31 │
│  32  34  36  38  40  42  44  46 │  │  33  35  37  39  41  43  45  47 │
│  48  50  52  54  56  58  60  62 │  │  49  51  53  55  57  59  61  63 │
│  64  66  68  70  72  74  76  78 │  │  65  67  69  71  73  75  77  79 │
│  80  82  84  86  88  90  92  94 │  │  81  83  85  87  89  91  93  95 │
│  96  98 100 102 104 106 108 110 │  │  97  99 101 103 105 107 109 111 │
│ 112 114 116 118 120 122 124 126 │  │ 113 115 117 119 121 123 125 127 │
└─────────────────────────────────┘  └─────────────────────────────────┘

Node 1:
┌─────────────────────────────────┐  ┌─────────────────────────────────┐
│ 128 130                         │  │ 129 131                         │
│                                 │  │                                 │
│                                 │  │                                 │
│                                 │  │                                 │
│                                 │  │                                 │
│                                 │  │                                 │
│                                 │  │                                 │
│                                 │  │                                 │
└─────────────────────────────────┘  └─────────────────────────────────┘
We now re-allocated the node filling them completely with 256 processes and mapby core
In fact here is their status:

Node 0:
┌──────────────────┐  ┌──────────────────┐
│ ✅✅✅✅✅✅✅✅ │  │ ✅✅✅✅✅✅✅✅ │
│ ✅✅✅✅✅✅✅✅ │  │ ✅✅✅✅✅✅✅✅ │
│ ✅✅✅✅✅✅✅✅ │  │ ✅✅✅✅✅✅✅✅ │
│ ✅✅✅✅✅✅✅✅ │  │ ✅✅✅✅✅✅✅✅ │
│ ✅✅✅✅✅✅✅✅ │  │ ✅✅✅✅✅✅✅✅ │
│ ✅✅✅✅✅✅✅✅ │  │ ✅✅✅✅✅✅✅✅ │
│ ✅✅✅✅✅✅✅✅ │  │ ✅✅✅✅✅✅✅✅ │
│ ✅✅✅✅✅✅✅✅ │  │ ✅✅✅✅✅✅✅✅ │
└──────────────────┘  └──────────────────┘
Active cores:	128 / 128
Empty cores:	0 /128
Active sockets:	2 / 2
Empty sockets:	0 / 2

Node 1:
┌──────────────────┐  ┌──────────────────┐
│ ✅✅✅✅✅✅✅✅ │  │ ✅✅✅✅✅✅✅✅ │
│ ✅✅✅✅✅✅✅✅ │  │ ✅✅✅✅✅✅✅✅ │
│ ✅✅✅✅✅✅✅✅ │  │ ✅✅✅✅✅✅✅✅ │
│ ✅✅✅✅✅✅✅✅ │  │ ✅✅✅✅✅✅✅✅ │
│ ✅✅✅✅✅✅✅✅ │  │ ✅✅✅✅✅✅✅✅ │
│ ✅✅✅✅✅✅✅✅ │  │ ✅✅✅✅✅✅✅✅ │
│ ✅✅✅✅✅✅✅✅ │  │ ✅✅✅✅✅✅✅✅ │
│ ✅✅✅✅✅✅✅✅ │  │ ✅✅✅✅✅✅✅✅ │
└──────────────────┘  └──────────────────┘
Active cores:	128 / 128
Empty cores:	0 /128
Active sockets:	2 / 2
Empty sockets:	0 / 2
We can simulate different collective operations seeing their latency, for instance here for a message size of 1B:
	 - linear broadcast latency: 50.573211704623475 us
	 - chain broadcast latency: 55.030291447907615 us
	 - binary broadcast latency: 11.795976127944595 us
	 - linear reduce latency: 0.29013244483611006 us
	 - chain reduce latency: 34.846116497184674 us
	 - binary reduce latency: 1.785089908861254 us
```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE.txt` for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTACT -->
## Contact

| Contact Me | |
| --- | --- |
| Mail | <marcotallone85@gmail.com> |
| LinkedIn | [LinkedIn Page](https://linkedin.com/in/marco-tallone-40312425b) |
| GitHub | [marcotallone](https://github.com/marcotallone) |

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- REFERENCES -->

## References

- [OSU Benchmark](http://mvapich.cse.ohio-state.edu/benchmarks/)
- [MPI Forum](https://www.mpi-forum.org/)
- [AREA Science Park](https://www.area.trieste.it/it/infrastrutture/orfeo)
- [ORFEO Documentation](https://orfeo-doc.areasciencepark.it/)
- [HPC UniTS](https://github.com/Foundations-of-HPC/High-Performance-Computing-2023)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

* [Best-README-Template](https://github.com/othneildrew/Best-README-Template?tab=readme-ov-file)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/marcotallone/collective-operations-latency.svg?style=for-the-badge
[contributors-url]: https://github.com/marcotallone/collective-operations-latency/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/marcotallone/collective-operations-latency.svg?style=for-the-badge
[forks-url]: https://github.com/marcotallone/collective-operations-latency/network/members
[stars-shield]: https://img.shields.io/github/stars/marcotallone/collective-operations-latency.svg?style=for-the-badge
[stars-url]: https://github.com/marcotallone/collective-operations-latency/stargazers
[issues-shield]: https://img.shields.io/github/issues/marcotallone/collective-operations-latency.svg?style=for-the-badge
[issues-url]: https://github.com/marcotallone/collective-operations-latency/issues
[license-shield]: https://img.shields.io/github/license/marcotallone/collective-operations-latency.svg?style=for-the-badge
[license-url]: https://github.com/marcotallone/collective-operations-latency/blob/master/LICENSE
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/marco-tallone-40312425b
[product-screenshot]: images/screenshot.png
[Next.js]: https://img.shields.io/badge/next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white
[Next-url]: https://nextjs.org/
[React.js]: https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB
[React-url]: https://reactjs.org/
[Vue.js]: https://img.shields.io/badge/Vue.js-35495E?style=for-the-badge&logo=vuedotjs&logoColor=4FC08D
[Vue-url]: https://vuejs.org/
[Angular.io]: https://img.shields.io/badge/Angular-DD0031?style=for-the-badge&logo=angular&logoColor=white
[Angular-url]: https://angular.io/
[Svelte.dev]: https://img.shields.io/badge/Svelte-4A4A55?style=for-the-badge&logo=svelte&logoColor=FF3E00
[Svelte-url]: https://svelte.dev/
[Laravel.com]: https://img.shields.io/badge/Laravel-FF2D20?style=for-the-badge&logo=laravel&logoColor=white
[Laravel-url]: https://laravel.com
[Bootstrap.com]: https://img.shields.io/badge/Bootstrap-563D7C?style=for-the-badge&logo=bootstrap&logoColor=white
[Bootstrap-url]: https://getbootstrap.com
[JQuery.com]: https://img.shields.io/badge/jQuery-0769AD?style=for-the-badge&logo=jquery&logoColor=white
[JQuery-url]: https://jquery.com 
