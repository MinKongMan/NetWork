# 1-1장 HTTP 리퀘스트 메시지를 작성한다.


# Url 해독 방법
  - 브라우저가 처음 하는 일은 웹 서버에 리퀘스트의 메시지를 작성하기 위해 URL을 해독하는 것<br/>
  ex1) http://www.lab.cyber.co.kr/dir1/file1.html을 분해
      http:   //   www.lab.cyber.co.kr(웹 서버명)   dir1/file1.html(데이터 출처의 경로명)
      즉 www.lab.cyber.co.kr이라는 웹 서버에 /dir1/file1.html 이라는 경로의 파일, 즉 /dir1/ 디렉토리 아래에 있는 file1.html 파일에 액세스한다는 의미
  ex2) http://www.lab.cyber.co.kr/dir/ (파일명을 생략한 경우)
      위와 같은 경우 미리 서버측에 액세스할 파일명을 설정해 둠.
  ex3) http://www.lab.cyber.co.kr/whatisthis
      이 경우 끝에 /가 없으므로 whatisthis를 파일명으로 보는 게 맞을 것 같다.<br/>
      그래서 일반적으로 whatisthis라는 파일이 있으면 파일에 접근하고, whatisthis라는 디렉토리가 있으면 디렉토리에 접근한다.
      이때 파일명과 디렉토리 이름이 같을 수 없음(같은 이름의 파일과 디렉토리를 만들 수 없음)

# HTTP의 기본 개념
  
  
