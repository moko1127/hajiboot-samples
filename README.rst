「はじめてのSpring Boot」サポートページ
********************************************************************************

「\ `はじめてのSpring Boot <http://www.kohgakusha.co.jp/books/detail/978-4-7775-1865-4>`_\ 」のサポートページです。

このページでサンプルコードと正誤表を管理します。書籍の内容に関する間違いの指摘等はIssuesかPull Requestでお願いします。

また、疑問やコメントはTwitterでハッシュタグ「#hajiboot」をつけてツイートしていただければ極力お答えします。気軽にツイートしてください。


正誤表 (初版)
================================================================================

.. list-table::
   :header-rows: 1

   * - 場所
     - 誤
     - 正
     - 訂正日
   * - P.19 コマンドプロンプト内 (2箇所)
     - \ ``$ java -jar target\\hajiboot-1.0.0-SNAPSHOT.jar``\ 
     - \ ``$ java -jar target\hajiboot-1.0.0-SNAPSHOT.jar``\ 
     - 2014-11-20
   * - P.25 中央よりやや下
     - \ ``<version>1.2.0.RELEASE</version>``\ 
     - \ ``<version>1.2.1.RELEASE</version>``\ 
     - 2014-11-18
   * - P.30 プログラム解説 (2)
     - 「DI コンテナ」に管理させたい「Bean」を生成するメソッドに、「@Configuration」
     - 「DI コンテナ」に管理させたい「Bean」を生成するメソッドに、「@Bean」
     - 2014-11-26
   * - P.47 米印のコメント
     - 「autoFigure」の仕組みについては
     - 「autoconfigure」の仕組みについては
     - 2014-11-18
   * - P.54 「Log4JDBC」用の「DataSource」の定義
     - これまでは「Spring Boot」の「@EnableAutoConfiguration」の効果で、「DateSource」が
     - これまでは「Spring Boot」の「@EnableAutoConfiguration」の効果で、「Dat\ **a**\ Source」が
     - 2014-11-25
   * - P.54 \ ``realDataSource``\ を定義する箇所
     - \ ``@Bean``\ 
     - \ ``@Bean(destroyMethod = "close")``\ 
     - 2014-11-18
   * - P.58 項番(1)
     - (b) 「エラーが発生した場合」は 
     - (b) 「\ **実行時例外が**\ 発生した場合」は (*1)
     - 2014-11-18
   * - P.68 中央のAppクラスの説明
     - \ ``customerRepository.findAllOrderById()``\ 
     - \ ``customerRepository.findAllOrderByName()``\ 
     - 2014-11-18
   * - P.69 ノート
     - \ ``List<Customer> findAllOrderById()``\ 
     - \ ``List<Customer> findAllOrderByName()``\ 
     - 2014-11-18
   * - P.77 表の1行1列目
     - PI名 
     - API名 
     - 2014-11-26
   * - P.89 前半
     - しかし、本節では
     - 本節では
     - 2014-11-26
   * - P.89 三分どころ
     - 「プログラマ」と「デザイナ」間での「HTML」ややり取りにおける変換コスト
     - 「プログラマ」と「デザイナ」間での「HTML」のやり取りにおける変換コスト 
     - 2014-11-26
   * - P.89 表のタイトル
     - 【コマンド・プロンプト】追加されたライブラリの確認
     - 【コマンド・プロンプト】簡易顧客管理システムの処理一覧
     - 2014-11-26
   * - P.94,95 ファイルパス(3箇所)
     - src/main/resources/customers/list.html
     - src/main/resources/templates/customers/list.html
     - 2014-12-01
   * - P.94,95 ファイルパス(3箇所)
     - src/main/resources/customers/list.html
     - src/main/resources/templates/customers/list.html
     - 2014-12-10
   * - P.99 サンプルコードの上から5行目
     - name="firstName"
     - name="lastName"
     - 2014-11-26
   * - P.117 「このように～」の文章 
     - 「このように～」の文章がノートの外側
     - 「このように～」の文章がノートの内側
     - 2014-11-18
   * - P.118 中央
     - アプリケーション起動時に「Java API」を自動で行う
     - アプリケーション起動時に「Flyway」の「Java API」を自動で実行する
     - 2014-11-18
   * - P.121 下
     - 「3.5.1」 「application.yml」の変更
     - 「3.5.1」 「User」の「エンティティ」と「リポジトリ」作成
     - 2014-11-24
   * - P.131 loginForm.html (1)付近
     - Invalid username and password.
     - ユーザー名またはパスワードが正しくありません。
     - 2014-11-18
   * - P.133 ファイルパス(2箇所)
     - src/main/resources/V3_add_user.sql
     - src/main/resources/db/migration/V3__add_user.sql
     - 2014-12-01
   * - P.155 
     - 「Unitコード」
     - 「JUnitコード」
     - 2014-11-18
   * - P.163 附録Aの下の文章
     - 「Java SE 8u5」
     - 「Java SE 8u25」
     - 2014-11-18

