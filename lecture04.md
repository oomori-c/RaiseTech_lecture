# 第4回課題
## VPCの作成
<img width="1344" alt="スクリーンショット 2023-11-23 23 55 10" src="https://github.com/oomori-c/RaiseTech_lecture/assets/149781833/6e264629-f19e-492a-9099-2fcd3f4f7e87">

## EC2作成
<img width="1184" alt="スクリーンショット 2023-11-23 22 51 44" src="https://github.com/oomori-c/RaiseTech_lecture/assets/149781833/f06a0439-1da6-44a0-b8ec-5b96bed8fbd9">

### セキュリティグループ
インバウンドルールは、カスタム IPで限定的に設定しました。

<img width="1256" alt="スクリーンショット 2023-11-23 23 31 36" src="https://github.com/oomori-c/RaiseTech_lecture/assets/149781833/10809764-d00a-4277-8013-fb76e077d9a6">

<img width="1377" alt="スクリーンショット 2023-11-23 23 04 04" src="https://github.com/oomori-c/RaiseTech_lecture/assets/149781833/9aa60334-47c0-4cd2-8b01-2fa6f8356068">

## RDS作成

<img width="1371" alt="スクリーンショット 2023-11-23 23 17 50" src="https://github.com/oomori-c/RaiseTech_lecture/assets/149781833/c0453e71-1b72-4b58-98d8-d128b840bc7c">


### RDSのセキュリティグループ
<img width="1417" alt="スクリーンショット 2023-11-23 23 24 03" src="https://github.com/oomori-c/RaiseTech_lecture/assets/149781833/dcb1301a-eebc-43ed-b064-b25aa44d0c57">

## EC2からRDSへ接続確認
<img width="1074" alt="スクリーンショット 2023-11-23 22 35 14" src="https://github.com/oomori-c/RaiseTech_lecture/assets/149781833/edc45f0c-d8ae-4494-81af-6110bf3f3c64">


## 第4回課題で学んだこと
### サブネットについて
パブリックサブネットとプライベートサブネットの２種類がある　　

* パブリックサブネット：インターネットに繋がる(公開する)サブネット
* プライベートサブネットワーク：インターネットに繋がらない(非公開の)サブネット

### CIDRについて
* アドレスクラスの概念を取り払った仕組み
* CIDRではサブネットマスクの値を好きに決められる
* 198.xx.xxx.xxx/24のような形式をCIDR表記と言い、/24の部分がサブネットマスクを表している
*　VPCのCIDRブロックは、「10.0.0.1 ～ 10.0.0.14」の範囲でIPアドレスが使用できる　　
    * 先頭（ネットワークアドレス）と終端（ブロードキャストアドレス）は使用不可

### セキュリティグループについて
* TCP/IP  を元にしたアクセス制限を行うための設定
* EC2用、RDS用と細かい単位で分けることが多い。
* セキュリティグループは、使い回しも可能だが、用途や役割によって、設計の段階で制限を事前に決めておくと良い。
