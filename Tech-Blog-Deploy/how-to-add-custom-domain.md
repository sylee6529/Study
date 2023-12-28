### Gatsby 블로그에 custom domain 적용하는 법

1. 먼저 DNS 레코드에 GitHub Pages 관련 Docs에 나와있는 ip 주소를 등록해준다.
![image](https://github.com/sylee6529/Study/assets/68765200/728d4bdb-45c0-4df0-8e3e-f2474e63db7c)


2. 레포지토리의 Settings>Pages>Custom domain 섹션에서 도메인을 입력해주면 끝. 
  public 폴더 아래에 CNAME 파일을 두라는 이야기도 있었지만, 일단 이슈가 없는 한 잘 작동하는 듯하다.

![image](https://github.com/sylee6529/Study/assets/68765200/f30387cd-ef11-494a-879c-5affe5ed64c1)