\*1 ... チェック例外の場合はロールバックされません(\ **重要**\ )


FAQ
================================================================================

ThymeleafはXHTMLじゃないと使えないのか？
--------------------------------------------------------------------------------

NekoHTMLを使うことで、XHTMLではないHTML5(Legacy HTML5と呼ばれています)を扱えます。

pom.xmlに以下の依存関係を追加して、

.. code-block:: xml

   <dependency>
       <groupId>net.sourceforge.nekohtml</groupId>
       <artifactId>nekohtml</artifactId>
       <version>1.9.21</version>
   </dependency>

application.ymlに以下の設定を行ってください。

.. code-block:: yaml

   spring.thymeleaf.mode: LEGACYHTML5

org.h2.jdbc.JdbcSQLException: 機能はサポートされていません: "isWrapperFor"が出力される
--------------------------------------------------------------------------------------------

Spring Boot1.1ではH2(1.3.176) + Spring Data JPA (Hibernate) + Log4JDBCの組み合わせで以下のようなエラーログが出力されます。

.. code-block:: bash

  2014-12-09 13:55:49.711 ERROR 6512 --- [o-auto-1-exec-5] jdbc.sqltiming                           : 15. PreparedStatement.isWrapperFor(java.sql.CallableStatement)

  org.h2.jdbc.JdbcSQLException: 機能はサポートされていません: "isWrapperFor"
  Feature not supported: "isWrapperFor" [50100-176]
          at org.h2.message.DbException.getJdbcSQLException(DbException.java:344)
          at org.h2.message.DbException.get(DbException.java:178)
          at org.h2.message.DbException.get(DbException.java:154)
          at org.h2.message.DbException.getUnsupportedException(DbException.java:215)
          at org.h2.message.TraceObject.unsupported(TraceObject.java:395)
          at org.h2.jdbc.JdbcStatement.isWrapperFor(JdbcStatement.java:1076)
          at net.sf.log4jdbc.PreparedStatementSpy.isWrapperFor(PreparedStatementSpy.java:1142)
          at org.hibernate.engine.jdbc.internal.ResultSetReturnImpl.isTypeOf(ResultSetReturnImpl.java:99)
          at org.hibernate.engine.jdbc.internal.ResultSetReturnImpl.extract(ResultSetReturnImpl.java:70)
          at org.hibernate.loader.Loader.getResultSet(Loader.java:2065)
          at org.hibernate.loader.Loader.executeQueryStatement(Loader.java:1862)
          at org.hibernate.loader.Loader.executeQueryStatement(Loader.java:1838)
          at org.hibernate.loader.Loader.doQuery(Loader.java:909)
          at org.hibernate.loader.Loader.doQueryAndInitializeNonLazyCollections(Loader.java:354)
          at org.hibernate.loader.Loader.doList(Loader.java:2553)
          at org.hibernate.loader.Loader.doList(Loader.java:2539)
          at org.hibernate.loader.Loader.listIgnoreQueryCache(Loader.java:2369)
          at org.hibernate.loader.Loader.list(Loader.java:2364)
          at org.hibernate.loader.hql.QueryLoader.list(QueryLoader.java:496)
          at org.hibernate.hql.internal.ast.QueryTranslatorImpl.list(QueryTranslatorImpl.java:387)
          at org.hibernate.engine.query.spi.HQLQueryPlan.performList(HQLQueryPlan.java:231)
          at org.hibernate.internal.SessionImpl.list(SessionImpl.java:1264)
          at org.hibernate.internal.QueryImpl.list(QueryImpl.java:103)
          at org.hibernate.jpa.internal.QueryImpl.list(QueryImpl.java:573)
          at org.hibernate.jpa.internal.QueryImpl.getResultList(QueryImpl.java:449)
          at org.springframework.data.jpa.repository.query.JpaQueryExecution$PagedExecution.doExecute(JpaQueryExecution.java:153)
          at org.springframework.data.jpa.repository.query.JpaQueryExecution.execute(JpaQueryExecution.java:59)
          at org.springframework.data.jpa.repository.query.AbstractJpaQuery.doExecute(AbstractJpaQuery.java:97)
          at org.springframework.data.jpa.repository.query.AbstractJpaQuery.execute(AbstractJpaQuery.java:88)
          at org.springframework.data.repository.core.support.RepositoryFactorySupport$QueryExecutorMethodInterceptor.doInvoke(RepositoryFactorySupport.java:384)
          at org.springframework.data.repository.core.support.RepositoryFactorySupport$QueryExecutorMethodInterceptor.invoke(RepositoryFactorySupport.java:344)
          at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:179)
          at org.springframework.transaction.interceptor.TransactionInterceptor$1.proceedWithInvocation(TransactionInterceptor.java:98)
          (以下略)

