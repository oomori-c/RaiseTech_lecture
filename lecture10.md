
# 第10回課題

## CloudFormation を利用して、現在までに作った環境をコード化

* ３つのyamlファイルに分けてテンプレートを作成  

| テンプレート名 | 作成したリソース |
| - | - |
| Network.yml | VPC<br>IGW<br>サブネット（パブリックサブネット２つ、プライベートサブネット２つ）<br>ルートテーブル |
| SecurityGroup.yml | EC2セキュリティグループ<br>RDSセキュリティグループ<br>ALBセキュリティグループ |
| Application.yml | EC2インスタンス<br>RDS<br>DBサブネットグループ<br>ALB<br>ALBターゲットグループ<br>リスナールール<br>S3バケット<br>IAMロール、ポリシー |

### Network.yml

![Network_yaml](lecture10/images/Network_yaml.png) 

#### リソース確認　　

- VPC,リソースマップ
    ![VPC](lecture10/images/VPC.png) 

### SecurityGroup.yml

![SecurityGroup_yml](lecture10/images/securitygroup_yml.png)

#### リソース確認　　

- EC2セキュリティグループ
    ![EC2_sg](lecture10/images/Ec2_sg.png)

- RDSセキュリティグループ
    ![RDS_sg](lecture10/images/rds_sg.png)

- ALBセキュリティグループ
    ![ALB_sg](lecture10/images/ALB_sg.png)

### Application.yml

![Application_yml](lecture10/images/Application_yml.png)

#### リソース確認

- EC2  
    ![EC2](lecture10/images/EC2.png)

- RDS
    ![RDS](lecture10/images/RDS.png)

- ALB
    ![ALB](lecture10/images/ALB_1.png)

    - ターゲットグループ
        ![ALB_tg](lecture10/images/ALB_tg.png)

- S3
    ![S3](lecture10/images/S3-bucket.png)

- IAMロール
    ![IAM](lecture10/images/IAM_role.png)

### EC2からRDSへ接続確認

![setuzoku](lecture10/images/setuzoku.png)


## テンプレート作成時に使用したVScodeの拡張機能

- **indent-rainbow-blocks**  
    インデントの色づけ

- **CloudFormation Snippets**  
    CloudFormationのリソースなど、自動で入力補助してくれる

- **CloudFormation**  
    startと入力するとテンプレートの要素を自動で入力してくれる

- **YAML**  
    yaml言語のサポート

## 学んだこと

* CloudFormationやInfrastructure as Codeについて、何となく苦手意識があり学習が進まなかったが、下記の動画と記事で苦手意識が減った。  
    全体の概要やよくあるミス等を見てから、どこでつまづきやすいのかを把握してから書き始めてみると、比較的導入しやすかった。  
    https://dev.classmethod.jp/articles/the_first_cloudformation/
    
* スペースインデントの数を間違えて、何度もやり直しとなった。  
    VScodeの拡張機能「**indent-rainbow-blocks**」でインデントを色づけすることで階層を把握して、解決した。  

* 論理IDは理解できたが、テンプレートの『Parameters』の意味を理解するのに時間がかかった。  
    下記の記事が参考になった。  
    https://qiita.com/okubot55/items/b18a5dd5166f1ec2696c
