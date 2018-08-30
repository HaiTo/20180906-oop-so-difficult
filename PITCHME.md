## OOPをした気持ちになる人達へのお手紙
HaiTo

---
## Abount me
Name: HaiTo
Career:
  2014/5 Sansan インターン(Ruby)
  2015/4 Sansan 正社員(Ruby)
  2017/1 MoneyForward 正社員(Ruby)
  2018/6 Mercari 正社員(PHP)
Hobby: Game(Leangue of Legends)

---
## 結論
> 俺が悪かった。素直に間違いを認めるから、もうFormObjectとか作るのはやめてくれ。    
> 元ネタ: https://qiita.com/joker1007/items/25de535cd8bb2857a685

**僕はFormObjectが嫌いです** というのを言いたいだけです。  
すべてのContext、Service、チームで当てはまるわけじゃないって言ったら当てはまるわけじゃない。

---
## Context
- 古今東西、Railsの標準的なMVC、特にModelの取扱について悩んでいる人間がたくさんいる。
- ServiceClass、FormObject、Decorator、……
- Modelになにか別の層を追加することで、凝集度を高める、あるいはテスタビリティを高める、Modelの肥大化を防ぐ
- いろんな思惑の上でこれまでたくさんの仕組みがRailsの上に乗ってきた
- FormObject もたくさんの場所で見る事ができた一つだ

---
## Subject
- FormObjectをなんのために、どうして導入するのか考え直してほしい。
- 声に出して呼んでほしい。
- Form Object 、 ふぉーむ おぶじぇくと。

---
## なぜ僕がFormObjectを嫌いなのか
- はい。声に出して読みましたか？ Form Object。
- 以下のようなFormObjectをよく見ますね(ウェブで)
- `Form::Base` が AM::Model とかを `include` しているとする

```ruby
class Form::Registration < Form::Base
  attribute :want_email_notification, :bool, default: true
  
  def register!
    validate!
    # 複数のモデルや複雑な保存処理
  end
  
  private 
  
  def validate!
    super
    # なんか適当な処理
  end
end
```
