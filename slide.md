### 表参道.rb #32
- - -
## RSpec x Vim

---

## 自己紹介
- - -

* なまえ  : おしょー
* Twitter : [@pink_bangbi](https://twitter.com/pink_bangbi)
* github  : [osyo-manga](https://github.com/osyo-manga)
* ブログ  : [Secret Garden(Instrumental)](http://secret-garden.hatenablog.com)
* Ruby（ﾁｮｯﾄ on Rails）
  * 役に立たない gem をつくってる
  * Ruby にパッチ投げつけてる

---

## [今年作った gem](https://rubygems.org/profiles/osyo-manga)
- - -

* [toplevel](https://github.com/osyo-manga/gem-toplevel)
  * ファイルローカルメソッドみたいなのを定義する
* [ruboty-tenki](https://github.com/osyo-manga/gem-ruboty-tenki)
  * Ruboty でお天気情報を返す bot
* [binding-debug](https://github.com/osyo-manga/gem-binding-debug)
  * `変数名 : 値` 形式でいい感じにデバッグ出力する

---

## 今日話す内容
## RSpec x Vim

---

## RSpec とは
- - -

Ruby で利用されているテストフレームワーク。DSL ぽく記述できるのが特徴
>>>

```ruby
describe Array do
	context "#empty?" do
		it { expect([].empty?).to eq true }
		it { expect([1].empty?).to eq false }
	end

	context "size" do
		it { expect([1].size).to eq 1 }
		it { expect([1, 2].size).to eq 2 }
		it { expect([1, 2, 3].size).to eq 3 }
	end

	context "[]" do
		subject { [1, 2, 3] }
		it { expect(subject[0]).to eq 1 }
		it { expect(subject[1]).to eq 2 }
		it { expect(subject[2]).to eq 3 }
	end
end
```

---

## RSpec を実行する
- - -

* spec ファイルを複数実行
  * $ rspec *
* spec ファイルを指定して実行
  * $ rspec hoge_spec.rb
* spec ファイルの行数を指定して
  * $ rspec hoge_spec.rb:3
* 今回は rake から実行する方法については置いておく

---

## 今日やること
## Vim から RSpec を実行する

---

## 具体的にやりたいこと
- - -

* Vim で現在開いている rspec ファイルを実行する
  * 実行には quickrunv.vim を使う
* カーソル位置のテストを実行する
>>>

## 設定例
- - -

```vim
let g:quickrun_config = {
\	"_" : {
\		"outputter/buffer/split" : ":botright 10sp",
\	},
\	"ruby.rspec" : {
\		"command" : "rspec",
\		"exec"    : "%c %s:p",
\	},
\	"ruby.rspec/on_cursor" : {
\		"command" : "rake",
\		"exec"    : "%c %s:p:%{line('.')}",
\		"hook/close_buffer/enable_failure" : 0,
\	},
\}
```

---


### まとめ
- - -

* テストの量が増えてくると実行時間が長くなってくる
* そういう場合は局所的にテストを実行したほうが効率がいい
* エディタ上からテストを実行できると更に効率がいい
* Vim を使っている人は端末からコマンドを打つのではなくて quickrun.vim を使うといいよ！

---

## ご清聴
## ありがとうございました
