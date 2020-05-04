# 200502~'Git blogging with Hexo' Begins!!
* Reference(참고사이트) <br> 
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
- $ npm install -g hexo-cli
#### Create Hexo Project
Now... create a new repository w Hexo!! 
- cd to where you want to create blogging repository in local then,,,
- $ hexo init *folder name* ; cd *folder name* ; npm install
<br> /For my case, got this msg 'found 1 low severity vulnerability\\ run 'npm audit fix' to fix them, or 'npm audit' for details' -> $ npm audit fix, but re-received an error msg saying '1 vulnerability required manual review and could not be updated' 
<br> /it seems to be a vulnerability affecting JavaScript, referring to the ability to inject propoerties into existing JavaScript language construct prototypes such as objects(ref. [here](https://snyk.io/vuln/SNYK-JS-MINIMIST-559764))....................... 우선 low vulnerability 이슈이기도 하고,,,, 해결법을 잘 모르겠는 만큼 사알짝 패스하고 tranquilpeak 테마 적용으로 넘어가본다_200504
#### Apply theme
- Download theme source code(I'm using [Tranquilpeak](https://github.com/LouisBarranqueiro/hexo-theme-tranquilpeak/releases/tag/v4.0.0)), 
<br> Unzip it into '..\ *your blog folder*\themes' directory. Rename the unsipped direc as 'tranquilpeak'
- Open *your blog folder*'s '\_config.yml' (not the themes\tranquilpeal\_config.yml)
- Scroll down to change theme to 'theme:tranquilpeak'
- Command prompt, run '$ hexo server' at *your blog folder*
<br> If successful, this will give msg like 'Hexo is running at http://localhost:4000'. Copy paste it to browser.
![hexo_initial_helloworld](.\img\hexo_helloworld.PNG)
#### Activate Category, Tags
Command prompt, at *your blog folder*
-$ hexo new page "all-categories"
-$ hexo new page "all-tags"
- Now there are '.\source\all-categories\index.md', '.\source\all-tags\index.md' 
![initial index file of all-categories](.\img\initial_index_categories.PNG)
- In each index.md file, add layout: "all-categoreis", layout: "all-tags" respectively. Also remove date, then add comments: false to both files
![fixed index file of all-categories](.\img\fixed_index_categories.PNG)





