---
# You can also start simply with 'default'
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://cover.sli.dev
# some information about your slides (markdown enabled)
title:
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# apply unocss classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
# take snapshot for each slide in the overview
overviewSnapshots: true
---

## Python 3.13 が正式リリースされました！

---
transition: fade-out
---

# 自己紹介

### 氏名（しめい）

- ソフトウェアエンジニア
- Go, Python, Terraform, AWS, TypeScript, Next.js
- 出身
- インターネット名は
- X: 
- カメラ・映像, 音楽, 旅行, サッカー
- 好きな技術はメディア系


---
transition: fade-out
---

# cryptライブラリが削除になりました

> Deprecated since version 3.11, will be removed in version 3.13: 
> The crypt module is deprecated (see PEP 594 for details and alternatives). 
> The hashlib module is a potential replacement for certain use cases. 
> The passlib package can replace all use cases of this module.

> バージョン3.11から非推奨、バージョン3.13で削除予定: 
> cryptモジュールは非推奨です（詳細と代替案についてはPEP 594を参照）。
> hashlib モジュールは、特定のユースケースを置き換える可能性があります。
> passlib パッケージは、このモジュールのすべてのユースケースを置き換えることができます。


---
transition: fade-out
---

# cryptライブラリが削除になりました


```py
import crypt

# ハッシュ化する文字列
text_to_hash = "example_string"

# ハッシュ化
hashed_text = crypt.crypt(text_to_hash)

# ハッシュ化された文字列を出力
print(hashed_text)
```

```
> python --version
Python 3.12.2
> python crypt-sample.py
~/crypt-sample.py:1: DeprecationWarning: 'crypt' is deprecated and slated for removal in Python 3.13
  import crypt
2l8sVfz6U2EM2
```

---
transition: fade-out
---

# hashlib または passlibを使いましょう


```py
import hashlib

# ハッシュ化する文字列
text_to_hash = "example_string"

# ハッシュ化
hashed_text = hashlib.sha256(text_to_hash.encode()).hexdigest()

# ハッシュ化された文字列を出力
print(hashed_text)
```

```
> python crypt-sample.py
9bfb55a8406617ff3e6767ec5d27fc6b5682c3a79c415ef6e084bf7d050273e6
```

---
layout: center
class: text-center
---

# Thank you for listening!

<PoweredBySlidev mt-10 />
