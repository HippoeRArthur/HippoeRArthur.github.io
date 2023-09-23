---
layout: create
title: Create a Githib page with Hexo (Mac)
date: 2023-09-23 13:46:52
tags:
---
Just note that the way to create a personal blog in Github with Hexo. Anytime coould change the contain.
## 1. 安裝 VScode : Visual Studio Code
## 2. Hexo

以下均使用bash shell，Mac在終端機下的指令為/bin/bash
https://hexo.io 中給出了以下指令
```bath
npm install hexo-cli -g
hexo init blog
cd blog
npm install
hexo server
```
說明：
安裝 Node.js, 會一起安裝 npm (node package manager)
有了 npm 就可以執行以下的terminal終端機指令，用以安裝hexo模組：
```bash
npm install hexo-cli -g
```
在相同的erminal終端機內，利用cd與ls確認將來執行指令的檔案夾位置
確認之後，執行以下指令：
```bash
hexo init <資料夾名稱>  # 創建並初始化一網站的開發者資料夾
```
結束terminal終端機，利用VScode開啟<資料夾名稱>
開啟VScode程式內bash shell的終端機，執行：
```bash
npm install
```
hexo server，則是用來確認網站結果

註：若改變的themes，要將_config.yml內的 theme 名稱更換來套用

## 3. Git repository
因為要上傳至Github，因此需要將此資料庫進行 git initialized
```bash
git init

```
由於Theme裡，也有進行過git init，會與根目錄的衝突，因此需要刪除themes裡的.git資料
```bash
cd themes/<theme名稱>
rm -rf .git
cd.. # 退回themes目錄底下
cd.. # 退回<資料夾名稱>目錄底下
```
回到根目錄後，執行以下指令，這些指令也是日後檔案若有更新，都需要輸入一次的指令
```bash
# <更新後指令>
git add . #Add file contents to the index
git commit -m "what changed" # Record changes to the repository # -m"what changed" must be key in
git push -u origin main # Update remote refs along with associated objects (to main branch)
```
註：過程中都可以使用$ git status 檢查狀態

## 4. Github : create a new repository
新創建的 repository 進頁面 Github 給的一些標準指令，除了 git init 已經執行過以外，其他照順序執行
如果HTTPS不是用，需要換REMOTE SSH，需要先移除之前REMOTE過的內容
```bash
git rempte remove origin 
```
若有更新要上傳，就根據<更新後指令>的內容執行

## 5. 在 GitHub Pages 上部署 Hexo
https://hexo.io/zh-tw/docs/github-pages.html

一鍵佈署需要安裝 hexo-deployer-git (https://github.com/hexojs/hexo-deployer-git)
安裝結束需要在根目錄的 _config.yml 更新 deploy 資訊
```
deploy:
    type: git
    repo: https://github.com/<username>/<project>
    # example, https://github.com/hexojs/hexojs.github.io
    branch: gh-pages
```
更新以後執行以下指令：
```bash
hexo clean && hexo deploy # 將本地的資料需要更新佈署到 deploy 資料內容內
```

## 6. Github 設定 pages
請參考
https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site