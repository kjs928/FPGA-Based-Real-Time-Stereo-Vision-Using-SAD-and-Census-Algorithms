# FPGA-Based Real-Time Stereo Vision (SAD & Census)

## 📌 프로젝트 요약

| 항목 | 내용 |
|------|------|
| 프로젝트 명 | FPGA 기반 SAD 및 Census 알고리즘을 활용한 실시간 Stereo Vision |
| 수행 목표 | SAD/Census 알고리즘을 HW로 구현하여 실시간 거리 인식 |
| 수행 기간 | 2025.05.28 ~ 2025.06.13 |
| 담당 역할 | SAD 알고리즘 설계 및 구현 |
| 사용 기술 | Verilog/SystemVerilog, Vivado |

---

## 프로젝트 개요

본 프로젝트는 **FPGA 기반 Stereo Vision 시스템**을 구현하여 **실시간 거리 측정**을 목표로 하였습니다.  
두 대의 OV7670 카메라를 통해 입력받은 영상을 Basys3 FPGA에서 처리하고, VGA 디스플레이로 출력합니다.  

- **SAD (Sum of Absolute Differences)**  
  - 3×3 → 3×1 윈도우 구조 최적화  
  - FSM 기반 구조 설계  
  - Texture threshold & penalty 누적 기법 적용 (노이즈 억제)

- **Census Transform**  
  - 주변 픽셀과 중심 픽셀 비교 → 이진 벡터 생성  
  - Hamming 거리 기반 매칭  
  - 3×15 윈도우 확장으로 정합 정확도 향상  

- **VGA 영상 처리**  
  - H-Sync, V-Sync, blanking 영역 처리  
  - 100MHz → 25MHz pixel clock 분주  
  - SCCB 제어를 통한 카메라 레지스터 설정  

---

## 핵심 성과

- **리소스 제약 극복**  
  - 3×3 SAD 구조 → 3×1 윈도우 단순화로 자원 소모 감소  
  - FSM 파이프라인 최적화 → 합성 성공 및 실시간 처리 확보  

- **정합 성능 개선**  
  - Texture threshold 및 penalty 누적 구조 → 노이즈 감소  
  - Census 기반 보완 → 경계/저텍스처 영역에서 정확도 향상  

- **시스템적 이해 확장**  
  - Camera → FPGA → VGA 전체 파이프라인 구성  
  - 영상 처리와 하드웨어 제약 간 트레이드오프 체득  

---

## 프로젝트 결과 영상

👉 [시연 영상 보기](Video_793dc3ae-c954-4861-885a-141a8696a06e.mp4)  

![Stereo Vision Demo](fd7f7e2c-7557-4188-88b4-36cb0fe70471.gif)

---

## 시스템 구조도

![Block Diagram](47349e58-319f-42b4-bb70-d6bce97f0942:image.png)

---

## 배운 점 & 고찰

- 단순한 알고리즘 구현을 넘어 **FPGA 리소스, 타이밍, 정확도 간 트레이드오프**를 직접 경험  
- VGA 타이밍 제어, Camera 입력 처리, FSM 기반 SAD 최적화 등 **시스템 레벨 설계 역량 강화**  
- 실시간 영상 처리 시스템의 **하드웨어 구현 경험**을 확보  
