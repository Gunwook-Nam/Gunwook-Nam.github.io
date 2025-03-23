---
layout: page
title: 패키지 관리 프로그램: conda와 mamba
description: >
  how to manage Python packages.
hide_description: false
sitemap: false
---

## 개요: 패키지 관리 프로그램
파이썬 패키지는 다른 패키지에 의존성을 갖는다. 개별 패키지는 패키지 구조가 바뀌거나, 함수가 삭제되거나, 기능이 통합되는 등 끊임없이 발전된다. 따라서 패키지마다 더 크게는 프로젝트마다 사용한 패키지의 특정 버전을 고정해야 한다. Anaconda는 패키지의 버전과 의존성을 검증하고 설치해주는 패키지 관리 프로그램이다. 파이썬에 국한된 것이 아니라서 Ruby, R을 포함한 다양한 패키지를 설치할 수 있다.

### `pip install`?
PyPI(Python Package Index)에 등록된 순수 Python 패키지는 pip install로도 설치할 수 있다. 특히 Ruby나 R을 사용하지 않는다면 pip install로 설치하는 것이 편리할 수 있다. 하지만 패키지 의존성을 순차적으로 처리하기 때문에 이후에 설치된 패키지로 인해 이전 패키지들의 의존성이 망가질 수 있다.

## Anaconda vs miniconda
`anaconda`는 데이터 과학에 필요한 패키지(700개 이상)를 포함한다. 어떤 패키지를 사용할지 명확하지 않거나, 버전관리에 익숙하지 않다면 anaconda는 좋은 선택지가 될 수 있다. 하지만 화학에 특화된 패키지(예: RDKit, pymatgen, ase 등)는 새로 설치해야 하기 때문에 패키지 버전 관리에 대한 고민을 anaconda만으로 해결하기는 어렵다.

`miniconda`는 파이썬과 conda만 포함하고 있는 최소한의 버전 관리 프로그램이다. miniconda를 이용해서 직접 패키지를 설치하고 관리하면 불필요한 패키지들을 설치하지 않아도 되며, 새로운 패키지 설치시 기존 패키지와 버전 충돌 여부 등을 확인하지 않아도 된다. 따라서 버전 관리를 위한 좋은 선택지다.

## miniconda vs mamba
요즘 주목하고 있는 패키지 관리 프로그램은 `mamba`이다. mamba는 conda에 비해 패키지 설치 속도가 빠르다. 병렬로 다운로드하며, C++로 구현됐다는 등의 특징이 있으며 여러 테스트는 패키지 설치 속도가 conda에 비해 10배 정도 빠르다고 말한다.

하지만 mamba는 anaconda나 miniconda보다 설치 방식이 친숙하지 않아서 처음에 헤매기 쉽다. 나도 miniconda와 mamba를 같이 설치해서 비효율적으로 사용하고 있었다. 이 글은 mamba 설치 과정을 정리한다.

## mamba 설치
anaconda나 miniconda는 설치하려는 프로그램의 `.exe` 파일을 다운받고 설치하면 되지만, (Windows 기준) mamba는 `miniforge`를 설치해야 한다.
아래 링크는 miniforge 설치 파일을 다운받을 수 있는 github 주소다.
[https://github.com/conda-forge/miniforge/releases/tag/24.11.3-2]

설치하면 miniconda와 mamba를 사용할 수 있다. 반대로 말하면 나도 모르게 conda 명령어를 사용할 수도 있으니, 헷갈리지말고 mamba를 사용하는 습관을 들여보자.