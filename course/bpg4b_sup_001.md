# BinjoCats Programming Guide for Beginners Supplement 001

メインの資料の中で紹介しきれていない、細々としたモノを解説する資料になります。  
今回はBPG4b 001～003 くらいの範囲に対応しています。

## 内容

- S1. 四則演算
- S2. インクリメント
- S3. 文字列埋め込み
- S4. n重ループ

## S1. 四則演算

```ruby
a = 12
b = 6
puts a + b  # 18 (足し算)
puts a - b  # 6 (引き算)
puts a * b  # 72 (掛け算)
puts a / b  # 2 (割り算)
puts a % b  # 0 (aをbで割った余り)
```

整数同士の割り算は整数での結果 (小数点以下切り捨て) が出ることに注意してください。  
たとえば、7 / 3 は実際には 2.333... ですが、Ruby上で `7 / 3` は 2 となります。

## S2. 複合代入

ある変数に別の値を代入するのではなく、その変数の値に直接何かしたいとき (`cnt`変数に1足したい、など) に用います。  
あらゆる算術演算子 `?` に対して、 `x ?= y` は `x = x ? y` と同じ意味です。

```ruby
x = 3
x += 1  # x = x + 1 (4)
x -= 1  # x = x - 1 (3)
x *= 1  # x = x * 1 (3)
x /= 1  # x = x / 1 (3)
x %= 1  # x = x % 1 (0)
puts x  # 0
```

## S3. 文字列埋め込み

文字列中に `#{変数名}` の記法をとることで、(型を気にせずに＝文字列でも数値でも) 変数の値を埋め込むことができます。

```ruby
s = "ル"
puts "黒澤#{s}ビィ"    # 黒澤ルビィ
i = 5
puts "黒澤#{i}ビィ"    # 黒澤5ビィ
```

## S4. n重ループ

for文やwhile文はいくつも重ねることができます。

```ruby
n = gets.to_i
for a in 1..10 do
  for b in 1..10 do
    for c in 1..10 do
      if a * b + c == n
        puts "#{a} x #{b} - #{c} = n"
      end
    end
  end
end
```

ここで、重なったループは「自分の中に含まれるループの回数 × 自分のループの回数」回の処理になることに注意してください。  
つまり、上の例では 10 × 10 × 10 回＝ 1000回の処理を行います。  
一般に、m回のループをn個重ねるとmのn乗回の処理を行います (これを俗にn重ループと呼びます) 。  
mが大きくなると (1億ほど)、たった2重のループでも何年もかかるような処理の回数になってしまうこともあります。ちなみにパソコンは1億回の計算をおよそ1秒でこなします。