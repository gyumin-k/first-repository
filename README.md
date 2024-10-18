# first-repository

# AIFFEL Data Scientist Campus Code Peer Review Templete

코더 : [김규민]
리뷰어: [여혜미]]

---

🔑 **PRT(Peer Review Template)**

[o ]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**
- 문제에서 요구하는 최종 결과물이 첨부되었는지 확인
	- (문제를 해결하는 완성된 코드란 프로젝트 루브릭 3개 중 2개, 퀘스트 문제 요구조건 등을 지칭)
- 해당 조건을 만족하는 코드를 캡쳐해 근거로 첨부쳐해 근거로 첨부

import random as r # random 모듈 불러오기

class Account:
  #클래스 속성
  bank_name = "SC은행"
  account_count = 0 # account_count 생성된 계좌 수

  def __init__(self, name, start): # name = 예금주, start = 초기 금액
    self.name = name
    self.balance = start # balance = 잔액
    self.account_number = str(r.randint(100,999)) +"-" + str(r.randint(10,99)) + "-" + str(r.randint(100000,999999))
    Account.account_count += 1 # account_number = 계좌번호

    self.money_count = 0 # money_count = 입금 횟수
    self.deposit_list = [] # deposit_list  = 입금 내역 기록
    self.withdraw_list = [] # withdraw_list = 출금 내역 기록



  def get_account_num(self):
    return self.account_count

  def deposit(self, money): # money 입금금액
    if money >= 1:
      self.balance += money
      self.money_count += 1
      self.deposit_list.append(money)

      if self.money_count == 5:
          self.balance = self.balance * 1.01
      return self.balance
    else:
      print('입금은 최소 1원 이상만 가능합니다.')

  def withdraw (self, money_output): # money_output 출금금액
    if self.balance >= money_output:
      self.balance = self.balance - money_output
      self.withdraw_list.append(money_output)
      return self.balance
    else:
      print('출금은 계좌의 잔고 이상으로 출금할 수는 없습니다.')

  def display_info(self):
    return f"은행이름: {self.bank_name}, 예금주: {self.name}, 계좌번호: {self.account_number},잔고: {self.balance:,}원"

  def deposit_history(self): # deposit_history 입금 내역
    for i in self.deposit_list:
      print(i)
  def withdraw_history(self): # withdraw_history 출금 내역
    for i in self.withdraw_list:
      print(i)



s = Account('김규민',1000000) # q1 q2 확인
print(s.get_account_num()) #q3 계좌 개수 출력
print(s.deposit(5000)) #q4 입금 후 잔액
print(s.withdraw(3000)) #q5 출금 후 잔액
print(s.display_info()) # q6 정보 출력
     
1
1005000
1002000
은행이름: SC은행, 예금주: 김규민, 계좌번호: 481-85-785383,잔고: 1,002,000원

# q7
print(s.deposit(100))
print(s.deposit(100))
print(s.deposit(100))
print(s.deposit(100))

     
1002100
1002200
1002300
1012424.0

# q8
ss = Account("은현", 20000)
sss = Account("정은", 30000)

account_list = []
account_list.append(s)
account_list.append(ss)
account_list.append(sss)

list(account_list)
     
[<__main__.Account at 0x7a0bf33d9f30>,
 <__main__.Account at 0x7a0bf33daf20>,
 <__main__.Account at 0x7a0bf33d9ae0>]

# q9
for i in account_list:
  if i.balance >= 1000000:
    print(i.name)

     
김규민

# q10
s.deposit_history()
s.withdraw_history()
     
5000
100
100
100
100
3000


[o ]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 
	주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**
- 해당 코드 블럭에 doc string/annotation이 달려 있는지 확인
- 해당 코드가 무슨 기능을 하는지, 왜 그렇게 짜여진건지, 작동 메커니즘이 뭔지 기술.
- 주석을 보고 코드 이해가 잘 되었는지 확인
	- 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
.def deposit(self, money): # money 입금금액
    if money >= 1:
      self.balance += money
      self.money_count += 1
      self.deposit_list.append(money)

      if self.money_count == 5:
          self.balance = self.balance * 1.01
      return self.balance
    else:
      print('입금은 최소 1원 이상만 가능합니다.')

  def withdraw (self, money_output): # money_output 출금금액
    if self.balance >= money_output:
      self.balance = self.balance - money_output
      self.withdraw_list.append(money_output)
      return self.balance
    else:
      print('출금은 계좌의 잔고 이상으로 출금할 수는 없습니다.')
[0 ]  **3. 에러가 난 부분을 디버깅하여 문제를 “해결한 기록"을 남겼거나 "새로운 시도 
또는 추가 실험"을 수행해봤나요?**
- 문제 원인 및 해결 과정을 잘 기록하였는지 확인 또는
- 문제에서 요구하는 조건에 더해 추가적으로 수행한 나만의 시도, 실험이 기록되어 있는지 확인
	- 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
        
[ 0]  **4. 회고를 잘 작성했나요?**
- 주어진 문제를 해결하는 완성된 코드 내지 프로젝트 결과물에 대해 배운점과 아쉬운점, 느낀점 등이 상세히 기록되어 있는지 확인
    - 딥러닝 모델의 경우, 인풋이 들어가 최종적으로 아웃풋이 나오기까지의 전체 흐름을 도식화하여 모델 아키텍쳐에 대한 이해를 돕고 있는지 확인

[ 0]  **5. 코드가 간결하고 효율적인가요?**
- 파
이썬 스타일 가이드 (PEP8) 를 준수하였는지 확인
- 코드 중복을 최소화하고 범용적으로 사용할 수 있도록 모듈화(함수화) 했는지
	- 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
def __init__(self, name, start): # name = 예금주, start = 초기 금액
    self.name = name
    self.balance = start # balance = 잔액
    self.account_number = str(r.randint(100,999)) +"-" + str(r.randint(10,99)) + "-" + str(r.randint(100000,999999))
    Account.account_count += 1 # account_number = 계좌번호

    self.money_count = 0 # money_count = 입금 횟수
    self.deposit_list = [] # deposit_list  = 입금 내역 기록
    self.withdraw_list = [] # withdraw_list = 출금 내역 기록


---
### 참고 문헌