以下のためです。

* HibernateがJDBC 4.0で追加された\ ``isWrapperFor``\ を呼んでいる
* H2(1.3.176)が\ ``isWrapperFor``\ を実装していない
* Log4JBDCがJDBCのエラーをログ出力する
* (Hibernateが\ ``isWrapperFor``\ がサポートされていないという例外を握りつぶす)

普段から起こっている事象ですが、Log4JBDCによって顕在化してしまっています。

無視しても問題ないのですが、精神衛生上よろしくないので修正したいという場合は、H2のバージョンをあげて\ ``isWrapperFor``\ がサポートされているものを使えばよいです。

H2のバージョンはspring-boot-starter-parentで管理されており、上書きするにはプロジェクトのpom.xmlにバージョンプロパティを指定すればよいです。

pom.xmlを以下のように修正してください。


.. code-block:: xml

    <properties>
        <java.version>1.8</java.version>
        <h2.version>1.4.182</h2.version><!-- ここ追加 -->
    </properties>

ちなみにSpring Boot 1.2では始めからH2 1.4.182が使われるようになっています。

なお、このバージョンのH2を使用すると、Windows上で\ ``jdbc:h2:file:/tmp/testdb``\ というURLの指定が出来ず、\ ``jdbc:h2:file:c:/tmp/testdb``\ というようにドライブレターを付ける必要があります。

この挙動が嫌な場合(\ ``jdbc:h2:file:/tmp/testdb``\ のまま使いたい場合)、実行時に\ ``-Dh2.implicitRelativePath=true``\ を付けてください。毎回このプロパティを指定するのが面倒な場合は、\ ``main``\ メソッドで以下のように実装してください

.. code-block:: java

  public static void main(String[] args) {
      if (System.getProperty("h2.implicitRelativePath") == null) {
          // keep compatibility with H2 1.3
          // prevent http://www.h2database.com/javadoc/org/h2/api/ErrorCode.html#c90011
          System.setProperty("h2.implicitRelativePath", "true");
      }
      SpringApplication.run(App.class, args);
  }


org.postgresql.util.PSQLException: 方法 org.postgresql.jdbc4.Jdbc4Connection.createClob() はまだ装備されていません。が出力される
-----------------------------------------------------------------------------------------------------------------------------------

