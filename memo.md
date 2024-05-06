テスト駆動python

2.4 
    スモークテスト
    test関数に、@pytest.mark.{marker_name}のデコレータを指定することでスモークテスト対象にできる。
    pytest -m 'marker_name' でテスト対象をマーカーがついたもののみにすることができる
    pytest -m 'marker1 (or | and) marker2' などでandやorを取れる。

2.5
    skip
        test関数に@pytest.mark.skip()のデコレータを追加することでテストをskipできる。
        reason='reason_string'を指定することでスキップ理由を記載可能。reason指定は任意
    skipif
        @pytest.mark.skipif(expression,reason)でexpressionに合致するテストをスキップ対象にする。
        reasonの指定は必須
    pytest -rs
        スキップしたテストの理由を出力する
        pytest -r{char} でcharに指定したパラメータに応じたサマリーを出力する。char=sの場合はskip

2.6
    xfail
        @pytest.mark.xfail()で失敗することを期待されるテストを記述できる
        テスト結果が失敗の場合、テスト結果としてx(xfail)が記載される
        テスト結果が成功の場合、テスト結果としてX(XPASS)が記載される
        XPASSをFailedとしてカウントするように、pytest.iniを設定できる

2.7
    -v(--verbose)
        テスト実行対象のファイル名と実行結果を出力する
    テスト対象の指定
        pytest {dir_name} でディレクトリ以下のテストを全実行する
        pytest {file_name} で指定したファイル内のテストを全実行する
        pytest {file_name}::{test_name} で指定したファイル内の指定したテスト名のテストを実行する
        pytest {file_name}::{test_class_name}で指定したファイル内のテストクラス内のテストを全実行する
        pytest {file_name}::{test_class_name}::{test_name}で指定したファイル、テストクラス内のテストを個別に実行する
    テストクラス
        テストを昨日ごとにまとめたい時に、テストクラスを使うことでまとめられる。
    -k {target_string}
        target_stringに指定した文字列を含むテストのみを実行対象にする
        target_stringを'target1 and target2'のようにすることで、and,or,notを取れる。
