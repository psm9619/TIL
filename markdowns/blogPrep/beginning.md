# 200502~'Git blogging with Hexo' Begins!!
* Reference(참고사이트) <br> 
전체적인 스텝들은 전적으로 밍피디님의 Hexo 블로그 만들기 과정을 참고합니다. <br>
[밍피디 Github블로그 만들기 with Hexo](https://mingpd.github.io/2019/04/14/github-blog-with-hexo-1/)<br>
Hexo Document [in Kor](https://hexo.io/ko/docs/) / [in Eng](https://hexo.io/docs/)<br>
Videos: [Hexo-Static Site Genearator Tutorial](https://www.youtube.com/playlist?list=PLLAZ4kZ9dFpOMJR6D25ishrSedvsguVSm)<br>
Theme: Tranquilpeak [Hexo-theme-tranquilpeak Github](https://github.com/LouisBarranqueiro/hexo-theme-tranquilpeak/blob/master/DOCUMENTATION.md)
<br>
* Additional Ref(추가_마크다운 에디터 등)<br>
[VS Code github style markdown](https://blog.aliencube.org/ko/2016/07/06/markdown-in-visual-studio-code/)
<br><br>

### Hexo?
- blog framework that generates static files w beautiful themes from Markdown in a sec 
<br>마크다운 또는 다른 언어로 작성된 포스트에 빠르게 테마를 가미하여 정적파일 생성 
- [Quick Overview](https://youtu.be/ARted4RniaU)

### Requirements: Node.js, Git
Git installation 
- [official download site](https://git-scm.com/download/win)<br>

Node.js installation
- provides [official installer](https://nodejs.org/en/download/) for most platforms
<br> / Windows users, check if Node.js is added in PATH variable (in official installer, Add to PATH is checked by default but make sure it's working!)

### Install HEXO
After Git, Node.js installation done, let's install HEXO!
``` 
$ npm install -g hexo-cli 
```
#### Create Hexo Project
Now... create a new repository w Hexo!! 
- cd to where you want to create blogging repository in local then,,,
``` 
$ hexo init *folder name* 
$ cd *folder name* 
$ npm install
```
- For my case, got this warning msg 
```
..found 1 low severity vulnerability, run 'npm audit fix' to fix them, or 'npm audit' for details' 
# ---- ran npm audit fix
$ npm audit fix
```
but re-received an error msg saying 
  ```
  1 vulnerability required manual review and could not be updated' 
  ```
it seems to be a vulnerability affecting JavaScript, referring to the ability to inject propoerties into existing JavaScript language construct prototypes such as objects(ref. [here](https://snyk.io/vuln/SNYK-JS-MINIMIST-559764))....................... 우선 low vulnerability 이슈이기도 하고,,,, 해결법을 잘 모르겠는 만큼 사알짝 패스하고 tranquilpeak 테마 적용으로 넘어가본다_200504
#### Apply theme
- Download theme source code(I'm using [Tranquilpeak](https://github.com/LouisBarranqueiro/hexo-theme-tranquilpeak/releases/tag/v4.0.0)), 
<br> Unzip it into ```..\ *your blog folder*\themes``` directory. Rename the unsipped direc as 'tranquilpeak'
- Open ```*your blog folder*'s '\_config.yml``` (not the themes\tranquilpeal\_config.yml)
- Scroll down to change theme to 'theme:tranquilpeak'
- Command prompt, cd to tranquilpeak folder
```
$ cd ..\ *your blog folder*\themes\tranquilpeak'
$ npm install  # might give some node vulnerability issues, then run $ npm audit fix
$ npm run prod
```
- Command prompt, at *your blog folder* 
```
'$ hexo server' 
```
<br> If successful, this will give msg like ```Hexo is running at http://localhost:4000```. Copy paste it to browser.
![hexo_initial_helloworld](markdowns/blogPrep/img/hexo_helloworld.PNG)
#### Activate Category, Tags
Command prompt, at *your blog folder*
```
$ hexo new page "all-categories"
$ hexo new page "all-tags"
```
- Now there are ```.\source\all-categories\index.md```, ```.\source\all-tags\index.md``` 
![initial index file of all-categories](.\img\initial_index_categories.PNG)
- In each index.md file, add layout: "all-categoreis", layout: "all-tags" respectively. Also remove date, then add comments: falnese to both files
![fixed index file of all-categories](.\img\fixed_index_categories.PNG)
#### Options1: Change Sidebar (decreasing width)
- open ```themes\tranquilpeak\_config.yml```
- fix sidebar_behavior to 'sidebar_behavior:2'
#### Options2: Change Cover (new image)
- save your fav image to ```themes\tranquilpeak\source\_images```
- open ```themes\tranquilpeak\_config.yml```
- change cover_image to 'cover_image:<*your image name*>'
<br>\\ For me, I downloaded several imgs from pixabay but for some reason they all show up as white background even after resizing them to 1920x1080 like original cover imgs... 그래서 어쨌건간에 이 부분도 오늘은 패애쓰_050420
#### Options3: Fonts (Korean Fonts)
- (밍피디 블로그 참조) 한글 폰트는 (나눔스퀘어라운드)[https://hangeul.naver.com/2017/nanum]를 사용하도록 한다. cdn에 올라가 있는 폰트import 하는 식으로 진행.
- Open ```themes/tranquilpeak/source/_css/tranquilpeak.scss```
- add at the bottom of the file 
```
@import
url(https://cdn.rawgit.com/innks/NanumSquareRound/master/nanumsquareround.css);
```
- 기본폰트 설정을 바꾸기 위해 open ```themes/tranquilpeak/source/_css/utils/_variables.scss``` <br>
change Font Families like below
```
// Font families
$merriweather-serif:   'Merriweather', serif; // 이건 지우면 에러나더라고요
$nanum-sans-kr:          'NanumSquareRound', "Helvetica Neue", sans-serif; // 기본 폰트 
$nanum-coding:   'Source Code Pro', "NanumSquareRound", Consolas; // 코드 폰트

$font-family-base: $nanum-sans-kr; // 기본폰트 바꾸기

// 아래처럼 'code'와 'highlight'만 코드 폰트로 변경하고
// 나머지는 전부 나눔스퀘어라운드로 변경합시다.
$font-families: (
  // base
    'headings': $nanum-sans-kr,
  // components
    'code': $nanum-coding,
    'caption': $nanum-sans-kr,
    'image-gallery': $nanum-sans-kr,
    'post-header-cover': $nanum-sans-kr,
    'post-meta': $nanum-sans-kr,
    'post-content': $nanum-sans-kr,
    'post-excerpt-link': $nanum-sans-kr,
    'highlight': $nanum-coding,
  // layout
    'sidebar': $nanum-sans-kr,
);
```
#### grunt: javascript build tool
- grunt is a tool to buildup javascript, so after modifying css, js filfes in themes, need to do 'grunt build' (themes 안의 css, js등을 변경한 후에는 grunt를 사용해야 한다.)
- installation & initialization
```
$ npm install -g grunt-cli

$ cd themes/tranquilpeak
$ npm install grunt --save-dev
```
and after modifying any css, js files in themes
```
# themes\tranquilpeak 디렉토리 내에서
$ grunt build
```
### 기타 설정
- 전체 \_config.yml (not tranquilpeak's config)에서 site 이름, author 등 바꿔줌
- (Hexo 공식문서)[https://github.com/LouisBarranqueiro/hexo-theme-tranquilpeak/blob/master/DOCUMENTATION.md]에 나오는 Hexo configuration 단계들 중 필요한것 실행

### TO DO
- [구글 사이트 등록 밑 검색엔진 최적화(SEO)](https://msj0319.github.io/2020/02/14/Hexo-Blog-%EA%B5%AC%EA%B8%80-%EC%82%AC%EC%9D%B4%ED%8A%B8-%EB%93%B1%EB%A1%9D-%EB%B0%8F-%EA%B2%80%EC%83%89%EC%97%94%EC%A7%84-%EC%B5%9C%EC%A0%81%ED%99%94-SEO/)


