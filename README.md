# Split-Beat HE · Hardware

codeki lab의 좌우 분리형 홀 이펙트 리듬게임 컨트롤러입니다. C86 4층 PCB는 좌우 각각 Hall 입력 7개와 기계식 입력·인코더를 지원합니다.

## 한 세트 주문

1. [PCB 제작 자료](manufacturing/pcb)의 Gerber/드릴 ZIP, BOM, CPL을 업로드합니다. 한 패널에 왼쪽과 오른쪽 각 1장이 들어 있습니다. 업체의 최소 수량과 실장 후 분리 옵션을 확인하세요.
2. 4층 1.6mm급, ENIG, 신호–GND–GND–신호 구성으로 견적을 받습니다. 제작 전 USB HS 차동 90Ω 목표와 공장 적층을 대조하고, **R609 한 자리만 미실장**과 하단 SWD 직각 헤더의 **긴 핀이 기판 안쪽**을 향하는지 확인합니다. KiCad 원본에 R609 패드가 남아 있습니다. CPL의 좌우 수직 노브 인코더와 SWD 헤더를 공장 DFM에서 확인하고, 수평 휠 TTC 엔코더는 별도로 구매해 직접 납땜합니다.
3. 알루미늄 5052 1.5mm [실제 조립 판](manufacturing/plates/as-built)을 상판 좌우·하판 좌우 각 1장 주문합니다. 상판은 은색 무광 아노다이징, 하판은 무처리로 제작했습니다. 상·하판 외곽을 맞춘 [수정 후보](manufacturing/plates/fit-candidate)는 실제 출력·조립 확인이 남아 있습니다.
4. [수평 휠 저장소](https://github.com/CodeKi0303/split-beat-he-wheel)에서 휠과 지지부, MR83ZZ 베어링, TTC Gold 엔코더 규격을 확인합니다. 수직 노브용 [베젤](manufacturing/knob-bezels), 스위치와 키캡, 나사·절연 와셔·스페이서도 준비합니다.

제작 묶음은 원본 업로드 자료의 공개용 복사본입니다. 공장 내부 CAM·견적·주문 화면과 계정 자료는 별도로 관리합니다. [PCB 제작 메모](manufacturing/pcb/README.md)에서 패널 분리와 실장 조건을 확인하세요.

## 조립과 사용

- [나사 체결 단면도](docs/fastener-assembly-sections.svg)의 A/B/C 위치를 기준으로 조립합니다. USB 개구부, 납땜 핀과 하판의 간격, 휠이 자유롭게 도는지 확인합니다.
- 새 보드는 [펌웨어의 SWD 초기 설치](https://github.com/CodeKi0303/split-beat-he-firmware/blob/main/C86-FIRST-FLASH.md)를 진행합니다.
- **PC → 왼쪽 PC용 USB-C**, **왼쪽 split 포트 → 오른쪽 split 포트** 순으로 연결합니다. 오른쪽 USB-C는 좌우 통신·전원용입니다. [Studio](https://studio.codekilab.com/)에서 캘리브레이션, 매핑, 작동점 및 Rapid Trigger를 설정합니다. [Studio 소스와 로컬 실행](https://github.com/CodeKi0303/split-beat-he-studio).

## 휠 가져오기

```sh
git clone --recurse-submodules https://github.com/CodeKi0303/split-beat-he-hardware.git
```

이미 내려받았다면 `git submodule update --init`으로 `modules/horizontal-wheel`을 받습니다. 서브모듈이 이 설계에 맞춰 검토한 휠 커밋을 고정합니다.

직접 만든 설계는 [CERN-OHL-P-2.0](LICENSE)입니다. `pcb/board/pcb-libs/`의 외부 풋프린트 고지는 해당 디렉터리에 보존합니다. 프로젝트 이력은 [codeki lab](https://codekilab.com/#keyboard-project)에서 볼 수 있습니다.
