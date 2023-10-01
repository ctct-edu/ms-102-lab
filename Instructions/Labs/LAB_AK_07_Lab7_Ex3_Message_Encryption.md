# [ラーニング パス 7 - ラボ 7 - 演習 3 - メッセージ暗号化ルールの作成](https://github.com/MicrosoftLearning/MS-102T00-Microsoft-365-Administrator-Essentials/blob/master/Instructions/Labs/LAB_AK_07_Lab7_Ex3_Message_Encryption.md#learning-path-7---lab-7---exercise-3---create-message-encryption-rules)

このラボでは、Adatum の新しい Microsoft 365 管理者である Holly Dickson の役割を果たします。あなたは、Adatum の Microsoft 365 導入で Microsoft 365 メッセージ暗号化の使用を試験的に試験する任務を与えられました。メッセージ暗号化ルールは Exchange Online と Windows PowerShell の両方を使用して作成できるため、各方法をテストして、運用開始後にどちらを使用するかを決定することにしました。

この演習では、Exchange 管理センターと Windows PowerShell の両方を使用してメール フロー暗号化ルールを作成する方法を学習します。

### [タスク 1 – Exchange 管理センターを使用してメール フロー暗号化ルールを作成する](https://github.com/MicrosoftLearning/MS-102T00-Microsoft-365-Administrator-Essentials/blob/master/Instructions/Labs/LAB_AK_07_Lab7_Ex3_Message_Encryption.md#task-1--create-a-mail-flow-encryption-rule-using-the-exchange-admin-center)

このタスクでは、Exchange 管理センターを使用して、Exchange Online 環境内のメッセージの暗号化ルールを作成します。次のタスクでは、代わりに PowerShell を使用して同じことを行います。

1. LON-CL1 では、Edge ブラウザーで、**Holly Dickson**として Microsoft 365 にログインしているはずです。

2. **Microsoft 365 管理センター**の左側のナビゲーション ウィンドウで、 [**すべて表示**] (必要な場合) を選択し、**[管理センター]で****[Exchange]**を選択します。これにより、Exchange Online 管理センターが開きます。

3. **Exchange 管理センター**の左側のナビゲーション ウィンドウで**[メール フロー]**を選択してこのグループを展開し、**[ルール]**を選択します。

4. **[ルール]**ページで、メニュー バーの**[+ルールの追加]を選択して、新しいルールを作成します。**これにより、アクションのドロップダウン メニューが表示されます。**「新しいルールの作成」**を選択します。これにより、**新しいトランスポート ルール**ウィザードが開始されます。

5. **新しいトランスポート ルール**ウィザードの**[ルール条件の設定]**ページで、 **[名前]**フィールドに「 **[guest@adatum.com](mailto:guest@adatum.com)****のメールを暗号化」**と入力します。

6. **「このルールを適用する場合」**条件の下に 2 つのフィールドが表示されます。最初のフィールドを選択します。表示されるドロップダウン メニューで、**受信者を**選択します。

   2 番目のフィールドを選択します。表示されるドロップダウン メニューで、 [**この人です]**を選択します。この条件では、ユーザー リストから既存の名前を選択するか、[**メンバーの選択]**フィールドに新しい電子メール アドレスを入力する必要があります。この場合、**「メンバーの選択」**フィールドに**[「guest@adatum.com」](mailto:guest@adatum.com)**と入力します。**表示されるguest@adatum**フィールドを選択し、**[保存]**を選択します。

7. ここで追加の条件を追加する必要があるため、**「この人物です**」フィールドの右側に表示される**プラス記号 (+)**を選択します。

8. 2 番目の条件が**And**見出しの下にどのように表示されるかに注目してください。この 2 番目の条件では、最初のフィールドを選択し、ドロップダウン メニューから**[受信者]を選択します。**2 番目のフィールドを選択します。表示されるドロップダウン メニューで、**外部/内部を選択します。**

9. **[受信者の場所の選択**] ダイアログ ボックスで、ドロップダウン矢印を選択します。ドロップダウン メニューで、[**組織外]**を選択し、**[保存] を選択します。**

10. 次に、このルールが適用されたときに実行するアクションを定義する必要があります。**「次の操作を実行します**」セクションで、最初のフィールドを選択します。表示されるドロップダウン メニューで、 [**メッセージ セキュリティの変更]**を選択します。2 番目のフィールドを選択します。表示されるメニューで、[ **Office 365 メッセージの暗号化と権利保護を適用する] を選択します。**

11. **[RMS テンプレートの選択]**ダイアログ ボックスで、ドロップダウン矢印を選択し、 [**暗号化]**を選択して、**[保存]**を選択します。

12. **「ルール条件の設定」**ページに戻ります。このルールには例外を定義しないため、ルールの**「Except if」セクションは更新しません。****「次へ」**を選択します。

13. **[ルール設定の設定]**ページで、**ルール モードが****[強制]**に設定されていることを確認します(まだ選択されていない場合は、このオプションを選択します)。**[重大度]**フィールドを選択し、ドロップダウン メニューから**[中]**を選択します。**「次へ」**を選択します。

