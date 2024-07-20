# SimpleTemplate Change Log

## ver 1.0.8
1.<include file='some.tpl'>の再帰的インクルード  
インクルードしたテンプレートファイルに<include file='some.tpl'>がある場合に、再帰的にテンプレートのインクルード処理をする

2.不具合修正
特定のパターン</{\$([\w.-_?&=]+)(\s*)\|(\s*)default:(\s*)[\'|"](.*)[\'|"]}/U>にマッチした場合にアサインされているテンプレート変数も設定したデフォルト値が表示されてしまう不具合を修正  

3.改修  
ifステートメントの実行プロセスにて①数値、②文字列を判別して$ifstatementを設定するように改修

4.{if}{elseif}{/if}構文の機能追加

5.不具合修正  
アサインされたテンプレート変数の一部が同一の場合（例：$message1と$message10）を区別して処理するように修正

6.改修  
{if}{/if}処理および{if}*{elseif}*{/if}処理にて改行を入れることが出来るように改修

7.改修  
assgin構文でvalue='someString'とすると「'someString」が変数に割り当てられる不具合を修正

8.改修  
default値の表示が、テンプレート変数が未アサインの場合にだけ表示されるように修正

9.機能追加  
出力エンコーディングを設定する機能を追加（プロパティー・メソッドの追加）

10.機能追加  
テンプレート記述エンコーディングを設定する機能を追加（プロパティー・メソッドの追加）

11.機能追加  
setTplEncordingメソッドにmb_stringにてサポートされいる文字エンコーディングかどうかのチェック機能を追加

12.機能追加  
setOutputEncordingメソッドにmb_stringにてサポートされいる文字エンコーディングかどうかのチェック機能を追加

13.プロパティー名・メソッド名変更  
【変更前】  
＜プロパティー＞$_tplEncording,$_outputEncording  
＜メソッド＞setTplEncording,setOutputEncording  
【変更後】  
＜プロパティー＞$_tplEncoding,$_outputEncoding  
＜メソッド＞setTplEncoding,setOutputEncoding  

## ver 1.0.9
1.プロパティー宣言部の修正  
プロパティー（$_tplEncoding,$_outputEncoding）宣言部の「var」を「private」に変更

2．ifステートメント修正  
ifステートメントのパターン文字列の修正　※修正前はhtmlタグ（/）が入るとそのまま文字列を表示してしまう。  
（変更前）$pattern_ifstatement = '/{if (.*)}((.*)){\/if}/U';　＜418行＞  
（変更後）$pattern_ifstatement = '/{if (.*)}([\s\S]*){\/if}/U';　＜418行＞

## ver 1.0.10
1.ifステートメントにおいて、htmlコードを認識しないバグを修正  

## ver 1.0.11
1.{foreach}、{section}構文内での{if}構文の実装

## ver 1.1.0
1.キャッシュ機構の追加  
【仕様】  
※displayメソッドにて処理定義  
1.キャッシュファイルの作成タイムスタンプ取得  

2．テンプレートファイルの更新タイムスタンプ取得  
　①インクルードファイル  
　②テンプレートファイル自身  
　　　　　　↓  
　最新のタイムスタンプ取得

3.キャッシュファイルとテンプレートファイルのタイムスタンプ比較  
　①キャッシュファイル＞テンプレートファイル  
　　⇒キャッシュファイルの出力  
　②キャッシュファイル＜テンプレートファイル  
　　⇒テンプレートファイル処理　⇒　キャッシュファイル作成 ※unlinkとmakefile  
　　⇒キャッシュファイルの出力  

※キャッシュファイル名命名規則  
　⇒some.cch  
【追加プロパティー】  
$_cacheDir  
【追加メソッド】  
function setCacheDir($path)  
【修正メソッド】  
function display()  

## ver 1.1.1
1.ループ構文(foreach/section)内で、ループインデックス(index)を参照出来るように改修