H2同様にPostgreSQL + Hibernateでも同様のエラーログが出力されます。

.. code-block:: bash

    2014-12-09 20:41:13.753  INFO 5484 --- [           main] org.hibernate.dialect.Dialect            : HHH000400: Using dialect: org.hibernate.dialect.PostgreSQLDialect
    2014-12-09 20:41:13.783 ERROR 5484 --- [           main] jdbc.sqltiming                           : 1. Connection.createClob()

    org.postgresql.util.PSQLException: 方法 org.postgresql.jdbc4.Jdbc4Connection.createClob() はまだ装備されていません。
            at org.postgresql.Driver.notImplemented(Driver.java:753)
            at org.postgresql.jdbc4.AbstractJdbc4Connection.createClob(AbstractJdbc4Connection.java:41)
            at org.postgresql.jdbc4.Jdbc4Connection.createClob(Jdbc4Connection.java:21)
            at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
            at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
            at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
            at java.lang.reflect.Method.invoke(Method.java:483)
            at org.springsource.loaded.ri.ReflectiveInterceptor.jlrMethodInvoke(ReflectiveInterceptor.java:1270)
            at org.apache.tomcat.jdbc.pool.ProxyConnection.invoke(ProxyConnection.java:126)
            at org.apache.tomcat.jdbc.pool.JdbcInterceptor.invoke(JdbcInterceptor.java:109)
            at org.apache.tomcat.jdbc.pool.DisposableConnectionFacade.invoke(DisposableConnectionFacade.java:80)
            at com.sun.proxy.$Proxy52.createClob(Unknown Source)
            at net.sf.log4jdbc.ConnectionSpy.createClob(ConnectionSpy.java:496)
            at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
            at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
            at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
            at java.lang.reflect.Method.invoke(Method.java:483)
            at org.springsource.loaded.ri.ReflectiveInterceptor.jlrMethodInvoke(ReflectiveInterceptor.java:1270)
            at org.hibernate.engine.jdbc.internal.LobCreatorBuilder.useContextualLobCreation(LobCreatorBuilder.java:112)
            at org.hibernate.engine.jdbc.internal.LobCreatorBuilder.<init>(LobCreatorBuilder.java:63)
            at org.hibernate.engine.jdbc.internal.JdbcServicesImpl.configure(JdbcServicesImpl.java:192)
            (略)
            
    2014-12-09 20:41:13.791  INFO 5484 --- [           main] o.h.e.jdbc.internal.LobCreatorBuilder    : HHH000424: Disabling contextual LOB creation as createClob() method threw error : java.lang.reflect.InvocationTargetException

これも実際は問題ないのですが、Log4JDBCによってエラーが見えてしまっています。

最新の9.3-1102-jdbc41で試してもまだ実装されていませんでした。

.. code-block:: xml

    <dependency>
        <groupId>org.postgresql</groupId>
        <artifactId>postgresql</artifactId>
        <version>9.3-1102-jdbc41</version>
    </dependency>

.. code-block:: bash

    2014-12-09 20:48:53.675 ERROR 7484 --- [           main] jdbc.sqltiming                           : 1. Connection.createClob()

    java.sql.SQLFeatureNotSupportedException: org.postgresql.jdbc4.Jdbc4Connection.createClob() メソッドはまだ実装されていません。
            at org.postgresql.Driver.notImplemented(Driver.java:729)
            at org.postgresql.jdbc4.AbstractJdbc4Connection.createClob(AbstractJdbc4Connection.java:51)
            at org.postgresql.jdbc4.Jdbc4Connection.createClob(Jdbc4Connection.java:21)
            at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)


ただ、書籍で扱っているPostgreSQL JDBCドライバのバージョンは9.0-801.jdbc4と古く、
https://devcenter.heroku.com/articles/heroku-postgresql#version-support-and-legacy-infrastructure\ の通り、今はHeroku側もデフォルトでPostgreSQLのバージョンが9.3なので、上げた方が良いですね。