14. **[確認して終了]**ページで、条件とルールの設定を確認します。値を変更する必要がある場合は、**「ルール条件の編集」**または**「ルール設定の編集」**を選択して、対応するフィールドを修正します。すべての条件と設定が正しい場合は、**[完了]**を選択します。

15. トランスポート ルールが正常に作成されたら、**[完了]**を選択します。

16. **これにより、 「ルール」**ページに戻るはずです。新しいルールがルールのリストに表示されない場合は、メニュー バーの**[更新]オプションを選択します。**

17. ブラウザのタブを開いたままにして、次のタスクに進みます。

### [タスク 2 – Windows PowerShell を使用してメール フロー暗号化ルールを作成する](https://github.com/MicrosoftLearning/MS-102T00-Microsoft-365-Administrator-Essentials/blob/master/Instructions/Labs/LAB_AK_07_Lab7_Ex3_Message_Encryption.md#task-2--create-a-mail-flow-encryption-rule-using-windows-powershell)

前のタスクでは、Exchange 管理センターを使用してメール フロー暗号化ルールを構成しました。このタスクでは、Windows PowerShell (具体的には Microsoft Graph PowerShell) を使用してメール フロー暗号化ルールを作成します。まず、Exchange Online PowerShell モジュール (ExchangeOnlineManagement) に接続する必要があります。このタスクで使用される**New-TransportRule**コマンドレットは Exchange Online コマンドレットであるため、これが必要です。そのため、このコマンドレットにアクセスするには、PowerShell を介して Exchange Online セッションに接続する必要があります。

1. LON-CL1 では、Edge ブラウザーで、**Holly Dickson**として Microsoft 365 にログインしているはずです。

2. Windows PowerShell がまだデスクトップ上で開いている場合は、タスクバーの PowerShell アイコンを選択して PowerShell ウィンドウを最大化します。ただし、PowerShell を最後に使用した後に閉じた場合は、タスク バーの**検索**ボックスに**「power」と入力し、表示されるメニューで****Windows PowerShell を**右クリックし、ドロップダウン メニューで [**管理者として実行]を選択します。**

3. **Windows PowerShell**では、コマンド プロンプトで次のコマンドを実行して、Exchange Online PowerShell モジュール (ExchangeOnlineManagement) をインストールすることから始める必要があります。

   インストール**モジュール - 名前 ExchangeOnlineManagement**

4. 信頼できないリポジトリ (PSGallery) からモジュールをインストールするかどうかを確認するメッセージが表示されたら、「**A 」と入力して****[A] すべてはいを**選択します。

5. 次に、コマンド プロンプトで次のコマンドを実行して、モジュールに接続する必要があります (注: コマンドでは、ラボ ホスティング プロバイダーから提供されたテナント名 (xxxxxZZZZZZ.onmicrosoft.com、xxxxxZZZZZZ はテナント) をコピーして貼り付ける必要があります)ラボ ホスティング プロバイダーによって割り当てられたプレフィックス):

   Connect **-ExchangeOnline -UserPrincipalName [holly@xxxxxZZZZZZ.onmicrosoft.com](mailto:holly@xxxxxZZZZZZ.onmicrosoft.com)**

6. **表示される[パスワードの入力]**ダイアログ ボックスで、ラボ ホスティング プロバイダーから提供された Microsoft 365 テナント管理者パスワードを入力し、 [**サインイン] を**選択します。

7. **ここで、 New-TransportRule**コマンドレットを使用してメール フロー ルールを作成し、 **ApplyRightsProtectionTemplate**プロパティを、使用可能な RMS テンプレートの 1 つである**Encrypt**に設定します。[このルールは、Adatum からGservices@adatum.com](mailto:Gservices@adatum.com)に送信されるすべての送信メールを暗号化します。

   このルールを作成するには、次のコマンドを実行します。

   **New-TransportRule -Name "ゲスト サービスの暗号化ルール" -SentTo " [Gservices@adatum.com](mailto:Gservices@adatum.com) " -SentToScope "NotinOrganization" -ApplyRightsProtectionTemplate Encrypt**

   **注:**このコマンドは完了するまでに数秒かかります。作成した新しいルールのプロパティが PowerShell に表示されるまで、次の手順に進まないでください。

8. ルールが存在することを確認するには、まず PowerShell ウィンドウを最小化します。**Microsoft Edge ブラウザでは、引き続きExchange 管理センターの****メール フロー**ウィンドウが表示され、**[ルール]**タブが表示されます。ルールのリストには、前のタスクで作成した**[「guest@adatum.com の](mailto:guest@adatum.com)****メールを暗号化する」ルールのみが表示されます。**

   ルールのリストの上に表示されるメニュー バーで、**[更新]**アイコンを選択します。更新されたリストには、PowerShell を使用して作成したばかりのルールも表示されます。

9. 次の演習のために Edge ブラウザを開いたままにしておきます。
