# 230919
컴퓨터공학과 20191276 양용석 </br>
비쥬얼프로그래밍 과제 </br>
</br>
</br>
</br>
1. 코드 작성 전에 해야할 일</br>
 1) 리소스 탭에서 리소스 삽입
 2) 상속받는 클래스 CSon 추가
 3) 기본 다이얼로그에는 리스트박스와 버튼(Modeless) 추가, 리스트박스 이름은 m_List 로 변수 추가
 4) 새로 삽입한 리소스에서는 EditText와 버튼 (Add) 추가, EditText 이름은 m_Str로 변수 추가, 값으로 받음.

```
//Modeless 버튼 클릭 시 
#include "CSon.h" 
void CMFCApplication8Dlg::OnBnClickedButton1()
{
	CSon* p = new CSon();                                           //포인터p 추가
	p->Create(IDD_DIALOG1);                                         //IDD_DIALOG1 (새 리소스를 삽입한 것) 을 불러옴 
	p->ShowWindow(SW_SHOW);                                         //불러온 후 화면에 보여줌

}

```
</br>

```
//Add 버튼 클릭 시
#include "MFCApplication8Dlg.h"
void CSon::OnBnClickedButton1()
{
	CMFCApplication8Dlg* p = (CMFCApplication8Dlg *)GetParent();   //Add 버튼 클릭 시 타입 변환을 하며 CMFCApplication8Dlg 에 대한 포인터 반환
	p->m_List.AddString(m_Str);                                    //m_Str 텍스트박스에 입력한 값을 m_List 리스트박스에 추가하기 위해 AddString 사용
	UpdateData(true);                                              //추가 후 리스트에 추가된 걸 업데이트 해주기 위해 UpdateData 사용
}

void CSon::OnClose()
{
	DestroyWindow();
	CDialogEx::OnClose();                                         // DestroyWindow 함수 실행으로 인해 창을 닫을 수 있음
}

void CSon::PostNcDestroy()
{                                                              //PostNcDestroy()는 대화상자가 완전히 소멸된 후에 호출되기 때문에 안전하게 삭제 가능
	CDialogEx::PostNcDestroy();                                  //클래스 마법사를 통해 가상 함수 추가 후 사용 , 생성자에서 new로 객체를 만든 경우에 적용
}

```
