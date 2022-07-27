## Git workflow 
>**Branch를 이용해서 협업**

1. 원격저장소 소유권이 있는 경우 (콜라보레이션 포함)
```bash
#1. 자신의원격저장소에 colne 
$git clone [url]

#2-1 자신이 사용할 branch 생성 후, 사용
$git branch [  ]
$git switch [  ]
#2-2 branch 생성하고 변경
$git switch -c [  ]

#3. PR(pull request) master 병합 요청하기 

#4. 병합 후, 이전 branch는 필요 없으니 삭제 

#5. master 이동
$git switch master

#6. 변경된 내용 받아오기
$git pull origin master

#7. 2번에서 생성한 branch 필요 없으니까 삭제 
$git branch -d [  ]
```        

2. 원격저장소 소유권이 없는 경우
```bash
#1. 자신의 소유가 아닌 저장소를 fork 하여 나의 저장소로 복제 

#2. 나의 저장소에서 clone 하기 
$git clone [url]

#3. 동기화
$git remote add upstream [url]

#4. branch 생성 
$git branch [  ]
$git switch[  ]
or
$git switch -c [  ]

#5. 저장소에 push
$git push origin [branch명]

#6. master 병합 후, master로 변경 
$git switch master

#7. 내용 받아오기 
$git pull upstream master

#8. branch 이름 삭제 
$git branch -d[  ]
```
## reset, revert
1. reset
```bash
$git reset  
```
> * **예전의 버전으로 돌아가고 싶을때** 사용, **돌아간 커밋 이후의 내용은 사라진다.**  
> * 특정 커밋으로 되돌아 갈 수 있다. 
> * reset 옵션은 **1) soft, 2) mixed, 3) hard**가 있다.


  
```bash
#1. soft
$git reset --soft
```
* commit 되어진 파일을 staging area로 돌려 놓음, 워킹 디렉토리에 파일 보존 
```bash
#2. mixed
$git reset --mixed
```
* add 하기 전 상태, unstaged 상태로 돌려 놓음, 워킹 디렉터리의 파일에 보존 되어 있음
```bash
#3. hard
$git reset --hard
```
* add 하기 전 상태, unstaged 상태로 돌려 놓음, 워킹 디렉터리 파일에서 삭제 됨
  
2. revert
> * 쉽게 과거로 돌아갈 수 있다.
> * 이전의 commit 이력을 남겨두고 새로운 commit을 생성하면서 과거로 돌아간다.  

```bash
$git revert [commit ID]
```
|       reset        |       revert         |
|      :-----:       |       :-----:        |
|혼자 일할 때 더 좋음 |협업 할때 사용하면 좋음|
|commit 내역이 사라짐 |commit 내역이 남게 됨 |



⚠️ 혼동 주의 
```bash
$git reset --hard [commit ID]
# [commit ID]로 돌아가고 과거 내역은 사라짐 

$git revert [commit ID]
# [commit ID]으로 되돌림   
