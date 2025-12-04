---
layout: page
title: Unix Shell
description: >
  Unix Shell의 종류와 스크립트의 실행
hide_description: false
sitemap: false
---

# Unix Shell과 Script

## 1. Unix Shell

Unix는 1969년 AT&T Bell Labs에서 Ken Thompson이 개발했다. 이 시기에는 소프트웨어를 판매할 수 없어서 1973년에는 교육기관에 거의 무료로 라이선스를 발급하고 소스코드도 제공했다. Berkeley 대학은 교육, 연구 목적 프로그램을 Unix에 추가하여 BSD(Berkeley Software Distribution) Unix를 개발했다.

Unix는 운영체제로서, 하드웨어를 조작하는 커널이 핵심이다. 프로그램은 커널과 연결되어 사용자의 입력에 따라 하드웨어를 조작한다. Shell은 프로그램 중 하나로, 사용자의 문자열 입력을 다른 프로그램 실행으로 연결한다. Shell이 발전함에 따라 자체 프로그래밍 구조(조건, 반복, 함수)를 갖거나, 프로그램을 실행하기 위한 환경 설정(PATH 등)이 포함됐다.

Unix shell은 AT&T Bell Lab이 개발한 **Bourne Shell (sh)** 계열과 Berkeley에서 개발한 **C Shell (csh)** 계열로 나뉜다. 두 계열은 문법이 서로 달라 호환이 안 되며, 필요에 따라 기능이 추가되며 발전했다. 시간에 따라 `sh`(1979), `csh`(1978) - `tcsh`(1981) - `bash`(1989) - `zsh`(1990)

### 1세대 Shell - 1970년대 말

#### Thompson Shell

1969년 AT&T Bell Labs에서 Ken Thompson이 개발한 Unix에 최초로 도입된 Shell. Unix에서 명령어를 실행하기 위한 목적으로 개발되어 편의성은 부족하지만, Shell의 개념을 최초로 제시했다는 점에 의의가 있다.

#### Bourne Shell (`sh`)

<img src="/assets/img/the_bourne_legacy.jpg" alt="Bourne Legacy" style="max-width: 300px; margin: 1rem 0;">

1979년 AT&T Bell Labs은 완성형인 Version 7 Unix를 발표하며 스티븐 본(Stephen Bourne)이 개발한 Bourne Shell을 탑재했다. (논문은 1978년에 "The UNIX Shell"로 발표) Bourne Shell은 Thompson Shell의 단순한 명령어 실행 기능을 넘어, 스크립트 프로그래밍이 가능한 수준으로 기능을 확장하여 Unix 계열의 표준으로 자리잡았고, POSIX 표준이 됐다.

#### C Shell (`csh`)

1978년 Berkeley 대학원생이던 빌 조이(Bill Joy)는 벨 연구소에서 개발한 쉘(Thompson Shell과 Bourn Shell)이 사용자에게 친화적이지 않은 점을 개선하고자 C 언어 문법을 적용한 C shell을 개발했다. C Shell은 명확하게 "대화형 인터페이스(interactive interface)"를 목적으로 하여, 사용자가 입력한 명령어를 기억하는 히스토리나 별칭(alias)을 사용하는 등의 사용자 편의성을 최초로 도입했다.

### 2세대 Shell - 1980년대

#### Tenex C Shell (`tcsh`)

1981년 카네기 멜론 대학의 켄 그리어(Ken Greer)는 타이핑의 번거로움을 줄이고자 TENEX OS의 '명령어 완성' 기능을 쉘에 최초로 추가했다. 이후 개발된 쉘은 모두 이 명령어 완성 기능을 갖는다. 

`csh`를 그대로 유지한 채로 확장했기 때문에, 사실상 csh를 의미한다. 하지만 1990년대 중반 "Csh Programming Considered Harmful"이라는 글에서 csh가 스크립트 언어로 사용하기에 부적하다는 것을 상세히 비판하면서, 대화형 인터페이스는 편리한 `tcsh`를 사용하고 복잡한 스크립트는 `sh`를 사용하는 방식이 유행했다.

### 3세대 Shell - 1980년대 말

#### Bourne Again Shell (`bash`)

리처드 스톨만은 GNU 프로젝트에서 UNIX를 대체할 자유 운영 체제를 만들며, AT&T에 저작권이 있던 `sh`를 대체할 쉘이 필요했다. 1989년 브라이언 폭스(Brian Fox)는 GNU 프로젝트의 일환으로 `bash`를 개발했다. `bash`는 Bourne Shell의 문법을 기반으로 하며, `csh`나 `ksh`의 편리함을 통합했다.

GNU 프로젝트로 개발되었기 때문에 거의 모든 Linux 시스템에는 `bash`가 설치되어 있으며, POSIX 표준을 따른다. Linux가 지배적인 현대에는 사실상 표준 Shell이다.

#### Z Shell (`zsh`)

