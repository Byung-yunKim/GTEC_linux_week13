# GTEC_linux_week13

2022.05.27

nano shtest1.sh    
#!/bin/sh -> 쉘 생성 시 필요함    
echo "사용자이름" $USER    
echo "홈디렉토리" $HOME    
echo "배쉬셀경로" $BASH

sh shtest1.sh -> 쉘 파일 실행시킬 때는 sh 사용해야됨

history -> 지금까지 사용한 명령어 확인 가능    
echo [문자열 / $환경변수] -> HOME, LANG, BASH, HISTFILE / 화면에 출력함(print)

nano son1.sh    
#!/bin/sh    
name="son"    
age=30    
echo "이름:" $name    
echo "나이:" $age

name = "son" -> 변수 선언시 공백이 없어야함    
name="son" -> 이렇게 써야됨

☆☆☆ 파라미터 변수(특이 변수)    
$sh son.sh aaa bbb ccc 라는 쉘이 있을 경우

1. $0 -> 쉘 스크립트 이름    
echo $0 -> son.sh

2. $1 ~ $9 -> 쉘 스크립트에서 사용한 변수    
$1 = aaa $2 = bbb $3 = ccc

3. $# -> 쉘 스크립트에 사용한 파라미터 변수의 수    
$# -> 3(변수가 3개 들어가 있음)

4. $@ -> 쉘 스크립트에 사용한 파라미터 변수 이름    
$@ -> aaa, bbb, ccc

5. $? -> 기재되어 있는 위치에서의 프로세스값 (디버깅 시 사용함)

son1.sh는 기본적으로 권한이 rw 밖에 없기 때문에 sh를 사용하지 않고서는 실행이 안됨 -> chmod +x son1.sh로 실행 권한 부여    
./son1.sh -> 실행 가능

nano son2.sh    
#!/bin/sh    
echo "this is var count:" $#    
echo "this is var word:" $@    
echo "this is first var:" $1    
echo "this is second var:" $2    
echo "this is third var:" $3

ubuntu@ip-172-31-35-142:~/sh_script$ sh son2.sh a b c    
this is var count: 3    
this is var word: a b c    
this is first var: a    
this is second var: b    
this is third var: c

read [변수명]-> 값을 읽어오는 명령어 변수에 데이터 저장 가능(input)

nano read1.sh    
#!/bin/sh    
echo "데이터를 입력하세요"    
read v1    
echo "read로 입력 받은 변수값:" $v1

if의 끝은 fi    
조건의 사이에는 공백이 무조건 있어야함 -> if [ 'cook' = 'cook' ]

-n [문자열] -> not null이면 true    
-z [문자열] -> null이면 true    
[수식1] -eq [수식2] -> =    
[수식1] -ne [수식2] -> !=    
[수식1] -gt [수식2] -> >    
[수식1] -ge [수식2] -> >=    
[수식1] -lt [수식2] -> <    
[수식1] -le [수식2] -> <=    
![수식] -> 수식이 거짓이면 true

nano if1.sh    
#!/bin/sh    
if [ "BTS" = "BTZ" ]    
then    
echo "문자열이 서로 같다"    
else    
echo "BTS와 비교하지 말아라"    
fi    
exit 0

nano if2.sh    
#!/bin/sh    
if [ 1004 -eq 1004 ]    
then    
echo "참입니다."    
else    
echo "서로 다른 숫자입니다"    
fi    
exit 0
