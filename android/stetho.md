# Stetho

感覺很厲害的調適工具 (http://facebook.github.io/stetho/)

* 在 App 裡面使用 Stetho Library
* 實際使用可以參考 Stetho Samples (https://github.com/facebook/stetho)

'''
    Stetho.initialize(Stetho.newInitializerBuilder(context)
        .enableDumpapp(new DumperPluginsProvider() {
          @Override
          public Iterable<DumperPlugin> get() {
            return new Stetho.DefaultDumperPluginsBuilder(context)
                .provide(new HelloWorldDumperPlugin())
                .provide(new APODDumperPlugin(context.getContentResolver()))
                .finish();
          }
        })
        .enableWebKitInspector(new ExtInspectorModulesProvider(context))
        .build());
'''

'''
  private static class ExtInspectorModulesProvider implements InspectorModulesProvider {

    private Context mContext;

    ExtInspectorModulesProvider(Context context) {
      mContext = context;
    }

    @Override
    public Iterable<ChromeDevtoolsDomain> get() {
      return new Stetho.DefaultInspectorModulesBuilder(mContext)
              .runtimeRepl(new JsRuntimeReplFactoryBuilder(mContext)
                      // Pass to JavaScript: var foo = "bar";
                      .addVariable("foo", "bar")
                      .build())
          .provideDatabaseDriver(createContentProviderDatabaseDriver(mContext))
          .finish();
    }

'''

* 開啟 Chrome 在網址列輸入 chrome://inspect/#devices