1990년 프린스턴 대학 학부생인 Paul Falstad는 조교였던 **Z**hong **Sh**ao의 이름을 따서 Z Shell을 개발했다. `zsh`는 POSIX를 기반으로 작성되어 `sh`, `bash`와 호환을 유지했으며 `tcsh`, `ksh`등 여러 UNIX shell의 장점을 통합했다. 게다가 경로 확장, 철자 교정 등의 편리한 기능을 더 추가했다. 현재 macOS의 기본 로그인 쉘로 사용된다.

편의성을 목표로 개발됐기 때문에 편리한 기능이 많다.
- 지능형 자동 완성 : 명령 옵션, 인자, Git 브랜치 등을 문맥에 맞게 제시한다. (예: `git checkout <Tab>` - 브랜치 목록이 메뉴로 표시됨)
- 철자 자동 교정 : 명령어 또는 디렉토리 이름의 오타를 실행 전에 감지하고 수정 여부를 질의한다. (예: `git status` - "zsh: correct 'gti' to 'git' [ynq]?")
- 커스터마이징 : Oh My Zsh 등의 프레임워크로 플러그인과 테마를 쉽게 적용할 수 있고, 프롬프트에 Git 상태, 파이썬 가상 환경을 표시한다.
- 히스토리 공유 : 여러 터미널 세션 간에 실시간으로 명령어 히스토리를 공유하고 업데이트 한다. (창 A에서 친 명령어를 창 B에서 화살표 키로 불러와서 사용)
- 글로빙 : `**`를 사용하여 모든 하위 디렉토리를 포함하여 파일 검색 및 매칭을 할 수 있다. (`ls **/*.log` - 모든 하위 폴더 내 `.log` 파일을 찾음)

---

## 2. 스크립트 실행

쉘에 어떤 이름(`ls`, `python`, `script.sh`)을 입력하면 쉘은 실행 가능한 파일(executable)을 `$PATH`에서 탐색한다. 그리고 해당 이름이 있으면 커널에 실행요청(`execve`)을 보낸다.

스크립트 실행 방식은 **새 프로세스를 만드는지 여부**에 따라 나뉜다.

### Subshell 실행 (`./script.sh`, `bash script.sh`)

- `./script.sh` 또는 `bash script.sh`로 스크립트를 실행하면 현재 쉘이 **자식 프로세스(Subshell)**를 하나 만들고, 그 안에서 스크립트를 실행한다.
- 스크립트가 끝나면 자식 프로세스가 종료된다. 그 동안 부모 쉘의 상태는 그대로 유지된다. 따라서 스크립트 안에서 변수 값을 바꾸거나 `cd`로 디렉토리를 옮겨도, 부모 쉘에는 영향을 주지 않는다.
- 독립적인 작은 프로그램처럼 동작하므로, 일반적인 명령형 스크립트나 배치 작업에 적합하다.

subshell에서 스크립트를 실행할 interpreter를 지정하는 방식은 Shebang에 작성하거나(`./script.sh`), 직접 interpreter를 명시(`bash script.sh`)한다.

#### `./script.sh`

- 스크립트 안에 Shebang으로 커널이 실행할 interpreter를 지정한다. (`#!/bin/bash`, `#!/bin/python`) 이는 이름은 같지만 여러 버전의 interpreter를 사용하는 경우 등에서 유용하다. 현재 쉘, 로그인 쉘과 관계없이 Shebang이 우선한다.

- 커널이 이 파일을 실행하려면 파일에 실행 권한을 먼저 줘야 한다.(`chmod +x script.sh`)

- `.`는 현재 디렉토리로 대부분 `$PATH`에 현재 디렉토리가 등록되어 있지 않아서 명시적으로 입력해야 한다. 따라서 `$PATH`에 등록된 경로라면 `script.sh`만 입력해도 커널에 실행 요청을 보낼 수 있고, 다른 경로에 있는 스크립트도 경로를 명시하면 실행할 수 있다. (`/path/to/script.sh`)

#### `bash script.sh`

- interpreter에 스크립트 파일을 input으로 넣어서 실행한다. 이 interpreter도 `$PATH`에 등록되어 있어야 한다.

- Shebang과 관계없이 실행된다. 예를 들어, 파일 첫 줄이 `#!/bin/tcsh`라도 `bash script.sh`로 실행하면 bash로 실행된다.


### Current Shell 실행 (`source script.sh`, `. script.sh`)

- `source script.sh` 또는 `. script.sh`로 스크립트를 실행하면 자식 프로세스를 만들지 않고, **현재 쉘**에서 스크립트를 실행한다.

- 스크립트 안에서 설정한 환경 변수, `cd`로 변경한 현재 디렉토리 등이 **지금 사용 중인 쉘에 그대로 남는다.**

- 환경 변수를 수정하거나, 쉘의 설정을 적용할 때 적합하다.
  - `conda activate`는 명령어 내부에서 `source`를 사용해서 환경 변수를 설정한다.
  `.bashrc`, `.zshrc`와 같은 설정 파일을 변경 후 적용할 때 사용한다. (`source .bashrc`)

