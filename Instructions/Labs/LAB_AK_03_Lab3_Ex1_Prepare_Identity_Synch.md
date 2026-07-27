# [ラーニング パス 3 - ラボ 3 - 演習 1 - ID 同期の準備](https://github.com/ctct-edu/ms-102-lab/blob/main/Instructions/Labs/LAB_AK_03_Lab3_Ex1_Prepare_Identity_Synch.md#learning-path-3---lab-3---exercise-1---prepare-for-identity-synchronization)

前のラボ演習と同様に、Adatum Corporation の新しい Microsoft 365 管理者である Holly Dickson の役割を引き受けます。Adatum は最近 Microsoft 365 をサブスクライブし、あなたは Adatum の仮想化されたラボ環境にアプリケーションを展開する任務を与えられました。このラボでは、Microsoft 365 管理センターと Windows PowerShell の両方を使用して、Microsoft 365 ID 環境を管理するために必要なタスクを実行します。

この演習では、Azure AD Connect をセットアップして管理します。オンプレミス ユーザーを作成し、その ID がクラウドに移動されるように同期プロセスを検証します。ユーザーとグループのメンテナンス手順の中には、以前の演習でおなじみのものもあるかもしれません。ただし、この場合、同期プロセスを検証するために必要です。

### タスク 1: UPN サフィックスを構成する

Active Directory では、デフォルトのユーザー プリンシパル名 (UPN) サフィックス (つまり、テナント プレフィックス) は、ユーザー アカウントが作成されたドメインの DNS 名です。Azure AD Connect ウィザードでは UserPrincipalName 属性を使用するか、Azure AD でユーザー プリンシパル名として使用するオンプレミス属性 (カスタム インストールの場合) を指定できます。これは、Azure AD へのサインインに使用される値です。

思い出してください。VM 環境は、 adatum.com というタイトルのオンプレミス ドメインを使用して、ラボ ホスティング プロバイダーによって作成されました。このドメインには、Holly Dickson、Laura Atkins など、いくつかのオンプレミス ユーザー アカウントが含まれていました。次に、このコースの前半のラボで、 WWLxZZZZZZ.onelearndns.com という名前の Adatum 用のカスタム承認済みドメインを作成しました 。

 このタスクでは、PowerShell を使用して、最初に確立されたadatum.com ドメインをカスタム WWLxZZZZZZ.onelearndns.com ドメインに置き換えることにより、Adatum Corporation 全体のドメインのユーザー プリンシパル名を変更します。その際、プライマリ ドメインの UPN サフィックスと、AD DS のすべてのオンプレミス ユーザー アカウントの UPN を @WWLxZZZZZZ.onelearndns.com で更新します。

1. **Adatum のドメイン コントローラーであるLON-DC1** に切り替えます。ここでも **ADATUM\Administrator** およびパスワード **Pa55w.rd** としてログインしているはずです。

2. Windows PowerShell がまだ開いている場合は、タスクバーの **PowerShellアイコンを選択します。** それ以外の場合は、タスクバーの虫眼鏡 (検索) アイコンを選択し、表示される検索ボックスに「power」と入力し、Windows PowerShellを右クリックし、 [Run as administrator] を選択して、 Windows PowerShell を開く必要があります。ドロップダウン メニュー。Windows PowerShell が開いたら、ウィンドウを最大化します。

4. Windows PowerShell を使用して、オンプレミスの adatum.com ドメインを WWLxZZZZZZ.onelearndns.com ドメインに置き換える必要があります。その際、プライマリ ドメインの UPN サフィックスと、AD DS 内のすべてのユーザーの UPN を WWLxZZZZZZ.onelearndns.com で更新します。

   次の PowerShell コマンドでは、 Set-ADForest コマンドレットは Active Directory フォレストのプロパティを変更し、 -identity パラメーターは変更する Active Directory フォレストを指定します。 このタスクを実行するには、**次のコマンドを実行して、 adatum.comフォレストの  UPNSuffixes プロパティを設定します (WWLxZZZZZZ を一意の UPN 名に変更することを忘れないでください) 。** 

   ```
    Set-ADForest -identity adatum.com -UPNSuffixes @{replace="WWLxZZZZZZ.onelearndns.com"}
   ```

4. 次に、**次のコマンドを実行して、既存のすべての adatum.com アカウントを新しい UPN @xxxUPNxxx.xxxCustomDomainxxx.xxx ドメインに変更する必要があります  (WWLxZZZZZZ を一意の UPN 名に変更することを忘れないでください) 。**

   ```
    Get-ADUser -Filter * -Properties SamAccountName | ForEach-Object { Set-ADUser $_  -UserPrincipalName ($_.SamAccountName + "@WWLxZZZZZZ.onelearndns.com" )}
   ```

   
