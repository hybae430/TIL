# **git 협업 branch 활용: 명령어 정리**



## 개념

- 나뭇가지라는 의미로 코드의 분기를 의미함
  - master은 가장 메인 나뭇가지

```bash 
git log --oneline --graph	 # commit 기록을 1줄로, 시각화해서 보여줌
```



## 확인

> `git branch`

```bash
git branch					# 현재 가지들의 목록을 보여준다
```



## 생성

> `git branch <new branch name>`

```bash
git branch crud				# crud라는 가지 추가
```



## 이동

> `git switch <branch name>`

```bash
git switch crud				# crud 가지로 이동 (작업위치가 master에서 crud로 바뀜)
```



## 삭제

> `git branch -d <branch name>`

```bash
git branch -d crud			# crud 가지 삭제
```



> branch를 활용하여 기능들을 각자 추가하고, 충돌 등 검사해서 merge하며 최종코드로 만든다.

## 병합

> `git merge <branch name>`
>
> branch는 계속 발전만 하고 master에 merge해나가는 과정
>
> - `FastForward`: 빨리감기

```bash
git merge login				# 현재 위치의 코드와 login을 병합하겠다
git branch -d login	 		# merge 완료했으므로(더 역할이 없으므로) branch를 지운다
```

> master와 새로 만든 branch 두 곳 모두에 수정이 일어났을 때
>
> - 관련없는 두 수정이 일어났을 때: `Auto-merging`
> - 같은 곳의 수정으로 충돌이 일어났을 때: `Conflict`발생 후 위치가 (master|MERGING)으로 수정됨

```python
def signup():
    Accept Current Change | Accept Incoming Change | Accept Both Change | Compare Changes
    <<<<<<HEAD
    form
    ======
    pass
	>>>>>>signup
```

- 이런식으로 들어오면 위 네 버튼으로 선택(기존 merge하는 위치의 값 선택 | merge할 파일 값 선택 | 둘다 선택 | 뭐가 다른지 비교)하거나 <<<, ===, >>> 선 지워주고 위 코드/밑 코드 하나 선택해서 저장하기
- 사용한 branch를 지우는 것은 공통