- `source`는 더 포괄적이며 `.`은 POSIX 표준이다.
  - `source`는 `bash, zsh, tcsh` 등 대부분의 shell에서 지원한다.
  
  - `.` (점)은 POSIX 표준이다(`. script.sh`). 따라서 POSIX 대상이 아닌 C Shell(특히 `tcsh`)은 반드시 `source`를 사용해야 한다.

  - `sh`처럼 최소한의 기능만 가진 쉘에서는 `source`가 없고, `.`만 사용할 수 있다.

| 구분 | Bourne Shell (`bash`, `zsh`) | C Shell (`tcsh`) |
| :--- | :--- | :--- |
| Shebang | `#!/bin/bash`, `#!/usr/bin/env bash` | `#!/bin/tcsh` |
| 환경 변수 | `export VAR=val` | `setenv VAR val` |
| 설정 파일 반영 | `source file`, `. file` | `source file` |
| 대표 사용 맥락 | 리눅스/맥 기본 쉘, 일반 연구 및 서버 | 계산 화학 및 유닉스 스크립트 |

---

## 3. Shebang (`#!`)

스크립트 파일의 첫 줄에 작성하는 `#!/bin/bash`와 같은 코드를 **Shebang**이라고 한다.

### Shebang의 역할

Shebang은 커널에게 새 프로세스를 만들고 어느 인터프리터로 실행해야 하는지를 알려준다. 따라서 사용자가 `./script.sh` 명령어로 Subshell에서 스크립트를 실행할 수 있다.

구체적으로 스크립트를 실행하면 다음 과정을 거친다.

- 실행 요청이 들어오면 커널이 첫 줄을 읽어 `#!` 뒤의 경로(예: `/bin/bash`)를 해석한다.

- 해당 프로그램을 새 프로세스로 실행하고, 스크립트 파일의 나머지 내용을 그 프로그램의 입력으로 넘긴다.


### 예시

- `#!/bin/bash`
  - 리눅스 환경에서 가장 흔하게 사용하는 형태다.
  - 시스템에 설치된 기본 `bash`를 사용하므로, 대부분의 배포판에서 동일하게 동작한다. 이를 이용해서 리눅스 표준을 정할 수 있다.

- `#!/bin/tcsh`
  - 스크립트를 `tcsh` 문법으로 해석하도록 강제한다. 따라서 로그인 쉘은 `bash`/`zsh`라 하더라도, 이 스크립트는 `tcsh` 규칙을 따른다.

- `#!/usr/bin/env python`
  - `PATH` 환경 변수에서 `python` 실행 파일을 찾아 사용한다.

- `#!/home/gunwook/.conda/envs/gw312/bin/python`
  - conda 가상환경을 지정하여 파이썬을 사용한다.


### 주의할 점

- 스크립트가 다양한 시스템에서 사용될 가능성이 있다면, 존재 여부가 불확실한 경로(`/usr/local/bin/...` 등)를 사용하지 않는게 좋다.

- 파이썬, 루비처럼 여러 버전이 있는 언어는 버전을 명시하는 것이 안전하다. (`#!/usr/bin/env python3`과 `#!/usr/bin/env python`이 모두 존재하기 때문)

- 파일 인코딩이나 줄 끝 형식(CRLF vs LF)이 잘못되어 Shebang 줄 앞에 보이지 않는 문자가 들어가면, 커널이 Shebang을 제대로 인식하지 못할 수 있다.


## POSIX 표준과 호환성

**POSIX(Portable Operating System Interface)**는 Unix 계열 운영체제에서 공통으로 지켜야 할 최소한의 규칙을 정해 둔 표준이다.

### POSIX와 `sh` 문법

- `bash`와 `zsh`는 POSIX에서 정의한 `sh` 문법을 포함한다. 따라서 POSIX 문법만 사용하면, Bourne-type Shell (`bash`, `zsh`, `/bin/sh`) 중 어느 것으로 실행해도 동일한 결과를 얻는다. 개인용 스크립트라면 bash, zsh의 고유 기능을 써도 되지만, 여러 서버, 여러 OS에 배포하는 스크립트라면 POSIX 문법만 사용하는 것이 안전하다.

- `tcsh`는 C Shell 계열로, POSIX `sh` 표준의 대상이 아니다. 따라서 `tcsh` 스크립트는 POSIX와 별개의 `tcsh` 전용 스크립트로 봐야 한다. 일반적으로 `tcsh`는 스크립트보다 사용자와 상호작용에 목적과 강점을 갖기 때문에, 스크립트로서 기능은 부족하다.


### 스크립트 작성 가이드라인

#### 여러 환경에 배포되는 공용 스크립트
- Shebang은 `#!/bin/sh`처럼 sh 계열로 지정한다.
- 조건문, 반복문, 변수 치환은 POSIX `sh`에서 정의한 기본 문법만 사용한다.
- 배열, 연관 배열, `[[ ... ]]`, 프로세스 치환(`<()`) 등은 사용하지 않는다.

#### 개인용 스크립트
- Shebang은 `#!/bin/bash`, `#!/bin/zsh`, `#!/bin/tcsh`처럼 실제로 사용하는 쉘을 명시한다.
- 필요한 경우 해당 쉘의 확장 기능을 사용한다. 단, 다른 쉘과의 호환성은 기대할 수 없다.
