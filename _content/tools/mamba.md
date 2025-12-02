---
layout: page
title: 패키지 관리 프로그램: conda와 mamba
description: >
  Python 패키지 관리 도구인 conda와 mamba의 특징 및 사용법 소개.
hide_description: false
sitemap: false
---

# mamba 소개 및 설치 가이드

## 개요: 패키지 관리는 왜 해야 할까?
Python 패키지는 서로 의존성을 갖는다. 그런데 개별 패키지는 구성을 바꾸거나, 함수를 삭제하거나, 기능이 통합되는 등 끊임없이 발전하고, 이는 다른 패키지에서 충돌이 발생하거나 오작동을 일으킨다. 따라서 패키지, 더 크게는 프로젝트마다 사용하는 패키지 버전을 고정해야 안정적으로 실행 환경을 유지할 수 있다.

### `pip`?
PyPI(Python Package Index)에 등록된 순수 Python 패키지는 `pip install`로도 설치할 수 있다. 특히 Ruby나 R 등 다른 언어를 사용하지 않는다면 `pip`만으로 패키지 관리가 가능하다. 하지만 패키지 의존성을 순차적으로 처리하기 때문에 나중에 설치된 패키지가 이전 패키지의 의존성을 망가뜨릴 수 있다. 간단한 환경을 만들 때는 별도의 패키지 관리 프로그램이 없어서 유용하지만, 여러 패키지를 사용하면 패키지 충돌을 경험해서 장기적으로 권장하지 않는다.

## Anaconda vs Miniconda
`conda`는 패키지의 의존성과 버전을 관리하고 설치해주는 대표적인 패키지 관리 프로그램이다. `Anaconda`는 `conda` 뿐 아니라 데이터 과학에 필요한 패키지(700개 이상)가 설치된 프로그램이다. Python에 국한하지 않고 Ruby, R 등 여러 언어의 패키지도 포함하며, 설치할 수도 있다. 따라서 어떤 패키지를 사용할지 모르거나, 버전관리에 익숙하지 않다면 Anaconda로 대부분의 패키지를 설치하여 이런 걱정을 덜 수 있다. 하지만 화학에 특화된 패키지(예: RDKit, pymatgen, ase 등)는 새로 설치해야 하기 때문에 패키지 버전 관리가 필요하다.

`Miniconda`는 Python과 conda만 포함하고 있는 최소한의 버전 관리 프로그램이다. 따라서 직접 패키지를 설치하고 관리해야 한다면 불필요한 패키지들이 없는 `Miniconda`가 좋은 선택지다. 더구나, 불필요한 패키지가 설치되지 않았기 때문에 가볍다.

## Mamba: 더 빠른 패키지 관리 프로그램
나는 요즘 `mamba`를 유용하게 사용하고 있다. mamba는 병렬 다운로드와 C++ 기반 구현으로 conda에 비해 패키지 설치 속도가 빠르다. (conda에 비해 10배 정도 빠르다.)

## mamba 설치

mamba는 `miniforge`를 설치하면 그 안에 포함되어 있다. 아래 절차를 따르자.
1. [Miniforge github 릴리즈 페이지](https://github.com/conda-forge/miniforge/releases/tag/24.11.3-2)
2. 설치 파일을 실행한다.
3. 사용할 터미널에서 `mamba init`으로 mamba를 사용하도록 설정한다. (혹은 mamba terminal을 찾아서 시작 페이지에 등록해둔다.)

### 주의사항
`miniforge`를 설치하면 miniconda와 mamba를 둘 다 사용할 수 있다. 따라서 습관적으로 conda 명령어를 사용할 수도 있다. mamba를 사용하는 습관을 들여서 효율적인 패키지 관리를 해보자.

### mamba 관련 링크
- [mamba 공식 문서](https://mamba.readthedocs.io/)
- [miniforge GitHub 페이지](https://github.com/conda-forge/miniforge)
