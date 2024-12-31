
# PNG-to-PDF Splitter (A3 비율 지원)

이 어플리케이션은 세로로 긴 PNG(또는 다른 이미지)를 여러 페이지로 분할한 뒤, 각 이미지를 A3 비율(약 297:420)에 맞춰 하단에만 여백을 추가하고, 마지막으로 이 페이지들을 단일 PDF 파일로 내보냅니다.

## 주요 특징

- **자동 A3 선**  
  - 이미지를 열면 A3 비율(297:420 ≈ 0.707)에 따라 자동으로 빨간색 가로선을 일정 간격으로 생성합니다.
- **드래그 가능한 선**  
  - 생성된 빨간 선을 마우스로 위아래로 드래그하여 분할 지점을 조절할 수 있습니다.
- **추가 선(“Add Line”) 기능**  
  - 툴바에서 “Add Line”을 클릭하면, 현재 뷰 중앙(화면 중앙)에 빨간색 선이 추가되며, 이를 다시 드래그하여 위치를 조정할 수 있습니다.
- **하단 여백 패딩**  
  - 이미지를 분할한 뒤, 각 조각을 A3 비율에 맞추어 **하단**에만 흰색 여백을 추가합니다.
- **단일 PDF 출력**  
  - 조각난 이미지를 하나의 PDF 파일로 합쳐서 내보낼 수 있습니다.

## 요구 사항

- Python 3.x 이상
- 다음 Python 라이브러리:
  - **PyQt5**
  - **Pillow**
  - **img2pdf**

아래 명령어로 한 번에 설치할 수 있습니다.

```
pip install -r requirements.txt
```

*(PyQt5 대신 PyQt6 등 다른 버전을 사용할 수도 있으니, 환경에 맞춰 조정하세요.)*

## 설치 및 실행 방법

1. **프로젝트 폴더**(예: `my_png_splitter/`)를 다운로드 혹은 클론 받습니다.
2. 폴더 안에 다음 파일들이 있어야 합니다.
   - `main.py` (메인 실행 스크립트)
   - `requirements.txt` (의존 라이브러리 목록)
3. (선택 사항) 가상 환경을 생성 및 활성화합니다.
   ```bash
   python -m venv splitter
   source splitter/bin/activate    # Mac/Linux
   splitter\Scripts\activate       # Windows
   ```
4. **의존 라이브러리 설치**  
   ```bash
   pip install -r requirements.txt
   ```
5. **실행**  
   ```bash
   python main.py
   ```
   실행하면 GUI 창이 뜨고, 이미지 열기·분할·PDF 저장이 가능합니다.

## 사용 방법

1. **이미지 열기**  
   - 상단 툴바의 **Open** 버튼을 클릭합니다.  
   - 긴 PNG나 JPEG 이미지를 선택하면, 화면에 표시됩니다.  
   - 자동으로 A3 간격에 맞춰 빨간색 가로선들이 생성됩니다.

2. **선 조정 / 추가**  
   - 이미 생성된 빨간 선을 **마우스로 드래그**해 위아래로 옮길 수 있습니다.  
   - **“Add Line”** 버튼을 클릭하면, 현재 화면(뷰)의 중앙에 새 빨간 선이 하나 추가됩니다.  
     그 선 역시 드래그하여 원하는 위치로 이동 가능합니다.

3. **PDF로 내보내기**  
   - 상단 툴바의 **Save PDF** 버튼을 클릭합니다.  
   - 파일 이름과 위치를 지정하면,  
     1. 씬에 있는 모든 빨간 선의 y좌표를 수집하여 이미지를 분할  
     2. 각 조각 이미지를 A3 비율로 맞도록 하단에만 여백을 추가  
     3. 모든 조각을 하나의 PDF 파일로 병합  
   - 작업이 완료되면 완료 메시지가 표시됩니다.

4. **출력 확인**  
   - 저장된 PDF를 열어보면,  
     - 여러 페이지로 구성된 PDF가 생성되어 있으며,  
     - 각 페이지는 A3 비율 크기의 흰 바탕에 원본 이미지 조각이 상단 정렬되어 들어가게 됩니다.

## 참고 사항

- **DPI(해상도) 조정**  
  - 실제 인쇄 시 300 DPI 이상을 요구하는 경우가 많습니다.  
  - 코드에서 픽셀 크기나 비율을 세밀하게 조정해야 할 수 있습니다.
- **메모리 사용**  
  - 초고해상도 이미지를 다룰 경우, 분할·패딩 과정에서 메모리를 많이 사용할 수 있습니다.
- **OS/환경별 차이**  
  - PyQt5 설치 시, Windows/Mac/Linux 별로 패키지가 다를 수 있으므로 환경에 맞게 설치하세요.
