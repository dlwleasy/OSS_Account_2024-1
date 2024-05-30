# OSS_Account_2024-1

가계부에 관련된 기능을 만드는 프로젝트입니다. 각종 가계부 앱 등에서 제공하는 작은 기능부터 복잡한 모든 기능을 포함합니다.
유용한 기능들 중심으로 추가해주면 좋겠습니다.

[2024.05.29] 기능 분리 포멧 추가.

# 가계부 데이터 예시 (단위: 원)
# 각 항목은 '항목명: 금액' 형태로 저장.
last_month_expenses = {
    '식비': 300000,
    '교통비': 100000,
    '통신비': 50000,
    '기타': 70000
}

this_month_expenses = {
    '식비': 350000,
    '교통비': 95000,
    '통신비': 50000,
    '기타': 80000
}

# 지난달 대비 이번 달 소비 차이를 계산하는 함수
def calculate_difference(last_month, this_month):
    differences = {}
    for key in this_month.keys():
        if key in last_month:
            # 이번 달 - 지난달 소비 차이 계산
            differences[key] = this_month[key] - last_month[key]
        else:
            # 지난달에는 없던 항목
            differences[key] = this_month[key]
    return differences

# 소비 차이를 출력하는 함수
def print_differences(differences):
    print("지난달 대비 이번 달 소비 차이:")
    for category, difference in differences.items():
        if difference > 0:
            print(f"{category}: 증가 {difference}원")
        elif difference < 0:
            print(f"{category}: 감소 {-difference}원")
        else:
            print(f"{category}: 변동 없음")

# 메인 로직
differences = calculate_difference(last_month_expenses, this_month_expenses)
print_differences(differences)
