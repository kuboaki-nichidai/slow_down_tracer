:encoding: utf-8
:lang: ja
:scripts: cjk
:media: prepress
:linkcss:
:stylesdir: css
:stylesheet: mystyle.css
:sectanchors:
:autofit-option:
:experimental:
:support-uri:
:original-support-uri:
:twoinches: width='360'
:full-width: width='100%'
:three-quarters-width: width='75%'
:two-thirds-width: width='66%'
:half-width: width='50%'
:half-size:
:one-thirds-width: width='33%'
:one-quarters-width: width='25%'
:thumbnail: width='60'
:imagesdir: images
:sourcesdir: codes
:icons: font
:hide-uri-scheme!:
:figure-caption: 図
:example-caption: リスト
:table-caption: 表
:appendix-caption: 付録
:xrefstyle: short
:section-refsig:
:chapter-refsig:


= slow_down_tracer

NOTE: この演習は、グループで相談しつつ、各自が実施します。

自動搬送ロボットを徐行できるようにする。

== 準備

. `sample04` のコードをディレクトリごと複製して `sample04_slow_down` を用意しなさい。
. `sample04.asta` を複製して、`sample04_slow_down.asta` を用意しなさい。
. クラス図の名前を、 `sample04_slow_downのクラス図` に変更しなさい。


== クラス図を修正する

. クラス図を参照して、`driver` クラスに、走行速度を変更する操作 `set_speed: void` を追加しなさい。
. クラス図を参照して、`tracer` クラスに、経路に沿って徐行する操作 `run_slow: void` を追加しなさい。

== ステートマシン図を修正する

. `Porter` のステートマシン図を修正して、荷物が載った後のアクションで「経路に沿って走行する」代わりに「経路に沿って徐行する」に変更しなさい。


== 修正を保存する

==== sample04_slow_downのモデル図を保存しなさい

作成したクラス図を `sample04_slow_down_class_01.png` として `images` ディレクトリに保存しなさい。

. 「ツール＞画像出力＞現在の図」で、保存用ダイアログを開く。
. 作成したクラス図を `sample04_slow_down_class_01.png` として `images` ディレクトリに保存する（ダミー画像ファイルになっているので、置き換える）

.`sample04_slow_down` のクラス図（保存できたら置き換わる）
image::sample04_slow_down_class_01.png[{full-width}]

ここまで編集したら、このファイル（ `README.adoc` ）を保存し、ターミナルからgitコマンドを使ってコミットしなさい。


==== sample04_slow_downのステートマシン図を保存しなさい

作成したクラス図を `sample04_slow_down_stm_01.png` として `images` ディレクトリに保存しなさい。

.`sample04` のステートマシン図（保存できたら置き換わる）
image::sample04_slow_down_stms_01.png[{full-width}]


ここまで編集したら、このファイル（ `README.adoc` ）を保存し、ターミナルからgitコマンドを使ってコミットしなさい。

==== 編集結果を保存する

このファイル（ `README.adoc` ）を保存し、ターミナルからgitコマンドを使ってプッシュしなさい。


== driverのコードを修正する

`driver` のコードを修正しなさい。

* `driver` が使うPOWERの定義について、通常走行用の他に徐行用のものを定義しなさい。
* `driver` に `set_power` を追加して、現在使うPOWERを変更するようにしなさい。
* `driver` の `forward` `turn_left` 等が、`set_power` による変更が反映されるか、確認しなさい。

== traerのコードを修正する

`tracer` のコードを修正しなさい。

* `tracer` の `run` を `driver` の操作を呼び出す前に、 `driver` の `set_power` を呼び出して、通常走行のPOWERを使うように修正しなさい。
* `tracer` の `run` を複製して `run_slow` を追加しなさい。
* `tracer` の `run_slow` を `driver` の操作を呼び出す前に、 `driver` の `set_power` を呼び出して、徐行のPOWERを使うように修正しなさい。

== ビルドして実験する

. 修正したプログラムをビルドして転送して、実行しなさい。

== 修正したコードを保存する

==== sample04_slow_downのコードをリポジトリに保存しなさい

. 動作確認できたら、`codes` ディレクトリに、`sample04_slow_down` ディレクトリをコピーしなさい。

この `README.adoc` のテキストの下記部分を編集して、`tracer_run` と `tracer_run_slow` の範囲を指定して表示できるようにしなさい。そのためには、 `[lines=1..27]` という部分を、みなさんが修正したコードの該当する行範囲に変更します。`define` の追加なども含めておきます。

[[sample04_slow_down_app_c_1]]
.`sample04/app.c`(1)（`tracer_run` と `tracer_run_slow`）
[source,ruby,linenums]
----
include::{sourcesdir}/sample04_slow_down/app.c[lines=1..27]
----

==== 編集結果を保存する

ここまで編集したら、このファイル（ `README.adoc` ）を保存し、ターミナルからgitコマンドを使ってコミットしなさい。

このファイル（ `README.adoc` ）を保存し、ターミナルからgitコマンドを使ってプッシュしなさい。
