## usersテーブル

|Colum                    |Type        |Options                         | 
|-------------------------|------------|--------------------------------|
|name                     |string      |null: false                     |
|email                    |string      |null: false, unique: true       |
|encrypted_password       |string      |null: false                     |
|team_id                  |references  |null: false, foreign_key: true  |
### Association

has_many :teams, through: :team_users
has_many :team_users
has_many :posts
has_many :comments





## team_usersテーブル

|Colum                    |Type       |Options                          | 
|-------------------------|-----------|---------------------------------|
|user_id                  |references |null: false, foreign_key: true   |
|team_id                  |references |null: false, foreign_key: true   |

### Association
belongs_to :user
belongs_to :team





## teamsテーブル

|Colum                    |Type       |Options                          | 
|-------------------------|-----------|---------------------------------|
|name                     |string     |null: false                      |
|user_id                  |references |null: false, foreign_key: true   |


### Association
has_many :users, through: :team_users
has_many :team_users
has_many :posts








## postsテーブル

|Colum                    |Type       |Options                          | 
|-------------------------|-----------|---------------------------------|
|date                     |date       |null: false                      |
|text                     |text       |null: false                      |
|user_id                  |references |null: false, foreign_key: true   |
|team_id                  |references |null: false, foreign_key: true   |

### Association
belongs_to :user
belongs_to :team
has_many :comments








## commentsテーブル

|Colum                    |Type       |Options                          | 
|-------------------------|-----------|---------------------------------|
|text                     |text       |null: false                      |
|user_id                  |references |null: false, foreign_key: true   |
|post_id                  |references |null: false, foreign_key: true   |

### Association
belongs_to :user
belongs_to :post, dependent: :destroy
has_many :comments



# アプリケーション名	TeamLabo
## アプリケーション概要	スポーツチーム（学生の部活など）の日々の練習、予定、チームの課題、個人の課題、練習の意図などについて、メンバーがコメントをすることによって記録し、考えてプレーすることを習慣付けることによって、チームと個人の実力を向上するアプリ。

 URL	デプロイ済みのURLを記述しましょう。デプロイが済んでいない場合は、デプロイ次第記述しましょう。

 テスト用アカウント	ログイン機能等を実装した場合は、記述しましょう。またBasic認証等を設けている場合は、そのID/Passも記述しましょう。


### 利用方法	 まずユーザー登録をします。ログインしたユーザーは新規チーム作成、メンバーの招待、投稿、コメント、予定作成ナデができます。


### 目指した課題解決	このアプリケーションを通じて、主に部活などでチームスポーツをする学生が、頭で考えてプレーすることを習慣付けること。それに加え、日記を書くことで自分の状況を言語化し、客観視することによって人として成長できるアプリ。


 洗い出した要件	スプレッドシートにまとめた要件定義を、マークダウンで記述しなおしましょう。


 実装した機能についてのGIFと説明	実装した機能について、それぞれどのような特徴があるのか列挙しましょう。GIFを添えることで、イメージがしやすくなります。


### 実装予定の機能	外部APIを用いて、他のSNSと連携してユーザー登録、ログインできるようにする。動画を投稿できるようにする。また、投稿された動画に対してコメントできるようにする。

 データベース設計	ER図等を添付しましょう。


 ローカルでの動作方法	git cloneしてから、ローカルで動作をさせるまでに必要なコマンドを記述しましょう。この時、アプリケーション開発に使用した環境を併記することを忘れないでください（パッケージやRubyのバージョンなど）。