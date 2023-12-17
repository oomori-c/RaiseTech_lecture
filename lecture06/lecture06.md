
# CloudTrail イベント履歴　　

## イベント名

### Startinstances  

* EC2起動
![EC2起動](image/ec2kidou.png)  
![startinstans](image/startinstances.png)  
  
  
## 含まれている内容３つ  

![json](image/event_json.png)  

1. "eventTime": "2023-12-14T05:48:40Z",  
    イベントが行われた時間。  
    9時間時差なので、UTC 05:48:40は、JST(日本標準時)で14:48:40  

2. "eventSource": "ec2.amazonaws.com",  
    リクエストが行われたサービス：EC2  

3. "eventName": "StartInstances",  
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

# ALBのアラーム設定

1. Amazon SNS作成  
![amazon sns](image/amazonsns.png)  

2. ALBターゲットグループがunhealthyの時にアラートメール通知  
![alert mail](image/alertmail.png)  


3. Railsアプリケーションが使える状態にする  
    ![rails](image/railsapp.png)  
    ターゲットグループが正常になった状態    
    ![alb_ok](image/albok.png)  



4. OKアクションの時のメール  
![ok_action](image/ok.png)  

![graph](image/graph.png)  
  


# コスト管理  

## AWS利用料の見積もり  

1. 今日までに作成したリソース内容の見積もり  
[見積もりはこちら](https://calculator.aws/#/estimate?id=437fcaa5fbcc21d65d970cebec9bebbc27afe3e1)  


2. 先月の請求書　billing  
    - 11月
        EC2で税抜で$1.44かかってしまった  
        
        ![billing](image/november_billing.png)  
        
        EC2の明細　　

        ![billing EC2](image/november_billing_ec2.png)  
        コストがかかってしまった要因は下記２点  
        - 初回、リージョンを間違えてシドニーで作成してしまい、無料枠内を超えてしまった  
        - ネットの情報でEC2へのアクセス方法を見て、真似てみた際、当初は使う予定のなかったElastic IPを設定してしまい、無料枠内を越えてしまった  






