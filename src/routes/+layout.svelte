# リポジトリをフォークする

GitHub上のリポジトリをフォークして、変更の提案、プロジェクトでの共同作業、コードベースの独自のコピーの管理を行います。

## フォークについて

リポジトリをフォークすると、アップストリーム リポジトリに影響を与えずにプロジェクトに変更を提案できます。 「[フォークについて](/ja/pull-requests/get-started/about-forks)」を参照してください。

## 前提条件

まだ設定していない場合は、Git から GitHub.com を使用して Git と認証を設定します。 「[Git のセットアップ](/ja/get-started/git-basics/set-up-git)」を参照してください。

## リポジトリをフォークする

<div class="ghd-tool webui">

上流リポジトリへの変更を提案するために、プロジェクトをフォークする場合があります。 この場合は、フォークをアップストリーム リポジトリと定期的に同期することをお勧めします。 これには、コマンドラインで Git を使用する必要があります。 フォークしたのと同じ [octocat/Spoon-Knife](https://github.com/octocat/Spoon-Knife) リポジトリを使用して、アップストリーム リポジトリの設定を練習できます。

1.

GitHub
で、[octocat/Spoon-Knife](https://github.com/octocat/Spoon-Knife) リポジトリに移動します。

1. ページの右上隅の **\[フォーク]** を選択します。

   ![リポジトリの main ページのスクリーンショット。 フォーク アイコンと "フォーク 59.3k" のラベルが付いたボタンが濃いオレンジの枠線で囲まれています。](/assets/images/help/repository/fork-button.png)
2. \[所有者] の下のドロップダウン メニューを選び、フォークされたリポジトリの所有者をクリックします。
3. 既定では、フォークの名前はその上流リポジトリと同じです。 必要に応じて、\[リポジトリ名] フィールドに別の名前を入力してフォークを区別します。
4. 必要に応じて、\[説明] フィールドにフォークの説明を入力します。
5. 必要に応じて、 **\[DEFAULT ブランチのみをコピーする]** を選びます。

   オープンソース プロジェクトへのコントリビューションなど、多くのフォーク シナリオでは、既定のブランチのみをコピーする必要があります。 このオプションを選ばないと、すべてのブランチが新しいフォークにコピーされます。
6. **\[フォークの作成]** をクリックします。

> [!NOTE]
> 上流リポジトリから追加のブランチをコピーする場合は、**\[Branches]** ページから行うことができます。 「[リポジトリ内のブランチの管理](/ja/pull-requests/how-tos/commit-changes/managing-branches-within-your-repository)」を参照してください。

</div>

<div class="ghd-tool cli">

> [!NOTE]
> GitHub CLI の詳細については、「[GitHub CLI について](/ja/github-cli/github-cli/about-github-cli)」を参照してください。

リポジトリのフォークを作成するには、`gh repo fork` サブコマンドを使用します。

```shell
gh repo fork REPOSITORY
```

組織内でフォークを作成するには、`--org` フラグを使用します。

```shell
gh repo fork REPOSITORY --org "octo-org"
```

</div>

<div class="ghd-tool desktop">

リポジトリは、 GitHub.com または GitHub Desktopでフォークできます。
GitHub.comのフォークの詳細については、[この記事の Web ブラウザーバージョンを](/ja/pull-requests/how-tos/work-with-forks/fork-a-repo?tool=webui)参照してください。

GitHub Desktop で、書き込みアクセス権限を持たないリポジトリをクローンし、そのリポジトリに変更をプッシュしようとすると、フォークが作成されます。

1. **\[ファイル]** メニューの **\[リポジトリの複製]** をクリックします。

   <div class="ghd-tool mac">

   ![Mac のメニュー バーのスクリーンショット。 \[ファイル\] ドロップダウン メニューが展開され、\[リポジトリのクローン\] オプションがオレンジ色の枠線で強調表示されています。](/assets/images/help/desktop/clone-file-menu-mac.png)

   </div>

   <div class="ghd-tool windows">

   ![Windows の \[GitHub Desktop\] メニュー バーのスクリーンショット。 \[File\] ドロップダウン メニューが展開され、\[Clone Repository\] オプションがオレンジ色の枠線で囲まれています。](/assets/images/help/desktop/clone-file-menu-windows.png)

   </div>

2. クローンしたいリポジトリの場所に対応するタブをクリックしてください。 この例では、\[URL] タブをクリックします。

   ![\[Clone a repository\] ウィンドウの \[URL\] タブのスクリーンショット。 \[GitHub.com\]、\[GitHub Enterprise\]、\[URL\] の各タブが濃いオレンジ色の枠線で囲まれています。](/assets/images/help/desktop/choose-repository-location-url-tab-windows.png)

3. クローンを作成するリポジトリの URL またはパスを入力します。

   ![\[Clone a repository\] ウィンドウの \[URL\] タブのスクリーンショット。 "octocat/Spoon-Knife" を含む入力がオレンジ色の枠線で強調表示されています。](/assets/images/help/desktop/clone-a-repository-url-tab-name-input.png)

4. リポジトリをクローンする先のローカル ディレクトリを選ぶには、\[ローカル パス] フィールドの横にある **\[選択]** をクリックし、そのディレクトリに移動します。

   ![\[Clone a repository\] ウィンドウの \[URL\] タブのスクリーンショット。 \[選択\] というボタンがオレンジ色の枠線で強調表示されています。](/assets/images/help/desktop/clone-choose-button-url-windows.png)

5. \[リポジトリのクローン] ウィンドウの下部にある **\[クローン]** をクリックします。

6. フォークを作成するには、変更をリポジトリにプッシュしてみてください。 たとえば、新しいブランチを作成して公開します。 このリポジトリをフォークするかどうかを確認するプロンプトが表示されます。

   ![\[Create a fork prompt\] ウィンドウのスクリーンショット。 \[Fork this repository\] というラベルが付いたボタンがオレンジ色の枠線で強調表示されています。](/assets/images/help/desktop/create-fork-button-windows.png)

7. \[How are you planning to use this fork?] (このフォークはどのように使う予定ですか?) ウィンドウの情報を読みます ] ウィンドウと同じです。
   * オリジナルの上流のリポジトリへのコントリビューションにこのフォークを使うつもりなのであれば、 **\[To contribute to the parent project]** (親プロジェクトへのコントリビュート) をクリックしてください。
   * 上流に接続されていないプロジェクトにこのフォークを使うつもりなのであれば、 **\[For my own purposes]** (自分自身の目的のため) をクリックしてください。

8. **\[続行]** をクリックします。

</div>

<div class="ghd-tool webui">

## フォークされたリポジトリを複製する

これで、Spoon-Knife リポジトリのフォークが作成されましたが、そのリポジトリのファイルはコンピューター上にありません。

1.

GitHub
で、Spoon-Knife リポジトリの**あなたのフォーク**に移動します。

1. ファイル一覧の上にある **\[<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-code" aria-label="code" role="img"><path d="m11.28 3.22 4.25 4.25a.75.75 0 0 1 0 1.06l-4.25 4.25a.749.749 0 0 1-1.275-.326.749.749 0 0 1 .215-.734L13.94 8l-3.72-3.72a.749.749 0 0 1 .326-1.275.749.749 0 0 1 .734.215Zm-6.56 0a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042L2.06 8l3.72 3.72a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L.47 8.53a.75.75 0 0 1 0-1.06Z"></path></svg> Code]** をクリックします。

   ![リポジトリのランディング ページのファイル リストのスクリーンショット。 \[コード\] ボタンが濃いオレンジ色の枠線で囲まれています。](/assets/images/help/repository/code-button.png)

2. リポジトリの URL をコピーします。

   * HTTPS を使用してリポジトリを複製するには、"HTTPS" の下にある <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copy" aria-label="クリップボードにコピー" role="img"><path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path></svg> をクリックします。
   * Organization の SSH 認証機関から発行された証明書などの SSH キーを使ってリポジトリをクローンするには、 **\[SSH]** 、<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copy" aria-label="Copy to clipboard" role="img"><path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path></svg> の順にクリックします。
   * GitHub CLI を使ってリポジトリをクローンするには、 **\[GitHub CLI]** をクリックしてから、<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copy" aria-label="Copy to clipboard" role="img"><path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path></svg> をクリックします。

     ![\[コード\] ドロップダウン メニューのスクリーンショット。 リポジトリの HTTPS URL の右側に、コピー アイコンが濃いオレンジ色の枠線で囲まれています。](/assets/images/help/repository/https-url-clone-cli.png)

3. ターミナルまたは Git Bash を開きます。

4. カレントワーキングディレクトリを、ディレクトリをクローンしたい場所に変更します。

5. `git clone`入力し、先ほどコピーした URL を貼り付けます。
   GitHubではなく、`YOUR-USERNAME`ユーザー名を使用すると、次のようになります。

   ```shell
   git clone https://github.com/YOUR-USERNAME/Spoon-Knife
   ```

6. **Enter** キーを押します。 Git によってローカルクローンが作成されます。

   ```shell
   $ git clone https://github.com/YOUR-USERNAME/Spoon-Knife
   > Cloning into `Spoon-Knife`...
   > remote: Counting objects: 10, done.
   > remote: Compressing objects: 100% (8/8), done.
   > remote: Total 10 (delta 1), reused 10 (delta 1)
   > Unpacking objects: 100% (10/10), done.
   ```

</div>

<div class="ghd-tool cli">

## フォークされたリポジトリを複製する

これで、Spoon-Knife リポジトリのフォークが作成されましたが、そのリポジトリのファイルはコンピューター上にありません。

> [!NOTE]
> GitHub CLI の詳細については、「[GitHub CLI について](/ja/github-cli/github-cli/about-github-cli)」を参照してください。

フォークのクローンを作成するには、`--clone` フラグを使用します。

```shell
gh repo fork REPOSITORY --clone=true
```

</div>

## フォークが上流リポジトリと同期するように Git を構成する

アップストリーム リポジトリへの変更を提案するプロジェクトをフォークする場合は、アップストリーム リポジトリからフォークのローカル クローンに変更をプルするように Git を構成できます。

<div class="ghd-tool webui">

1.

GitHub
で、[octocat/Spoon-Knife](https://github.com/octocat/Spoon-Knife) リポジトリに移動します。

1. ファイル一覧の上にある **\[<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-code" aria-label="code" role="img"><path d="m11.28 3.22 4.25 4.25a.75.75 0 0 1 0 1.06l-4.25 4.25a.749.749 0 0 1-1.275-.326.749.749 0 0 1 .215-.734L13.94 8l-3.72-3.72a.749.749 0 0 1 .326-1.275.749.749 0 0 1 .734.215Zm-6.56 0a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042L2.06 8l3.72 3.72a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L.47 8.53a.75.75 0 0 1 0-1.06Z"></path></svg> Code]** をクリックします。

   ![リポジトリのランディング ページのファイル リストのスクリーンショット。 \[コード\] ボタンが濃いオレンジ色の枠線で囲まれています。](/assets/images/help/repository/code-button.png)

2. リポジトリの URL をコピーします。

   * HTTPS を使用してリポジトリを複製するには、"HTTPS" の下にある <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copy" aria-label="クリップボードにコピー" role="img"><path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path></svg> をクリックします。
   * Organization の SSH 認証機関から発行された証明書などの SSH キーを使ってリポジトリをクローンするには、 **\[SSH]** 、<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copy" aria-label="Copy to clipboard" role="img"><path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path></svg> の順にクリックします。
   * GitHub CLI を使ってリポジトリをクローンするには、 **\[GitHub CLI]** をクリックしてから、<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copy" aria-label="Copy to clipboard" role="img"><path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path></svg> をクリックします。

     ![\[コード\] ドロップダウン メニューのスクリーンショット。 リポジトリの HTTPS URL の右側に、コピー アイコンが濃いオレンジ色の枠線で囲まれています。](/assets/images/help/repository/https-url-clone-cli.png)

3. ターミナルまたは Git Bash を開きます。

4. 複製したフォークのディレクトリに移動します。
   * ホーム ディレクトリに移動するには、他のテキストを含めずに「`cd`」と入力します。
   * 現在のディレクトリのファイルとフォルダーを一覧表示するには、「`ls`」と入力します。
   * 一覧表示されているディレクトリのいずれかに移動するには、「`cd YOUR-LISTED-DIRECTORY`」と入力します。
   * 1 つ上のディレクトリに移動するには、「`cd ..`」と入力します。

5. 「`git remote -v`」と入力して **Enter** キーを押します。 フォーク用に現在構成されているリモート リポジトリが表示されます。

   ```shell
   $ git remote -v
   > origin  https://github.com/YOUR-USERNAME/YOUR-FORK.git (fetch)
   > origin  https://github.com/YOUR-USERNAME/YOUR-FORK.git (push)
   ```

6. `git remote add upstream`入力し、手順 3 でコピーした URL を貼り付けて **Enter キー**を押します。 次のようになります。

   ```shell
   git remote add upstream https://github.com/ORIGINAL-OWNER/Spoon-Knife.git
   ```

7. フォークに指定した新しいアップストリーム リポジトリを確認するには、もう一度 `git remote -v` 入力します。 フォークの URL が `origin` として表示され、アップストリーム リポジトリの URL が `upstream`として表示されます。

   ```shell
   $ git remote -v
   > origin    https://github.com/YOUR-USERNAME/YOUR-FORK.git (fetch)
   > origin    https://github.com/YOUR-USERNAME/YOUR-FORK.git (push)
   > upstream  https://github.com/ORIGINAL-OWNER/ORIGINAL-REPOSITORY.git (fetch)
   > upstream  https://github.com/ORIGINAL-OWNER/ORIGINAL-REPOSITORY.git (push)
   ```

いくつかの Git コマンドを使用して、フォークをアップストリーム リポジトリと同期し続けることができます。 「[フォークを同期する](/ja/pull-requests/how-tos/work-with-forks/syncing-a-fork)」を参照してください。

</div>

<div class="ghd-tool cli">

> [!NOTE]
> GitHub CLI の詳細については、「[GitHub CLI について](/ja/github-cli/github-cli/about-github-cli)」を参照してください。

フォークされたリポジトリのリモート リポジトリを構成するには、`--remote` フラグを使用します。

```shell
gh repo fork REPOSITORY --remote=true
```

リモート リポジトリの名前を指定するには、`--remote-name` フラグを使用します。

```shell
gh repo fork REPOSITORY --remote-name "main-remote-repo"
```

</div>

### フォークを編集する

フォークには、次のような変更を加えることができます。

* **ブランチの作成:**[*ブランチ*](/ja/pull-requests/how-tos/commit-changes/managing-branches-within-your-repository) を使用すると、メイン プロジェクトを危険にさらすことなく、新しい機能を構築し、アイデアをテストできます。
* **pull requests を開く:** アップストリーム リポジトリに貢献する場合は、プル要求を送信して、フォークをリポジトリにプルするように元の作成者に依頼できます。 「[フォークからプルリクエストを作成する](/ja/pull-requests/how-tos/create-pull-requests/creating-a-pull-request-from-a-fork)」を参照してください。

## フォークする他のリポジトリを見つける

リポジトリをフォークしてプロジェクトへのコントリビューションを開始しましょう。
任意のパブリック リポジトリをフォークできます。

* 個人アカウントへ
* リポジトリを作成する権限がある組織へ

プライベート リポジトリにアクセスできて、所有者がフォークを許可している場合は、次の場所にリポジトリをフォークできます。

* 個人用アカウントへ
* リポジトリを作成するアクセス許可を持っている GitHub Team 上の組織へ

GitHub Freeを使用して組織にプライベート リポジトリをフォークすることはできません。
GitHub TeamとGitHub Freeの詳細については、[AUTOTITLE を](/ja/get-started/learning-about-github/githubs-plans)参照してください。

リポジトリをフォークできるタイミングの詳細については、 [フォーク](/ja/pull-requests/reference/forks) を参照してください。

[\[探索\] GitHub](https://github.com/explore)を参照してプロジェクトを検索し、オープンソース リポジトリへの投稿を開始できます。 「[GitHubのopen sourceに貢献する方法を見つける](/ja/get-started/exploring-projects-on-github/finding-ways-to-contribute-to-open-source-on-github)」を参照してください。

## 次のステップ

リポジトリをフォークし、フォークのクローンを練習し、アップストリームリポジトリを構成しました。

* コマンド ラインで Git を使用して変更を複製および同期する方法の詳細については、 [Git のセットアップ](/ja/get-started/git-basics/set-up-git) を参照してください。

* プロジェクトを格納し、 GitHubでコードを共有する新しいリポジトリを作成することもできます。 プロジェクトのリポジトリを作成すると、コードを GitHub に格納できます。 これにより、他の開発者と共有するために選択できる作業のバックアップが提供されます。 詳しくは、「[リポジトリのクイック スタート](/ja/repositories/creating-and-managing-repositories/quickstart-for-repositories)」をご覧ください。

* GitHub上の各リポジトリは、個人または組織によって所有されています。
  GitHubで接続してフォローすることで、ユーザー、リポジトリ、組織と対話できます。 詳しくは、「[GitHubでのプロジェクトの検出](/ja/get-started/exploring-projects-on-github/discovering-projects-on-github)」をご覧ください。

* GitHub には素晴らしいサポート コミュニティがあり、助けを求め、世界中の人々と話すことができます。 [GitHub Community](https://github.com/orgs/community/discussions) で会話に参加してください。
