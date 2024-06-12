# .gitignore 파일 .gitkeep 파일

### 1️⃣ Husky가 뭘까?
<hr/>

### 1. .gitignore
`Git의 root 디렉토리에 저장되어, Git Repository나 Staging Area에 추가되지 말아야 하는(무시되어야 하는) 폴더나 파일을 정의하는 파일`

**.gitignore에 정의된 파일은 Staging Area에 올라가지 않기 때문에 tracking 되지 않음**

따라서 git status 를 이용했을 때 보이지 않는다.

정리하면
```
- 프로젝트 작업시 로컬 환경의 정보나 빌드 정보등 원격 저장소에 관리하지 말아야되는 파일들에 대해서 지정하여 원격 저장소에 실수로 올라가지 않도록 관리하는 파일

- 정의한 정보들에 해당하는 파일들에 대하여 git track하지 않도록 설정하는 역할
```
이다

### 문법 

```
# : comments

# no .a files
*.a

# but do track lib.a, even though you're ignoring .a files above
!lib.a

# only ignore the TODO file in the current directory, not subdir/TODO
/TODO

# ignore all files in the build/ directory
build/

# ignore doc/notes.txt, but not doc/server/arch.txt
doc/*.txt

# ignore all .pdf files in the doc/ directory
doc/**/*.pdf
```

### 적용
- .gitignore File을 같이 Push하면 됨

- 기존에 있던 Project에 .gitignore File이 적용이 안되는 경우 -> <br/> git Repository에서 적용해보고 다시 Push

```
git rm -r --cached .
git add .
git commit -m "Apply .gitignore"
```

### 2️⃣ .gitkeep
<hr/>

디렉토리 내의 `다른 파일들이 모두 삭제되더라도 혼자 남아서 디렉토리를 지킨다`(keep)는 의미

gitkeep 파일은 Git 사용자가 만든 빈 파일

Git 저장소가 빈 프로젝트 디렉토리를 유지
 
 만약 A라는 빈폴더를 생성하고 커밋을 하려고 하면 Git 저장소에 A폴더가 커밋되지 X <br/>
이럴 때 gitkeep파일을 A라는 폴더에 넣으면 A폴더가 커밋 O <br/>
  +만일 B라는 폴더에 있던 다른 파일들이 모두 삭제되더라도 gitkeep 파일이 있으면 B폴더는 커밋할 때 없어지지 않고 유지

한마디로
```
gitkeep 비어있는 폴더 커밋 가능
```
인 셈 

일종의 더미(dummy) 느낌이 아닐까??

### 적용

빈 디렉토리 생성
```
mkdir 폴더명
```

생성된 디렉토리에 `.gitkeep` 파일 추가하기:
```
touch 폴더명/.gitkeep
```

` .gitkeep `파일을 Git에 추가하고 커밋하기:
```
git add 폴더명/.gitkeep
git commit -m "빈 디렉토리 추가"
```