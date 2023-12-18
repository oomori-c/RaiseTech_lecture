
# CloudTrail

## 最後にログインしたイベントをピックアップ

- EC2起動  
![start instance](images/startinstances.png)    
![EC2起動](images/ec2kidou.png)    
  
## 見つけたイベントの中に含まれている内容３つ

![JSON](images/event_json.png)  

- "eventTime": "2023-12-14T05:48:40Z",  
    イベントが行われた時間。  
    時差があるため、UTC 05:48:40は、JST(日本標準時)で、14:48:40  
  
- "eventSource": "ec2.amazonaws.com",  
    リクエストが行われたサービス：EC2  
  
- "eventName": "StartInstances",  
    リクエストされたアクション：インスタント起動  
  
## 学んだことメモ

誰が、いつ、何を操作したかがイベントとして記録されている。  

- 誰が：**`userIdentity`、`sourceIPAddress`**
    リクエストを作成した IAM アイデンティティ、IPアドレス  
    （IPアドレスから、より詳しく特定する情報はプロバイダに開示してもらわないといけないが）  

- いつ：**`eventTime`**
    リクエストが完了した日付と時刻、協定世界時 (UTC)
    ※時差注意必要

- 何を：**`eventSource`**、**`eventName`**  
    リクエストが行われたサービス、アクション  

# CloudWatchアラームを使って、ALBのアラームを設定

1. Amazon SNS作成  
![amazon sns](images/amazonsns.png)  
  
2. EC2のターゲットグループがunhealthyになったらアラート通知  
![アラート通知](images/alertmail.png)  
  
3. Railsアプリケーションに接続　　
    ![Rails](images/railsapp.png)  
    　　
    ターゲットグループが正常に変わった　　
    ![代替テキスト](images/albok.png)
  
4. OKアクションでの通知  
    ![OKアクション](images/ok.png)  
    グラフ状態  
    ![graph](images/graph.png)  
  
# コスト管理について

## AWS見積もり

[これまで使用した内容のリソースを見積もり作成](https://calculator.aws/#/estimate?id=437fcaa5fbcc21d65d970cebec9bebbc27afe3e1)  

## 先月の請求書確認

- 11月  
    ![billing](images/november_billing.png)  
    EC2で無料枠内越え、$1.44かかってしまった。  

    ![billing statement](images/november_billing_ec2.png)  
    - ネットの情報でEC2へのアクセス方法を見て、真似てみた際、本来使う予定のなかったElastic IPを設定してしまい、無料枠内を越えてしまった。  
    - 過去の課題取り組み時、誤ってシドニーのリージョンで作成してしまった。リージョンが変わると、価格帯が違うので注意する。  




