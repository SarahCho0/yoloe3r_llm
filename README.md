# YOLOE3R: Perception-Efficient 3D Reconstruction

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python: 3.8+](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/downloads/)


### Quick Start
#### Install
```bash
conda create --name yoloe3r python=3.10
conda activate yoloe3r
git clone 
pip install requirements.txt
```
#### Usage
```bash
python pe3r_demo.py
```

### Acknowledgements
- [DUSt3R](https://github.com/naver/dust3r) / [MASt3R](https://github.com/naver/mast3r)
- [SAM](https://github.com/facebookresearch/segment-anything) / [SAM2](https://github.com/facebookresearch/sam2) / [MobileSAM](https://github.com/ChaoningZhang/MobileSAM)
- [SigLIP](https://github.com/google-research/big_vision)

### BibTeX
```BibTeX
@article{hu2025pe3r,
  title={PE3R: Perception-Efficient 3D Reconstruction},
  author={Hu, Jie and Wang, Shizun and Wang, Xinchao},
  journal={arXiv preprint arXiv:2503.07507},
  year={2025}
}
```

## 기술 스택

| 분류     | 기술               | 상세                                                                    |
| :---    | :---              | :---                                                                   |
| 언어     | Python            | 모든 스크립트 작성에 사용                                                    |
| AI 모델  | Google Gemini API | `gemini-2.5-flash` (리포트 분석), `gemini-2.5-flash-image` (이미지 생성/수정) |
| 라이브러리 | `google-genai`    | Gemini 모델과의 통신                                                       |
| 라이브러리 | `Pillow`          | 이미지 로드 및 저장 등 기본 처리                                               |


:-----------

## 자세한 설치 및 실행 방법

1. 코드 다운로드 및 환경 설정
터미널을 열고 저장소를 클론한 후, 필요한 패키지를 설치합니다.

```Bash
# 1-1. 저장소 클론 (URL을 실제 저장소 주소로 변경하세요)
git clone https://github.com/SarahCho0/yoloe3r.git
cd "내가 만든 파일이름"
# 1-2. 의존성 설치
pip install -r requirements.txt
```

2. 환경 설정 
config.py 파일을 열어 Google GenAI API 키와 초기 입력 이미지 경로를 설정해야 합니다.

```Python
# config.py
API_KEY = "YOUR_GOOGLE_GENAI_API_KEY_HERE"# 3장의 최초 입력 이미지 경로를 실제 경로로 변경하세요.
INITIAL_IMAGE_PATHS = [
    "path/to/your/initial_image_1.jpg", 
    "path/to/your/initial_image_2.jpg",
    "path/to/your/initial_image_3.jpg"
]
# ...
```

3. 워크플로우 실행
단계 1: 공간 분석 및 리포트 생성
먼저 main_report.py를 실행하여 분석을 시작합니다.

```bash
python main_report.py
결과: selected_input_image.jpg, parsed_report.json 등이 생성됩니다.
```

단계 2: 사용자 선택 파일 준비
프론트엔드 또는 수동으로 시뮬레이션 옵션을 style_choice.json 및 user_choice.json에 저장합니다.
style_choice.json{"selected_style": "AI 추천"} - 방 전체 스타일 변경 시 사용

user_choice.json{"use_add": true, "use_remove": false, "use_change": true} - 가구 부분 수정 시 사용

단계3: 시뮬레이션 실행 (둘 중 하나 선택)

A. 전체 스타일 변경 시뮬레이션 (style_choice.json 사용)
```bash
python main_new_looks.py
```

B. 가구 부분 수정 시뮬레이션 (user_choice.json 사용)
```bash
python main_modify_looks.py
```

최종 결과물
시뮬레이션이 완료되면, 프로젝트 루트 디렉토리에 3장의 최종 이미지 파일이 생성됩니다.

- img4new3r_org.png (변경된 사진의 정면 뷰) 
- img4new3r_left.png (좌측 뷰) 
- img4new3r_right.png (우측 뷰)
