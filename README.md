# Git 연습용 미니 프로젝트

이 프로젝트는 VS Code에서 아래 흐름을 직접 연습하기 위한 아주 작은 Python 프로젝트입니다.

```text
파일 수정 → Stage → Commit → Push → Pull
```

## 프로젝트 파일

```text
git-practice-project/
├─ README.md
├─ greeting.py
├─ calculator.py
└─ .gitignore
```

- `greeting.py`: 이름을 입력하면 인사하는 프로그램
- `calculator.py`: 두 숫자를 더하는 프로그램
- `.gitignore`: Python이 자동 생성하는 불필요한 파일을 Git에서 제외

## 0. 준비하기

1. ZIP 파일을 내려받아 압축을 풉니다.
2. VS Code에서 `파일 > 폴더 열기`를 누릅니다.
3. 압축을 푼 `git-practice-project` 폴더를 엽니다.
4. VS Code에서 `터미널 > 새 터미널`을 엽니다.
5. 아래 명령으로 프로그램이 실행되는지 확인합니다.

```bash
python greeting.py
python calculator.py
```

Windows에서 `python`이 동작하지 않으면 `py`를 사용해도 됩니다.

```bash
py greeting.py
py calculator.py
```

## 1. Git 저장소 시작하기

VS Code 터미널에서 실행합니다.

```bash
git init
git status
```

왼쪽의 **소스 제어(Source Control)** 아이콘을 눌러도 파일 목록을 볼 수 있습니다. 단축키는 `Ctrl + Shift + G`입니다.

### 첫 번째 Stage

소스 제어 화면의 **Changes** 아래에서 파일마다 나타나는 `+` 버튼을 누릅니다. 모든 파일을 한꺼번에 넣고 싶다면 **Changes** 제목 옆의 `+`를 누릅니다.

그러면 파일들이 **Staged Changes**로 이동합니다.

> Stage는 "다음 Commit에 이 변경을 포함하겠다"라고 고르는 단계입니다.

### 첫 번째 Commit

소스 제어 화면 위쪽 입력란에 아래 메시지를 입력합니다.

```text
Add initial practice project
```

그다음 **Commit** 버튼을 누릅니다.

터미널에서 기록을 확인할 수도 있습니다.

```bash
git log --oneline
```

## 2. 수정 → Stage → Commit 연습

### 과제 A: 인사말 수정

1. `greeting.py`를 엽니다.
2. `안녕하세요`를 `반갑습니다`로 바꿉니다.
3. `Ctrl + S`로 저장합니다.
4. 소스 제어에서 `greeting.py`를 클릭해 바뀐 부분을 확인합니다.
5. 파일 옆의 `+`를 눌러 Stage합니다.
6. 아래 메시지로 Commit합니다.

```text
Change greeting message
```

### 과제 B: 일부 파일만 Stage

이번에는 두 파일을 모두 수정하되, Commit은 따로 만들어 봅니다.

1. `greeting.py`의 마지막 줄 아래에 다음 문장을 추가합니다.

```python
print("오늘도 좋은 하루 보내세요!")
```

2. `calculator.py`의 `add` 함수 아래에 빼기 함수를 추가합니다.

```python
def subtract(a, b):
    return a - b
```

3. 두 파일을 모두 저장합니다.
4. 소스 제어에서 두 파일이 모두 **Changes**에 보이는지 확인합니다.
5. `greeting.py`만 Stage하고 아래 메시지로 Commit합니다.

```text
Add a closing greeting
```

6. `calculator.py`는 아직 **Changes**에 남아 있어야 합니다.
7. 이제 `calculator.py`를 Stage하고 아래 메시지로 별도 Commit합니다.

```text
Add subtraction function
```

이 과제의 핵심은 **수정된 파일이 여러 개여도 원하는 파일만 골라 Commit할 수 있다**는 점입니다.

## 3. GitHub에 Push 연습

### GitHub에서 빈 저장소 만들기

1. GitHub에 로그인합니다.
2. 오른쪽 위 `+`를 누르고 **New repository**를 선택합니다.
3. 저장소 이름을 `git-practice-project`로 입력합니다.
4. Public 또는 Private 중 원하는 것을 선택합니다.
5. **Add a README file**, `.gitignore`, License는 선택하지 않습니다. 이미 로컬 프로젝트에 파일이 있기 때문입니다.
6. **Create repository**를 누릅니다.

### 내 프로젝트와 GitHub 연결하기

GitHub가 보여주는 저장소 주소를 복사합니다. 아래의 주소는 예시이므로 반드시 본인의 주소로 바꿔야 합니다.

```bash
git branch -M main
git remote add origin https://github.com/내아이디/git-practice-project.git
git push -u origin main
```

GitHub 페이지를 새로고침했을 때 파일과 Commit 기록이 보이면 성공입니다.

> Push는 내 PC의 Commit을 GitHub로 보내는 작업입니다. Stage하지 않았거나 Commit하지 않은 변경은 Push되지 않습니다.

## 4. 혼자서 Pull 연습

팀원이 GitHub에서 파일을 수정했다고 가정하고, GitHub 웹사이트에서 직접 변경을 만들어 봅니다.

1. GitHub 저장소 페이지에서 `README.md`를 클릭합니다.
2. 연필 모양의 **Edit this file** 버튼을 누릅니다.
3. 문서 맨 아래에 다음 문장을 추가합니다.

```text
GitHub에서 만든 변경사항입니다.
```

4. **Commit changes...**를 누릅니다.
5. Commit 메시지에 `Update README on GitHub`를 입력하고 변경을 확정합니다.
6. VS Code로 돌아옵니다.
7. 터미널에서 아래 명령을 실행합니다.

```bash
git pull
```

8. 로컬의 `README.md` 맨 아래에 문장이 생겼는지 확인합니다.

> Pull은 GitHub에 있는 새 Commit을 내 PC로 가져오는 작업입니다.

## 5. 전체 흐름 최종 연습

마지막으로 안내를 보지 않고 아래 과제를 해보세요.

1. `calculator.py`에 곱셈 함수 `multiply(a, b)`를 추가합니다.
2. 변경 내용을 확인합니다.
3. Stage합니다.
4. `Add multiplication function`이라는 메시지로 Commit합니다.
5. GitHub로 Push합니다.
6. GitHub에서 코드가 바뀌었는지 확인합니다.

## 자주 쓰는 명령어 요약

VS Code 화면으로 작업해도 되지만, 상태를 확인할 때 아래 명령어가 유용합니다.

```bash
git status          # 현재 변경 및 Stage 상태 확인
git log --oneline   # Commit 기록 확인
git pull            # GitHub → 내 PC
git push            # 내 PC의 Commit → GitHub
```

## 헷갈릴 때 보는 한 줄 요약

```text
수정: 파일 내용을 바꿈
Stage: 다음 Commit에 넣을 변경을 선택
Commit: 선택한 변경을 내 PC의 Git 기록으로 저장
Push: 내 PC의 Commit을 GitHub로 보냄
Pull: GitHub의 새 Commit을 내 PC로 가져옴
```
