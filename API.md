# hapijs 中文文档【v17.5.x API Reference】

<!-- toc -->

- [Server](#server)
  - [`server([options])`](#server())
  - [Server options](#server.options)
    - [`server.options.address`](#server.options.address)
    - [`server.options.app`](#server.options.app)
    - [`server.options.autoListen`](#server.options.autolisten)
    - [`server.options.cache`](#server.options.cache)
    - [`server.options.compression`](#server.options.compression)
      - [`server.options.compression.minBytes`](#server.options.compression.minBytes)
    - [`server.options.debug`](#server.options.debug)
    - [`server.options.host`](#server.options.host)
    - [`server.options.listener`](#server.options.listener)
    - [`server.options.load`](#server.options.load)
    - [`server.options.mime`](#server.options.mime)
    - [`server.options.plugins`](#server.options.plugins)
    - [`server.options.port`](#server.options.port)
    - [`server.options.router`](#server.options.router)
    - [`server.options.routes`](#server.options.routes)
    - [`server.options.state`](#server.options.state)
    - [`server.options.tls`](#server.options.tls)
    - [`server.options.uri`](#server.options.uri)
  - [Server properties](#server-properties)
    - [`server.app`](#server.app)
    - [`server.auth.api`](#server.auth.api)
    - [`server.auth.settings.default`](#server.auth.settings.default)
    - [`server.decorations`](#server.decorations)
    - [`server.events`](#server.events)
      - [`'log'` Event](#server.events.log)
      - [`'request'` Event](#server.events.request)
      - [`'response'` Event](#server.events.response)
      - [`'route'` Event](#server.events.route)
      - [`'start'` Event](#server.events.start)
      - [`'stop'` Event](#server.events.stop)
    - [`server.info`](#server.info)
    - [`server.listener`](#server.listener)
    - [`server.load`](#server.load)
    - [`server.methods`](#server.methods)
    - [`server.mime`](#server.mime)
    - [`server.plugins`](#server.plugins)
    - [`server.realm`](#server.realm)
    - [`server.registrations`](#server.registrations)
    - [`server.settings`](#server.settings)
    - [`server.states`](#server.states)
    - [`server.states.settings`](#server.states.settings)
    - [`server.states.cookies`](#server.states.cookies)
    - [`server.states.names`](#server.states.names)
    - [`server.type`](#server.type)
    - [`server.version`](#server.version)
  - [`server.auth.default(options)`](#server.auth.default())
  - [`server.auth.scheme(name, scheme)`](#server.auth.scheme())
    - [Authentication scheme](#authentication-scheme)
  - [`server.auth.strategy(name, scheme, [options])`](#server.auth.strategy())
  - [`await server.auth.test(strategy, request)`](#server.auth.test())
  - [`server.bind(context)`](#server.bind())
  - [`server.cache(options)`](#server.cache())
  - [`await server.cache.provision(options)`](#server.cache.provision())
  - [`server.control(server)`](#server.control())
  - [`server.decoder(encoding, decoder)`](#server.decoder())
  - [`server.decorate(type, property, method, [options])`](#server.decorate())
  - [`server.dependency(dependencies, [after])`](#server.dependency())
  - [`server.encoder(encoding, encoder)`](#server.encoder())
  - [`server.event(events)`](#server.event())
  - [`await server.events.emit(criteria, data)`](#server.events.emit())
  - [`server.events.on(criteria, listener)`](#server.events.on())
  - [`server.events.once(criteria, listener)`](#server.events.once())
  - [`await server.events.once(criteria)`](#server.events.once.await())
  - [`server.expose(key, value)`](#server.expose())
  - [`server.expose(obj)`](#server.expose.obj())
  - [`server.ext(events)`](#server.ext())
  - [`server.ext(event, method, [options])`](#server.ext.args())
  - [`await server.initialize()`](#server.initialize())
  - [`await server.inject(options)`](#server.inject())
  - [`server.log(tags, [data, [timestamp]])`](#server.log())
  - [`server.lookup(id)`](#server.lookup())
  - [`server.match(method, path, [host])`](#server.match())
  - [`server.method(name, method, [options])`](#server.method())
  - [`server.method(methods)`](#server.method.array())
  - [`server.path(relativeTo)`](#server.path())
  - [`await server.register(plugins, [options])`](#server.register())
  - [`server.route(route)`](#server.route())
    - [Path parameters](#path-parameters)
    - [Path matching order](#path-matching-order)
    - [Catch all route](#catch-all-route)
  - [`server.rules(processor, [options])`](#server.rules())
  - [`await server.start()`](#server.start())
  - [`server.state(name, [options])`](#server.state())
  - [`server.states.add(name, [options])`](#server.states.add())
  - [`await server.states.format(cookies)`](#server.states.format())
  - [`await server.states.parse(header)`](#server.states.parse())
  - [`await server.stop([options])`](#server.stop())
  - [`server.table([host])`](#server.table())
- [Route options](#route-options)
  - [`route.options.app`](#route.options.app)
  - [`route.options.auth`](#route.options.auth)
    - [`route.options.auth.access`](#route.options.auth.access)
    - [`route.options.auth.access.scope`](#route.options.auth.access.scope)
    - [`route.options.auth.access.entity`](#route.options.auth.access.entity)
    - [`route.options.auth.mode`](#route.options.auth.mode)
    - [`route.options.auth.payload`](#route.options.auth.payload)
    - [`route.options.auth.strategies`](#route.options.auth.strategies)
    - [`route.options.auth.strategy`](#route.options.auth.strategy)
  - [`route.options.bind`](#route.options.bind)
  - [`route.options.cache`](#route.options.cache)
  - [`route.options.compression`](#route.options.compression)
  - [`route.options.cors`](#route.options.cors)
  - [`route.options.description`](#route.options.description)
  - [`route.options.ext`](#route.options.ext)
  - [`route.options.files`](#route.options.files)
  - [`route.options.handler`](#route.options.handler)
  - [`route.options.id`](#route.options.id)
  - [`route.options.isInternal`](#route.options.isInternal)
  - [`route.options.json`](#route.options.json)
  - [`route.options.jsonp`](#route.options.jsonp)
  - [`route.options.log`](#route.options.log)
  - [`route.options.notes`](#route.options.notes)
  - [`route.options.payload`](#route.options.payload)
    - [`route.options.payload.allow`](#route.options.payload.allow)
    - [`route.options.payload.compression`](#route.options.payload.compression)
    - [`route.options.payload.defaultContentType`](#route.options.payload.defaultContentType)
    - [`route.options.payload.failAction`](#route.options.payload.failAction)
    - [`route.options.payload.maxBytes`](#route.options.payload.maxBytes)
    - [`route.options.payload.multipart`](#route.options.payload.multipart)
    - [`route.options.payload.output`](#route.options.payload.output)
    - [`route.options.payload.override`](#route.options.payload.override)
    - [`route.options.payload.parse`](#route.options.payload.parse)
    - [`route.options.payload.timeout`](#route.options.payload.timeout)
    - [`route.options.payload.uploads`](#route.options.payload.uploads)
  - [`route.options.plugins`](#route.options.plugins)
  - [`route.options.pre`](#route.options.pre)
  - [`route.options.response`](#route.options.response)
    - [`route.options.response.emptyStatusCode`](#route.options.response.emptyStatusCode)
    - [`route.options.response.failAction`](#route.options.response.failAction)
    - [`route.options.response.modify`](#route.options.response.modify)
    - [`route.options.response.options`](#route.options.response.options)
    - [`route.options.response.ranges`](#route.options.response.ranges)
    - [`route.options.response.sample`](#route.options.response.sample)
    - [`route.options.response.schema`](#route.options.response.schema)
    - [`route.options.response.status`](#route.options.response.status)
  - [`route.options.rules`](#route.options.rules)
  - [`route.options.security`](#route.options.security)
  - [`route.options.state`](#route.options.state)
  - [`route.options.tags`](#route.options.tags)
  - [`route.options.timeout`](#route.options.timeout)
    - [`route.options.timeout.server`](#route.options.timeout.server)
    - [`route.options.timeout.socket`](#route.options.timeout.socket)
  - [`route.options.validate`](#route.options.validate)
    - [`route.options.validate.errorFields`](#route.options.validate.errorFields)
    - [`route.options.validate.failAction`](#route.options.validate.failAction)
    - [`route.options.validate.headers`](#route.options.validate.headers)
    - [`route.options.validate.options`](#route.options.validate.options)
    - [`route.options.validate.params`](#route.options.validate.params)
    - [`route.options.validate.payload`](#route.options.validate.payload)
    - [`route.options.validate.query`](#route.options.validate.query)
- [Request lifecycle](#request-lifecycle)
  - [Lifecycle methods](#lifecycle-methods)
    - [Lifecycle workflow](#lifecycle-workflow)
    - [Takeover response](#takeover-response)
    - [`failAction` configuration](#lifecycle-failAction)
    - [Errors](#errors)
      - [Error transformation](#error-transformation)
  - [Response Toolkit](#response-toolkit)
    - [Toolkit properties](#toolkit-properties)
      - [`h.abandon`](#h.abandon)
      - [`h.close`](#h.close)
      - [`h.context`](#h.context)
      - [`h.continue`](#h.continue)
      - [`h.realm`](#h.realm)
      - [`h.request`](#h.request)
    - [`h.authenticated(data)`](#h.authenticated())
    - [`h.entity(options)`](#h.entity())
    - [`h.redirect(uri)`](#h.redirect())
    - [`h.response([value])`](#h.response())
    - [`h.state(name, value, [options])`](#h.state())
    - [`h.unauthenticated(error, [data])`](#h.unauthenticated())
    - [`h.unstate(name, [options])`](#h.unstate())
  - [Response object](#response-object)
    - [Response properties](#response-properties)
      - [`response.app`](#response.app)
      - [`response.events`](#response.events)
      - [`response.headers`](#response.headers)
      - [`response.plugins`](#response.plugins)
      - [`response.settings`](#response.settings)
        - [`response.settings.passThrough`](#response.settings.passThrough)
        - [`response.settings.stringify`](#response.settings.stringify)
        - [`response.settings.ttl`](#response.settings.ttl)
        - [`response.settings.varyEtag`](#response.settings.varyEtag)
      - [`response.source`](#response.source)
      - [`response.statusCode`](#response.statusCode)
      - [`response.variety`](#response.variety)
    - [`response.bytes(length)`](#response.bytes())
    - [`response.charset(charset)`](#response.charset())
    - [`response.code(statusCode)`](#response.code())
    - [`response.message(httpMessage)`](#response.message())
    - [`response.created(uri)`](#response.created())
    - [`response.encoding(encoding)`](#response.encoding())
    - [`response.etag(tag, options)`](#response.etag())
    - [`response.header(name, value, options)`](#response.header())
    - [`response.location(uri)`](#response.location())
    - [`response.redirect(uri)`](#response.redirect())
    - [`response.replacer(method)`](#response.replacer())
    - [`response.spaces(count)`](#response.spaces())
    - [`response.state(name, value, [options])`](#response.state())
    - [`response.suffix(suffix)`](#response.suffix())
    - [`response.ttl(msec)`](#response.ttl())
    - [`response.type(mimeType)`](#response.type())
    - [`response.unstate(name, [options])`](#response.unstate())
    - [`response.vary(header)`](#response.vary())
    - [`response.takeover()`](#response.takeover())
    - [`response.temporary(isTemporary)`](#response.temporary())
    - [`response.permanent(isPermanent)`](#response.permanent())
    - [`response.rewritable(isRewritable)`](#response.rewritable())
- [Request](#request)
  - [Request properties](#request-properties)
    - [`request.app`](#request.app)
    - [`request.auth`](#request.auth)
    - [`request.events`](#request.events)
    - [`request.headers`](#request.headers)
    - [`request.info`](#request.info)
    - [`request.logs`](#request.logs)
    - [`request.method`](#request.method)
    - [`request.mime`](#request.mime)
    - [`request.orig`](#request.orig)
    - [`request.params`](#request.params)
    - [`request.paramsArray`](#request.paramsArray)
    - [`request.path`](#request.path)
    - [`request.payload`](#request.payload)
    - [`request.plugins`](#request.plugins)
    - [`request.pre`](#request.pre)
    - [`request.response`](#request.response)
    - [`request.preResponses`](#request.preResponses)
    - [`request.query`](#request.query)
    - [`request.raw`](#request.raw)
    - [`request.route`](#request.route)
    - [`request.server`](#request.server)
    - [`request.state`](#request.state)
    - [`request.url`](#request.url)
  - [`request.generateResponse(source, [options])`](#request.generateResponse())
  - [`request.log(tags, [data])`](#request.log())
  - [`request.route.auth.access(request)`](#request.route.auth.access())
  - [`request.setMethod(method)`](#request.setMethod())
  - [`request.setUrl(url, [stripTrailingSlash]`](#request.setUrl())
- [Plugins](#plugins)

<!-- tocstop -->

## 服务器 (Server)

服务器对象是主应用程序的容器。服务器管理所有传入的请求以及框架提供的所有设备【facilities】。每个服务器支持一个单独的连接（例如 监听到 80 端口）。

### <a name="server()" /> `server([options])`

创建一个新的 server 对象：

Creates a new server object where:
- `options` - (可选) 一个 [server 可配置对象](#server.options).

```js
const Hapi = require('hapi');

const server = Hapi.server({ load: { sampleInterval: 1000 } });
```

### <a name="server.options" /> Server options

options 控制服务器对象的行为。注意 options 对象是深拷贝的（除了 [`listener`](#server.options.listener) 属性是浅拷贝）并且不能包含任何不安全的值来执行【perform】深拷贝

所有的选项都是可选的。

#### <a name="server.options.address" /> `server.options.address`

默认值：`'0.0.0.0'` （所有可用的网络接口）

设置服务器所要监听的主机名或者 IP 地址。如果没有配置，默认会为已提供的 [`host`](#server.options.host) 选项，否则为所有可用的网络接口。设置 `'127.0.0.1'` 或 `'localhost'` 限制服务器仅来自同一主机。

#### <a name="server.options.app" /> `server.options.app`

默认值: `{}`.

提供特定于【specific】应用程序的配置，以后可以通过【via】它进行访问 [`server.settings.app`](#server.settings)。框架不与此对象交互【interact】。它只是提供一个随处可用的 `server` 的引用。

注意与 `server.settings.app` 的区别，它用于存储静态的配置值。[`server.app`](#server.app) 用于存储运行时的状态。

#### <a name="server.options.autolisten" /> `server.options.autoListen`

默认值: `true`.

用于禁用 [`listener`](#server.options.listener) 的自动初始化。值为 `false` 时，表示【indicates】框架外将手动开启 [`listener`](#server.options.listener)

不能与 [`port`](#server.options.port) 一起设置为 `false`

#### <a name="server.options.cache" /> `server.options.cache`

默认值: `{ engine: require('catbox-memory') }`.

设置服务端缓存的提供者程序。每个服务器包含一个默认用于存储应用程序状态的缓存。默认情况下，会创建一个容量【capacity】和功能【capability】有限，基于内存的缓存，

**hapi** 使用 [**catbox**](https://github.com/hapijs/catbox) 为其缓存实现【implementation】，包括对常见存储解决方案的支持（例如 Redis, MongoDB, Memcached, Riak 等等）。仅当 [methods](#server.methods) 和 [plugins](#plugins) 明确存储状态在缓存中时才使用缓存。

服务器缓存配置仅定义存储容器本身。配置可以指定一个或多个（数组）：

- 一个类或者原型方法（通常通过在 **catbox** 策略上调用 `require()` 来获得，例如 `require('catbox-redis')`）。一个新的  **catbox** [client](https://github.com/hapijs/catbox#client) 将使用此函数在内部【internally】创建。

- 配置对象具有以下内容：

    - `engine` - 一个类, 原型方法, 或 **catbox** 对象.
    
    - `name` - 稍后为 [server methods](#server.methods) 或 [plugins](#plugins) 提供或配置缓存时使用的标识符。每个缓存名称必须是惟一的。单一项可以省略定义默认缓存的 `name` 选项。如果每个缓存都包含 `name`，还会配置默认的内存缓存。

    - `shared` - 如果为 `true`, 允许多个缓存用户共享同一个片段【segment】 (例如多个方法使用相同的缓存存储容器). 默认为 `false`.

    - `partition` - (可选) 字符串用于隔离缓存的数据. 默认为 `'hapi-cache'`.

    - other options passed to the **catbox** strategy used. Other options are only passed to
      **catbox** when `engine` above is a class or function and ignored if `engine` is a **catbox**
      engine object).

#### <a name="server.options.compression" /> `server.options.compression`

默认值: `{ minBytes: 1024 }`.

定义服务端控制的内容编码请求。如果 `false`，相应内容编码被禁用，并且服务器不执行【perform】压缩

##### <a name="server.options.compression.minBytes" /> `server.options.compression.minBytes`

默认值: '1024'.

设置最小响应有效负荷大小（以字节为单位），它是内容编码压缩所必须的。
如果有效负载大小低于限制，则不执行压缩。

#### <a name="server.options.debug" /> `server.options.debug`

默认值: `{ request: ['implementation'] }`.

确定【Determines】将哪些日志事件发送到控制台。仅用于开发模式并且不影响【affect】记录实际内部和收录的事件。设置 `false` 去关闭所有输出日志，或者传入一个对象：

- `log` - a string array of server log tags to be displayed via `console.error()` when
    the events are logged via [`server.log()`](#server.log()) as well as
    internally generated [server logs](#server-logs). Defaults to no output.

- `request` - a string array of request log tags to be displayed via `console.error()` when
    the events are logged via [`request.log()`](#request.log()) as well as
    internally generated [request logs](#request-logs). For example, to display all errors,
    set the option to `['error']`. To turn off all console debug messages set it to `false`.
    To display all request logs, set it to `'*'`.
    Defaults to uncaught errors thrown in external code (these errors are handled
    automatically and result in an Internal Server Error response) or runtime errors due to
    developer error.

举个例子, 为了展示所有错误, 设置 `log` or `request` 为 `['error']`. 关闭所有输出，设置 `log` or `request` 为 `false`. 展示所有服务器日志, 设置 `log` or
`request` 为 `'*'`. 关闭所有服务器日志, 设置 `debug` 为 `false`.

#### <a name="server.options.host" /> `server.options.host`

默认值: 操作系统的主机名，如果不可用默认为 `'localhost'`。

公共主机名或 IP 。 用于设置 [`server.info.host`](#server.info) ，
[`server.info.uri`](#server.info) 和 [`address`](#server.options.address) 没有指定.

#### <a name="server.options.listener" /> `server.options.listener`

默认值: none.

可选的 node HTTP (或 HTTPS) [`http.Server`](https://nodejs.org/api/http.html#http_class_http_server)
对象 (或具有兼容【compatible】接口的对象).

如果 `listener` 需要手动启动，设置 [`autoListen`](#server.options.autolisten) 为 `false`。

如果 `listener` 使用 TLS， 设置 [`tls`](#server.options.tls) 为 `true`。

#### <a name="server.options.load" /> `server.options.load`

默认值: `{ sampleInterval: 0, concurrent: 0 }`.

服务器过载【excessive】处理的限制，其中：

- `sampleInterval` - the frequency of sampling in milliseconds. When set to `0`, the other load
  options are ignored. Defaults to `0` (no sampling).

- `maxHeapUsedBytes` - maximum V8 heap size over which incoming requests are rejected with an HTTP
  Server Timeout (503) response. Defaults to `0` (no limit).

- `maxRssBytes` - maximum process RSS size over which incoming requests are rejected with an HTTP
  Server Timeout (503) response. Defaults to `0` (no limit).

- `maxEventLoopDelay` - maximum event loop delay duration in milliseconds over which incoming
  requests are rejected with an HTTP Server Timeout (503) response. Defaults to `0` (no limit).

- `concurrent` - maximum number of requests to execute in parallel. This is useful to reduce
  garbage collection costs on high load deployment where the actual handler computation load is
  low. For example, a handler that mostly waits for upstream data will allow many incoming requests
  to queue up all the way to the handler lifecycle step. This will trigger heavy garbage collection
  load trying to sort out the many pending objects. Reducing the number of concurrent requests
  being processed can help. There is no recommended value - you need to test what works best for
  your specific deployment. Defaults to `0` (no queue).

#### <a name="server.options.mime" /> `server.options.mime`

默认值: none.

生成服务器使用的 mime 数据库时传递给 [**mimos**](https://github.com/hapijs/mimos) 模块的选项 (并通过 [`server.mime`](#server.mime) 访问)：

- 一个对象哈希，被合并到指定 [here](https://github.com/jshttp/mime-db) 的内置 mime 信息中

- `override` - 一个对象哈希，被合并到指定 [here](https://github.com/jshttp/mime-db) 的内置 mime 信息中。 每个键值对代表一个单独的 mime 对象。
  每个覆盖值必须包含:

    - `key` - 小写的 mime-type 字符串 (例如 `'application/javascript'`).

    - `value` - 符合规范【specifications】的对象 [here](https://github.com/jshttp/mime-db#data-structure)。
      其他值包含:

        - `type` - 指定 `type` 的结果， 默认为 `key`。

        - `predicate` - 带签名的方法 `function(mime)` 当 mime 的类型在数据库中, 此函数执行以允许自定义

```js
const options = {
    mime: {
        override: {
            'node/module': {
                source: 'iana',
                compressible: true,
                extensions: ['node', 'module', 'npm'],
                type: 'node/module'
            },
            'application/javascript': {
                source: 'iana',
                charset: 'UTF-8',
                compressible: true,
                extensions: ['js', 'javascript'],
                type: 'text/javascript'
            },
            'text/html': {
                predicate: function(mime) {
                    if (someCondition) {
                        mime.foo = 'test';
                    }
                    else {
                        mime.foo = 'bar';
                    }
                    return mime;
                }
            }
        }
    }
};
```

#### <a name="server.options.plugins" /> `server.options.plugins`

默认值: `{}`.

特定于插件的配置，以后可以通过 [`server.settings.plugins`](#server.settings) 访问。`plugins` 是一个对象，其中每个键是插件名称，值是配置。注意它与 [`server.settings.plugins`](#server.settings) 和 [`server.plugins`](#server.plugins) 的不同，前者用于存储静态配置值，后者用于存储运行时的状态。

#### <a name="server.options.port" /> `server.options.port`

默认值: `0` (一个无常【ephemeral】的端口).

服务器要监听的 TCP 端口. 默认为服务器启动后的下一个可用端口。(并分配给 [`server.info.port`](#server.info)).

如果 `port` 是一个包含 '/' 的字符串，它用作 UNIX 域的 socket 路径。
如果以 '\\.\pipe' 开头，它用作 Windows 命名管道。

#### <a name="server.options.router" /> `server.options.router`

默认值: `{ isCaseSensitive: true, stripTrailingSlash: false }`.

控制传入请求URI与路由表的匹配方式：

- `isCaseSensitive` - 确定【determines】路径 '/example' 和 '/EXAMPLE' 是否被视为不同的资源。默认为 `true`.

- `stripTrailingSlash` - 删除传入路径上的尾部斜杠。默认为 `false`.

#### <a name="server.options.routes" /> `server.options.routes`

默认值: none.

一个 [route options](#route-options) 对象用于每个路由的默认配置。

#### <a name="server.options.state" /> `server.options.state`

默认值:
```js
{
    strictHeader: true,
    ignoreErrors: false,
    isSecure: true,
    isHttpOnly: true,
    isSameSite: 'Strict',
    encoding: 'none'
}
```

为每个状态（cookie）显式【explicitly】设置默认配置通过 `server.state()`](#server.state()) 或者 隐式(没有定义)使用 [state configuration](#server.state()) 对象

#### <a name="server.options.tls" /> `server.options.tls`

默认值: none.

用于创建 HTTPS 连接. `tls` 对象不变传递到 node HTTPS 服务器，如下所示 [node HTTPS documentation](https://nodejs.org/api/https.html#https_https_createserver_options_requestlistener)。

当传入一个已配置 [`listener`](#server.options.listener) 对象为 `true` 时，直接使用 TLS

#### <a name="server.options.uri" /> `server.options.uri`

默认值: 由运行时的服务器信息构建

没有路径的完整公共 URI (例如 'http://example.com:8080'). 如果存在, 用作服务器的 [`server.info.uri`](#server.info), 否则由服务器设置构造.

### 服务器属性 (Server properties)

#### <a name="server.app" /> `server.app`

访问: 读 / 写.

提供了一个安全的地方来存储特定于服务器的运行时应用程序数据，而不与框架内部潜在【potential】冲突。数据可以在任何服务器可用状态下被访问。初始化为空对象。

```js
const server = Hapi.server();

server.app.key = 'value';

const handler = function (request, h) {

    return request.server.app.key;        // 'value'
};
```

#### <a name="server.auth.api" /> `server.auth.api`

访问: 指定的认证策略【strategy】。

一个对象，其中每个键都是一个身份验证策略名称，值是公开【exposed】的策略 API。仅当身份验证方案【scheme】通过实现函数返回对象中的 `api` 键来公开 API 时才可用。

```js
const server = Hapi.server({ port: 80 });

const scheme = function (server, options) {

    return {
        api: {
            settings: {
                x: 5
            }
        },
        authenticate: function (request, h) {

            const authorization = request.headers.authorization;
            if (!authorization) {
                throw Boom.unauthorized(null, 'Custom');
            }

            return h.authenticated({ credentials: { user: 'john' } });
        }
    };
};

server.auth.scheme('custom', scheme);
server.auth.strategy('default', 'custom');

console.log(server.auth.api.default.settings.x);    // 5
```

#### <a name="server.auth.settings.default" /> `server.auth.settings.default`

访问: 只读。

包含默认的身份认证配置，如果是默认的策略设置请通过 [`server.auth.default()`](#server.auth.default())

#### <a name="server.decorations" /> `server.decorations`

访问: 只读。

提供对已应用于各种框架接口修饰符的访问。对象不能直接被修改，但只能通过 [`server.decorate`](#server.decorate())。

包含：

- `request` - 装饰 [request object](#request).
- `toolkit` - 装饰 [response toolkit](#response-toolkit).
- `server` -装饰 [server](#server) 对象.

```js
const Hapi = require('hapi');
const server = Hapi.server({ port: 80 });

const success = function () {

    return this.response({ status: 'ok' });
};

server.decorate('toolkit', 'success', success);
console.log(server.decorations.toolkit);            // ['success']
```

#### <a name="server.events" /> `server.events`

访问: **podium** 公共接口.

服务器的事件触发器. 利用【Utilizes】 [**podium**](https://github.com/hapijs/podium) 支持的事件标准验证, 频道和过滤器。

使用下面方法与 `server.events` 进行交互：

- [`server.event(events)`](#server.event()) - 注册应用事件.
- [`server.events.emit(criteria, data)`](#server.events.emit()) - 触发服务器事件.
- [`server.events.on(criteria, listener)`](#server.events.on()) - 订阅服务器事件.
- [`server.events.once(criteria, listener)`](#server.events.once()) - 订阅

其他方法包含: `server.events.removeListener(name, listener)`,
`server.events.removeAllListeners(name)`, 和 `server.events.hasListeners(name)`。

##### <a name="server.events.log" /> `'log'` Event

`'log'` 事件类型触发由框架生成的内部服务器事件，以及使用 [`server.log()`](#server.log()) 记录的应用程序事件

`'log'` 事件处理程序使用函数签名 `function(event, tags)`，其中：

- `event` - 具有以下属性的对象：
    - `timestamp` - 事件时间戳.
    - `tags` - 标识事件的标签数组 (例如 `['error', 'http']`).
    - `channel` - 为内部生成的事件设置为 `'internal'`， 否则由 [`server.log()`](#server.log()) 生成 `'app'`。
    - `data` - 特定事件的信息。 当指定事件数据并且不是错误时可用。错误通过 `error` 传递。
    - `error` - 与事件相关的错误对象（如果适用）。不能与 `data` 同时出现。

- `tags` - 一个对象，其中每个 `event.tag` 是一个键，值为 `true`。有助于快速识别【identification】事件

```js
server.events.on('log', (event, tags) => {

    if (tags.error) {
        console.log(`Server error: ${event.error ? event.error.message : 'unknown'}`);
    }
});
```

内部生成的事件是 (由它们 `tags` 识别):

- `load` - 由于 [high load](#server.options.load) 服务器拒绝请求时记录当前服务器负载测量值。事件数据包含流程负载指标【metrics】。

- `connection` `client` `error` -  从 HTTP 或 HTTPS 监听器收到的 `clientError` 事件。事件数据是收到的错误对象。

##### <a name="server.events.request" /> `'request'` Event

 `'request'` 事件类型触发由框架生成的内部请求事件以及使用[`request.log()`](#request.log())记录的应用程序事件。

`'request'` 事件处理程序使用函数签名 `function(request, event, tags)` 其中：

- `request` - the [request object](#request).

- `event` - an object with the following properties:
    - `timestamp` - the event timestamp.
    - `tags` - an array of tags identifying the event (e.g. `['error', 'http']`).
    - `channel` - one of
        - `'app'` - events generated by [`server.log()`](#server.log()).
        - `'error'` - emitted once per request if the response had a `500` status code.
        - `'internal'` - internally generated events.
    - `request` - the request [identifier](#request.info.id).
    - `data` - event-specific information. Available when event data was provided and is not an
      error. Errors are passed via `error`.
    - `error` - the error object related to the event if applicable. Cannot appear together with
      `data`.

- `tags` - an object where each `event.tag` is a key and the value is `true`. Useful for quick
  identification of events.

```js
server.events.on('request', (request, event, tags) => {

    if (tags.error) {
        console.log(`Request ${event.request} error: ${event.error ? event.error.message : 'unknown'}`);
    }
});
```

仅监听一个频道, 使用事件的条件对象：

```js
server.events.on({ name: 'request', channels: 'error' }, (request, event, tags) => {

    console.log(`Request ${event.request} failed`);
});
```

内部生成的事件 (由 `tags` 标识):

- `accept-encoding` `error` - a request received contains an invalid Accept-Encoding header.
- `auth` `unauthenticated` - no authentication scheme included with the request.
- `auth` `unauthenticated` `response` `{strategy}` - the authentication strategy listed returned a
  non-error response (e.g. a redirect to a login page).
- `auth` `unauthenticated` `error` `{strategy}` - the request failed to pass the listed
  authentication strategy (invalid credentials).
- `auth` `unauthenticated` `missing` `{strategy}` - the request failed to pass the listed
  authentication strategy (no credentials found).
- `auth` `unauthenticated` `try` `{strategy}` - the request failed to pass the listed
  authentication strategy in `'try'` mode and will continue.
- `auth` `scope` `error` - the request authenticated but failed to meet the scope requirements.
- `auth` `entity` `user` `error` - the request authenticated but included an application entity
  when a user entity was required.
- `auth` `entity` `app` `error` - the request authenticated but included a user entity when an
  application entity was required.
- `handler` `error` - the route handler returned an error. Includes the execution duration and the
  error message.
- `pre` `error` - a pre method was executed and returned an error. Includes the execution duration,
  assignment key, and error.
- `internal` `error` - an HTTP 500 error response was assigned to the request.
- `internal` `implementation` `error` - an incorrectly implemented [lifecycle method](#lifecycle-methods).
- `request` `abort` `error` - the request aborted.
- `request` `closed` `error` - the request closed prematurely.
- `request` `error` - the request stream emitted an error. Includes the error.
- `request` `server` `timeout` `error` - the request took too long to process by the server.
  Includes the timeout configuration value and the duration.
- `state` `error` - the request included an invalid cookie or cookies. Includes the cookies and
  error details.
- `state` `response` `error` - the response included an invalid cookie which prevented generating a
  valid header. Includes the error.
- `payload` `error` - failed processing the request payload. Includes the error.
- `response` `error` - failed writing the response to the client. Includes the error.
- `response` `error` `close` - failed writing the response to the client due to prematurely closed
  connection.
- `response` `error` `aborted` - failed writing the response to the client due to prematurely
  aborted connection.
- `response` `error` `cleanup` - failed freeing response resources.
- `validation` `error` `{input}` - input (i.e. payload, query, params, headers) validation failed.
  Includes the error.
- `validation` `response` `error` - response validation failed. Includes the error message.

##### <a name="server.events.response" /> `'response'` Event

当响应被发送回客户端，`'response'` 事件类型将被触发（或当客户端连接关闭并且没有响应发送，在这种情况下 [`request.response`](#request.response) 为 `null`)。
每个请求发出一个事件。`'response'` 事件控制使用的函数签名 `function(request)` 如下：

- `request` - the [request object](#request).

```js
server.events.on('response', (request) => {

    console.log(`Response sent for request: ${request.info.id}`);
});
```

##### <a name="server.events.route" /> `'route'` Event

The `'route'` event type is emitted when a route is added via [`server.route()`](#server.route()).
The `'route'` event handler uses the function signature `function(route)` where:

- `route` - the [route information](#request.route). The `route` object must not be modified.

```js
server.events.on('route', (route) => {

    console.log(`New route added: ${route.path}`);
});
```

##### <a name="server.events.start" /> `'start'` Event

The `'start'` event type is emitted when the server is started using [`server.start()`](#server.start()).
The `'start'` event handler uses the function signature `function()`.

```js
server.events.on('start', () => {

    console.log('Server started');
});
```

##### <a name="server.events.stop" /> `'stop'` Event

The `'stop'` event type is emitted when the server is stopped using [`server.stop()`](#server.stop()).
The `'stop'` event handler uses the function signature `function()`.

```js
server.events.on('stop', () => {

    console.log('Server stopped');
});
```

#### <a name="server.info" /> `server.info`

访问： 只读。

一个包含如下服务器信息的对象：

- `id` - a unique server identifier (using the format '{hostname}:{pid}:{now base36}').

- `created` - server creation timestamp.

- `started` - server start timestamp (`0` when stopped).

- `port` - the connection port based on the following rules:

    - before the server has been started: the configured [`port`](#server.options.port) value.
    - after the server has been started: the actual port assigned when no port is configured or was
      set to `0`.

- `host` - The [`host`](#server.options.host) configuration value.

- `address` - the active IP address the connection was bound to after starting. Set to `undefined`
  until the server has been started or when using a non TCP port (e.g. UNIX domain socket).

- `protocol` - the protocol used:

    - `'http'` - HTTP.
    - `'https'` - HTTPS.
    - `'socket'` - UNIX domain socket or Windows named pipe.

- `uri` - a string representing the connection (e.g. 'http://example.com:8080' or
  'socket:/unix/domain/socket/path'). Contains the [`uri`](#server.options.uri) value if set,
  otherwise constructed from the available settings. If no [`port`](#server.options.port) is
  configured or is set to `0`, the `uri` will not include a port component until the server is
  started.

```js
const Hapi = require('hapi');
const server = Hapi.server({ port: 80 });

console.log(server.info.port);            // 80
```

#### <a name="server.listener" /> `server.listener`

访问： 只读和监听公共接口。

node HTTP 服务器对象。

```js
const Hapi = require('hapi');
const SocketIO = require('socket.io');

const server = Hapi.server({ port: 80 });

const io = SocketIO.listen(server.listener);
io.sockets.on('connection', (socket) => {

    socket.emit({ msg: 'welcome' });
});
```

#### <a name="server.load" /> `server.load`

访问： 只读。

包含流程负载指标的对象 (当 [`load.sampleInterval`](#server.options.load) 已启用):

- `eventLoopDelay` - 时间循环延迟毫秒.
- `heapUsed` - V8 堆使用情况.
- `rss` - RSS 内存使用情况.

```js
const Hapi = require('hapi');
const server = Hapi.server({ load: { sampleInterval: 1000 } });

console.log(server.load.rss);
```

#### <a name="server.methods" /> `server.methods`

访问： 只读。

Server methods are functions registered with the server and used throughout the application as a
common utility. Their advantage is in the ability to configure them to use the built-in cache and
share across multiple request handlers without having to create a common module.

`sever.methods` is an object which provides access to the methods registered via
[server.method()](#server.method()) where each server method name is an object
property.

```js
const Hapi = require('hapi');
const server = Hapi.server();

server.method('add', (a, b) => (a + b));
const result = server.methods.add(1, 2);    // 3
```

#### <a name="server.mime" /> `server.mime`

访问： 只读且 **mimos** 公共接口。

Provides access to the server MIME database used for setting content-type information. The object
must not be modified directly but only through the [`mime`](#server.options.mime) server setting.

```js
const Hapi = require('hapi');

const options = {
    mime: {
        override: {
            'node/module': {
                source: 'steve',
                compressible: false,
                extensions: ['node', 'module', 'npm'],
                type: 'node/module'
            }
        }
    }
};

const server = Hapi.server(options);
console.log(server.mime.path('code.js').type)        // 'application/javascript'
console.log(server.mime.path('file.npm').type)        // 'node/module'
```

#### <a name="server.plugins" /> `server.plugins`

访问： 读 / 写.

包含每个注册插件公开的值的对象，其中每个键是一个插件名称，值是每个插件使用 [`server.expose()`](#server.expose()) 公开的属性. 插件可以直接或通过 `server.expose()` 方法设置 `server.plugins[name]` 对象的值

```js
exports.plugin = {
    name: 'example',
    register: function (server, options) {

        server.expose('key', 'value');
        server.plugins.example.other = 'other';

        console.log(server.plugins.example.key);      // 'value'
        console.log(server.plugins.example.other);    // 'other'
    }
};
```

#### <a name="server.realm" /> `server.realm`

访问： 只读。

The realm object contains sandboxed server settings specific to each plugin or authentication
strategy. When registering a plugin or an authentication scheme, a `server` object reference is
provided with a new `server.realm` container specific to that registration. It allows each plugin
to maintain its own settings without leaking and affecting other plugins.

For example, a plugin can set a default file path for local resources without breaking other
plugins' configured paths. When calling [`server.bind()`](#server.bind()), the active realm's
`settings.bind` property is set which is then used by routes and extensions added at the same level
(server root or plugin).

The `server.realm` object contains:

- `modifiers` - when the server object is provided as an argument to the plugin `register()`
  method, `modifiers` provides the registration preferences passed the
  [`server.register()`](#server.register()) method and includes:

    - `route` - routes preferences:

        - `prefix` - the route path prefix used by any calls to [`server.route()`](#server.route())
          from the server. Note that if a prefix is used and the route path is set to `'/'`, the
          resulting path will not include the trailing slash.
        - `vhost` - the route virtual host settings used by any calls to
          [`server.route()`](#server.route()) from the server.

- `parent` - the realm of the parent server object, or `null` for the root server.

- `plugin` - the active plugin name (empty string if at the server root).

- `pluginOptions` - the plugin options passed at registration.

- `plugins` - plugin-specific state to be shared only among activities sharing the same active
  state. `plugins` is an object where each key is a plugin name and the value is the plugin state.

- `settings` - settings overrides:

    - `files.relativeTo`
    - `bind`

The `server.realm` object should be considered read-only and must not be changed directly except
for the `plugins` property which can be directly manipulated by each plugin, setting its properties
inside `plugins[name]`.

```js
exports.register = function (server, options) {

    console.log(server.realm.modifiers.route.prefix);
};
```

#### <a name="server.registrations" /> `server.registrations`

访问： 只读。

当前注册的插件的对象，其中每个 key 对应注册的插件名称，值是包含的对象：

- `version` - 插件版本.
- `name` - 插件名称.
- `options` - (可选) 注册期间传递给插件的选项。

#### <a name="server.settings" /> `server.settings`

访问： 只读。

应用默认值后的服务器配置对象。

```js
const Hapi = require('hapi');
const server = Hapi.server({
    app: {
        key: 'value'
    }
});

console.log(server.settings.app);   // { key: 'value' }
```

#### <a name="server.states" /> `server.states`

访问： 只读和 **statehood** 公共接口.

服务器 cookies 管理器.

#### <a name="server.states.settings" /> `server.states.settings`

访问： 只读。

服务器 cookies 管理器设置. 设置基于 [`server.options.state`](#server.options.state) 中配置的值.

#### <a name="server.states.cookies" /> `server.states.cookies`

访问： 只读。

包含通过 [`server.state()`](#server.state()) 添加的每个cookie的配置的对象，其中每个 key 是 cookie 名称，值是配置对象。

#### <a name="server.states.names" /> `server.states.names`

访问： 只读。

包含所有已配置【configured】 cookie 的名称的数组。

#### <a name="server.type" /> `server.type`

访问： 只读。

一个字符串，标明【indicating】监听类型，其中：
- `'socket'` - UNIX domain socket or Windows named pipe.
- `'tcp'` - an HTTP listener.

#### <a name="server.version" /> `server.version`

访问： 只读。

**hapi** 版本号

```js
const Hapi = require('hapi');
const server = Hapi.server();

console.log(server.version);        // '17.0.0'
```

### <a name="server.auth.default()" /> `server.auth.default(options)`

设置应用于每个路由的默认认证策略【strategy】，其中：

- `options` - 其中之一:

    - 具有默认策略名称的字符串
    - 使用与 [route `auth` handler options](#route.options.auth) 相同格式的身份验证配置对象.

返回值: none.

当路由配置指定 `auth` 为 `false` 时，默认值不适用，或已配置身份验证策略 (包含 [`strategy`](#route.options.auth.strategy) 或 [`strategies`](#route.options.auth.strategies) 身份认证设置。否则，路由验证配置将应用于默认值。

Note that if the route has authentication configured, the default only applies at the time of
adding the route, not at runtime. This means that calling `server.auth.default()` after adding a
route with some authentication config will have no impact on the routes added prior. However, the
default will apply to routes added before `server.auth.default()` is called if those routes lack
any authentication config.

可以通过 [`server.auth.settings.default`](#server.auth.settings.default) 访问默认的 auth 策略配置。
要获【obtain】取路由的主动身份验证配置，请使用 `server.auth.lookup(request.route)`.

```js
const Hapi = require('hapi');
const server = Hapi.server({ port: 80 });

server.auth.scheme('custom', scheme);
server.auth.strategy('default', 'custom');
server.auth.default('default');

server.route({
    method: 'GET',
    path: '/',
    handler: function (request, h) {

        return request.auth.credentials.user;
    }
});
```

### <a name="server.auth.scheme()" /> `server.auth.scheme(name, scheme)`

注册身份验证方案:

- `name` - 方案名称。
- `scheme` - 用签名 `function(server, options)` 实现该方案 其中:
    - `server` - 一个参考方案被添加到服务器对象。
    - `options` - (可选的) 当实例一个策略时， 传给 [`server.auth.strategy()`](#server.auth.strategy()) 的 `options` 参数.

返回值: none.

当调用时，`scheme` 函数必须返回一个 [authentication scheme object](#authentication-scheme)

#### 身份验证方案

身份验证方案是具有以下属性的对象：

- `api` - (可选) 通过 [`server.auth.api`](#server.auth.api) 公开的对象.

- `async authenticate(request, h)` - (必要) 为使用身份验证方案配置的每个传入请求调用 [lifecycle method](#lifecycle-methods) 函数。 方法提供了两个特殊的工具包方法，用于返回经过身份验证或未经身份验证的方法结果:
    - [`h.authenticated()`](#h.authenticated()) - 表示【indicate】请求已成功验证。
    - [`h.unauthenticated()`](#h.unauthenticated()) - 表示请求验证失败.

- `async payload(request, h)` - (可选) 用于验证请求有效负载的 [lifecycle method](#lifecycle-methods)。

- `async response(request, h)` - (可选) 一个 [lifecycle method](#lifecycle-methods) 用于写入响应头或有效负荷之前描述带有身份认证头的响应。

- `options` - (可选) 具有以下键的对象：
    - `payload` - 如果为 `true`, 要求有效负载验证作为方案的一部分，并禁止【forbids】路由禁用有效负载验证. 默认为 `false`。

When the scheme `authenticate()` method implementation throws an error or calls
[`h.unauthenticated()`](#h.unauthenticated()), the specifics of the error affect whether additional
authentication strategies will be attempted (if configured for the route). If the error includes a
message, no additional strategies will be attempted. If the `err` does not include a message but
does include the scheme name (e.g. `Boom.unauthorized(null, 'Custom')`), additional strategies will
be attempted in the order of preference (defined in the route configuration). If authentication
fails, the scheme names will be present in the 'WWW-Authenticate' header.

When the scheme `payload()` method throws an error with a message, it means payload validation
failed due to bad payload. If the error has no message but includes a scheme name (e.g.
`Boom.unauthorized(null, 'Custom')`), authentication may still be successful if the route
[`auth.payload`](#route.options.auth.payload) configuration is set to `'optional'`.

```js
const Hapi = require('hapi');
const server = Hapi.server({ port: 80 });

const scheme = function (server, options) {

    return {
        authenticate: function (request, h) {

            const req = request.raw.req;
            const authorization = req.headers.authorization;
            if (!authorization) {
                throw Boom.unauthorized(null, 'Custom');
            }

            return h.authenticated({ credentials: { user: 'john' } });
        }
    };
};

server.auth.scheme('custom', scheme);
```

### <a name="server.auth.strategy()" /> `server.auth.strategy(name, scheme, [options])`

注册身份验证策略:

- `name` - 策略名称。
- `scheme` - 方案名称 (必须事先使用 [`server.auth.scheme()`](#server.auth.scheme())) 注册。
- `options` - 基于方案要求的方案选项。

返回值: none.

```js
const Hapi = require('hapi');
const server = Hapi.server({ port: 80 });

server.auth.scheme('custom', scheme);
server.auth.strategy('default', 'custom');

server.route({
    method: 'GET',
    path: '/',
    config: {
        auth: 'default',
        handler: function (request, h) {

            return request.auth.credentials.user;
        }
    }
});
```

### <a name="server.auth.test()" /> `await server.auth.test(strategy, request)`

针对身份验证策略测试请求：

- `strategy` - 使用 [`server.auth.strategy()`](#server.auth.strategy()) 注册的策略名称.
- `request` - the [request object](#request).

返回值: 验证成功时的身份验证凭据对象，否则抛出错误。

请注意，`test()` 方法不考虑【take into account】路由验证配置。它也不执行【perform】有效负载认证。它仅限于【limited to】基本策略身份验证执行【execution】。它不包括验证范围，入口或其他路由属性。

```js
const Hapi = require('hapi');
const server = Hapi.server({ port: 80 });

server.auth.scheme('custom', scheme);
server.auth.strategy('default', 'custom');

server.route({
    method: 'GET',
    path: '/',
    handler: async function (request, h) {

        try {
            const credentials = await request.server.auth.test('default', request);
            return { status: true, user: credentials.name };
        }
        catch (err) {
            return { status: false };
        }
    }
});
```

### <a name="server.bind()" /> `server.bind(context)`

在添加路由或扩展时，设置用作默认绑定对象的全局上下文:

- `context` - the object used to bind `this` in [lifecycle methods](#lifecycle-methods) such as
  the [route handler](#route.options.handler) and [extension methods](#server.ext()). The context
  is also made available as [`h.context`](#h.context).

返回值: none.

在插件中设置上下文时，上下文仅应用于插件设置的方法。 请注意，上下文仅适用于设置后添加的路由和扩展。如果绑定的方法是箭头函数，则忽略。

```js
const handler = function (request, h) {

    return this.message;    // Or h.context.message
};

exports.plugin = {
    name: 'example',
    register: function (server, options) {

        const bind = {
            message: 'hello'
        };

        server.bind(bind);
        server.route({ method: 'GET', path: '/', handler });
    }
};
```

### <a name="server.cache()" /> `server.cache(options)`

规定[provision]服务器缓存设施中的缓存段：

- `options` - [**catbox** policy](https://github.com/hapijs/catbox#policy) 配置如下:

    - `expiresIn` - 自项目保存在缓存中，用毫秒表示的相对过期时间。 不能和 `expiresAt` 一起使用.

    - `expiresAt` - 使用 'HH:MM' 格式表示的时间, 此时所有缓存记录都将过期. 使用本地时间. 不能和 `expiresIn` 一起使用.

    - `generateFunc` - 如果在调用 `get()` 时未在缓存中找到一个缓存项，用于生成新缓存项的函数. 该方法的签名是 `async function(id, flags)` 其中:

          - `id` - 提供给 `get()` 方法的 `id` 字符串或对象。
          - `flags` - 用于将其他标志传递回缓存的对象，其中：
              - `ttl` - 缓存 ttl 值，以毫秒为单位。设置为 `0` 以跳过存储在缓存中。 默认为缓存全局策略。

    - `staleIn` - 当提供 `generateFunc` 时，存储在缓存中的项目标记为失效【stale】并尝试【attempt】重新生成它的毫秒数。 必须小于 `expiresIn`。

    - `staleTimeout` - 检查项目是否过时之前要等待的毫秒数.

    - `generateTimeout` - 当 `generateFunc` 函数超时毫秒数。最终返回值时, 它存储在缓存中以供将来请求使用. 当 `generateFunc` 指定是，该值是必要的。 设置 `false` 将禁用可能导致所有 `get()` 请求永远被卡住的超时。

    - `generateOnReadError` - 如果为 `false`, 上游缓存读取错误将停止 `cache.get()` 方法调用 generate 函数，而是传回缓存错误。默认为 `true`.

    - `generateIgnoreWriteError` - 如果为 `false`, 调用 `cache.get()` 时出现的上游缓存写入错误会被调用时返回. 默认为 `true`.

    - `dropOnError` - 如果为 `true`, `generateFunc` 中的错误或超时导致超时的值会从缓存中逐出。默认为 `true`.

    - `pendingGenerateTimeout` - 当指定 id 进程调用 `generateFunc` 时的毫秒数, 后续的 `generateFunc` 会被允许. 默认为 `0` (no
      blocking of concurrent `generateFunc` calls beyond `staleTimeout`).

    - `cache` - 配置在 [`server.cache`](#server.config.cache) 的缓存名称. 默认为默认的缓存名。

    - `segment` - segment 字符串名, 用于隔离【isolate】缓存分区【partition】中的缓存项目。在插件中调用时，默认为插件名称 '!name'。在服务器方法中, 默认为服务器方法名 '#name'。在插件外部调用时，该值是必要的。

    - `shared` - 如果为 `true`, 允许多个缓存共享同一个 segment。 默认为`false`.

```js
const Hapi = require('hapi');

async function example() {

    const server = Hapi.server({ port: 80 });
    const cache = server.cache({ segment: 'countries', expiresIn: 60 * 60 * 1000 });
    await cache.set('norway', { capital: 'oslo' });
    const value = await cache.get('norway');
}
```

### <a name="server.cache.provision()" /> `await server.cache.provision(options)`

Provisions a server cache as described in [`server.cache`](#server.config.cache) where:

- `options` - same as the server [`cache`](#server.options.cache) configuration options.

返回值: none.

Note that if the server has been initialized or started, the cache will be automatically started
to match the state of any other provisioned server cache.

```js
const Hapi = require('hapi');

async function example() {

    const server = Hapi.server({ port: 80 });
    await server.initialize();
    await server.cache.provision({ engine: require('catbox-memory'), name: 'countries' });

    const cache = server.cache({ cache: 'countries', expiresIn: 60 * 60 * 1000 });
    await cache.set('norway', { capital: 'oslo' });
    const value = await cache.get('norway');
}
```

### <a name="server.control()" /> `server.control(server)`

Links another server to the initialize/start/stop state of the current server by calling the
controlled server `initialize()`/`start()`/`stop()` methods whenever the current server methods
are called, where:

- `server` - the **hapi** server object to be controlled.

### <a name="server.decoder()" /> `server.decoder(encoding, decoder)`

Registers a custom content decoding compressor to extend the built-in support for `'gzip'` and
'`deflate`' where:

- `encoding` - the decoder name string.

- `decoder` - a function using the signature `function(options)` where `options` are the encoding
  specific options configured in the route [`payload.compression`](#route.options.payload.compression)
  configuration option, and the 返回值 is an object compatible with the output of node's
  [`zlib.createGunzip()`](https://nodejs.org/api/zlib.html#zlib_zlib_creategunzip_options).

返回值: none.

```js
const Zlib = require('zlib');
const Hapi = require('hapi');
const server = Hapi.server({ port: 80, routes: { payload: { compression: { special: { chunkSize: 16 * 1024 } } } } });

server.decoder('special', (options) => Zlib.createGunzip(options));
```

### <a name="server.decorate()" /> `server.decorate(type, property, method, [options])`

Extends various framework interfaces with custom methods where:

- `type` - the interface being decorated. Supported types:

    - `'handler'` - adds a new handler type to be used in [routes handlers](#route.options.handler).
    - `'request'` - adds methods to the [Request object](#request).
    - `'server'` - adds methods to the [Server](#server) object.
    - `'toolkit'` - adds methods to the [response toolkit](#response-toolkit).

- `property` - the object decoration key name or symbol.

- `method` - the extension function or other value.

- `options` - (可选) supports the following optional settings:
    - `apply` - when the `type` is `'request'`, if `true`, the `method` function is invoked using
      the signature `function(request)` where `request` is the current request object and the
      returned value is assigned as the decoration.
    - `extend` - if `true`, overrides an existing decoration. The `method` must be a function with
      the signature `function(existing)` where:
        - `existing` - is the previously set decoration method value.
        - must return the new decoration function or value.
        - cannot be used to extend handler decorations.

返回值: none.

```js
const Hapi = require('hapi');
const server = Hapi.server({ port: 80 });

const success = function () {

    return this.response({ status: 'ok' });
};

server.decorate('toolkit', 'success', success);

server.route({
    method: 'GET',
    path: '/',
    handler: function (request, h) {

        return h.success();
    }
});
```

注册处理程序装饰时, `method` 必须使用签名的函数 `function(route, options)` 其中:

- `route` - [route information](#request.route).
- `options` - 处理程序配置中提供的配置对象。

```js
const Hapi = require('hapi');

async function example() {

    const server = Hapi.server({ host: 'localhost', port: 8000 });

    // Defines new handler for routes on this server

    const handler = function (route, options) {

        return function (request, h) {

            return 'new handler: ' + options.msg;
        }
    };

    server.decorate('handler', 'test', handler);

    server.route({
        method: 'GET',
        path: '/',
        handler: { test: { msg: 'test' } }
    });

    await server.start();
}
```

The `method` function can have a `defaults` object or function property. If the property is set to
an object, that object is used as the default route config for routes using this handler. If the
property is set to a function, the function uses the signature `function(method)` and returns the
route default configuration.

```js
const Hapi = require('hapi');
const server = Hapi.server({ host: 'localhost', port: 8000 });

const handler = function (route, options) {

    return function (request, h) {

        return 'new handler: ' + options.msg;
    }
};

// Change the default payload processing for this handler

handler.defaults = {
    payload: {
        output: 'stream',
        parse: false
    }
};

server.decorate('handler', 'test', handler);
```

### <a name="server.dependency()" /> `server.dependency(dependencies, [after])`

在插件中用于声明【declare】对其他 [plugins](#plugins) 所需的依赖：

- `dependencies` - 单个字符串或插件名称字符串数组，必须注册才能使此插件运行【operate】。 列出的插件必须在初始化或启动服务器之前注册。

- `after` - (可选) 在注册了所有指定的依赖项之后且在服务器启动之前调用的函数。仅在初始化或启动服务器时才调用该函数。 函数签名是 `async function(server)` 其中：

    - `server` - 服务器调用 `dependency()` 方法

返回值: none.

`after` 方法与在 `'onPreStart'` 上设置服务器扩展点相同【identical】。

如果检测【detected】到循环依赖关系，, 异常【exception】将会被抛出 (例如 两个插件各有一个可以在另一个之后调用的 `after` 函数)。

该方法不提供应使用 [npm peer dependencies](https://nodejs.org/en/blog/npm/peer-dependencies/) 实现的版本依赖性。

```js
const after = function (server) {

    // Additional plugin registration logic
};

exports.plugin = {
    name: 'example',
    register: function (server, options) {

        server.dependency('yar', after);
    }
};
```

依赖关系也可以通过插件 `dependencies` 属性设置(不支持设置 `after`)：

```js
exports.plugin = {
    name: 'test',
    version: '1.0.0',
    dependencies: 'yar',
    register: function (server, options) { }
};
```

### <a name="server.encoder()" /> `server.encoder(encoding, encoder)`

注册一个自定义内容编码压缩器，以扩展对  `'gzip'` and `'deflate'` 的支持，其中：

- `encoding` - 编码器名称的字符串。

- `encoder` - 使用签名 `function(options)` 的函数，其中 `options` 是路由 [`compression`](#route.options.compression) 选项中配置的编码特定选项， 返回值为与 node 的[`zlib.createGzip()`](https://nodejs.org/api/zlib.html#zlib_zlib_creategzip_options) 输出兼容的对象。

返回值: none.

```js
const Zlib = require('zlib');
const Hapi = require('hapi');
const server = Hapi.server({ port: 80, routes: { compression: { special: { chunkSize: 16 * 1024 } } } });

server.encoder('special', (options) => Zlib.createGzip(options));
```

### <a name="server.event()" /> `server.event(events)`

Register custom application events where:

- `events` - must be one of:

    - 一个事件名称字符串.

    - 带有以下可选键的事件选项对象 (除非另有说明):

        - `name` - 事件名称字符串 (必须).

        - `channels` - a string or array of strings specifying the event channels available.
          Defaults to no channel restrictions (event updates can specify a channel or not).

        - `clone` - if `true`, the `data` object passed to [`server.events.emit()`](#server.events.emit())
          is cloned before it is passed to the listeners (unless an override specified by each
          listener). Defaults to `false` (`data` is passed as-is).

        - `spread` - if `true`, the `data` object passed to [`server.event.emit()`](#server.event.emit())
          must be an array and the `listener` method is called with each array element passed as a
          separate argument (unless an override specified by each listener). This should only be
          used when the emitted data structure is known and predictable. Defaults to `false` (`data`
          is emitted as a single argument regardless of its type).

        - `tags` - if `true` and the `criteria` object passed to [`server.event.emit()`](#server.event.emit())
          includes `tags`, the tags are mapped to an object (where each tag string is the key and
          the value is `true`) which is appended to the arguments list at the end. A configuration
          override can be set by each listener. Defaults to `false`.

        - `shared` - if `true`, the same event `name` can be registered multiple times where the
          second registration is ignored. Note that if the registration config is changed between
          registrations, only the first configuration is used. Defaults to `false` (a duplicate
          registration will throw an error).

    - 一个 [**podium**](https://github.com/hapijs/podium) 触发器对象。

    - 包含上述任何内容的数组

返回值: none.

```js
const Hapi = require('hapi');

async function example() {

    const server = Hapi.server({ port: 80 });
    server.event('test');
    server.events.on('test', (update) => console.log(update));
    await server.events.emit('test', 'hello');
}
```

### <a name="server.events.emit()" /> `await server.events.emit(criteria, data)`

Emits a custom application event to all the subscribed listeners where:

- `criteria` - the event update criteria which must be one of:

    - the event name string.
    - an object with the following optional keys (unless noted otherwise):
        - `name` - the event name string (required).
        - `channel` - the channel name string.
        - `tags` - a tag string or array of tag strings.

- `data` - the value emitted to the subscribers. If `data` is a function, the function signature
  is `function()` and it called once to generate (返回值) the actual data emitted to the
  listeners. If no listeners match the event, the `data` function is not invoked.

返回值: none.

Note that events must be registered before they can be emitted or subscribed to by calling
[`server.event(events)`](#server.event()). This is done to detect event name misspelling and
invalid event activities.

```js
const Hapi = require('hapi');

async function example() {

    const server = Hapi.server({ port: 80 });
    server.event('test');
    server.events.on('test', (update) => console.log(update));
    await server.events.emit('test', 'hello');          // await is optional
}
```

### <a name="server.events.on()" /> `server.events.on(criteria, listener)`

Subscribe to an event where:

- `criteria` - the subscription criteria which must be one of:

    - event name string which can be any of the [built-in server events](#server.events) or a
      custom application event registered with [`server.event()`](#server.event()).

    - a criteria object with the following optional keys (unless noted otherwise):

        - `name` - (required) the event name string.

        - `channels` - a string or array of strings specifying the event channels to subscribe to.
          If the event registration specified a list of allowed channels, the `channels` array must
          match the allowed channels. If `channels` are specified, event updates without any
          channel designation will not be included in the subscription. Defaults to no channels
          filter.

        - `clone` - if `true`, the `data` object passed to [`server.event.emit()`](#server.event.emit())
           is cloned before it is passed to the `listener` method. Defaults to the event
           registration option (which defaults to `false`).

        - `count` - a positive integer indicating the number of times the `listener` can be called
          after which the subscription is automatically removed. A count of `1` is the same as
          calling `server.events.once()`. Defaults to no limit.

        - `filter` - the event tags (if present) to subscribe to which can be one of:

            - a tag string.
            - an array of tag strings.
            - an object with the following:

                - `tags` - a tag string or array of tag strings.
                - `all` - if `true`, all `tags` must be present for the event update to match the
                  subscription. Defaults to `false` (at least one matching tag).

        - `spread` - if `true`, and the `data` object passed to [`server.event.emit()`](#server.event.emit())
          is an array, the `listener` method is called with each array element passed as a separate
          argument. This should only be used when the emitted data structure is known and
          predictable. Defaults to the event registration option (which defaults to `false`).

        - `tags` - if `true` and the `criteria` object passed to [`server.event.emit()`](#server.event.emit())
          includes `tags`, the tags are mapped to an object (where each tag string is the key and
          the value is `true`) which is appended to the arguments list at the end. Defaults to the
          event registration option (which defaults to `false`).

- `listener` - the handler method set to receive event updates. The function signature depends on
  the event argument, and the `spread` and `tags` options.

返回值: none.

```js
const Hapi = require('hapi');

async function example() {

    const server = Hapi.server({ port: 80 });
    server.event('test');
    server.events.on('test', (update) => console.log(update));
    await server.events.emit('test', 'hello');
}
```

### <a name="server.events.once()" /> `server.events.once(criteria, listener)`

Same as calling [`server.events.on()`](#server.events.on()) with the `count` option set to `1`.

返回值: none.

```js
const Hapi = require('hapi');

async function example() {

    const server = Hapi.server({ port: 80 });
    server.event('test');
    server.events.once('test', (update) => console.log(update));
    await server.events.emit('test', 'hello');
    await server.events.emit('test', 'hello');       // Ignored
}
```

### <a name="server.events.once.await()" /> `await server.events.once(criteria)`

Same as calling [`server.events.on()`](#server.events.on()) with the `count` option set to `1`.

 返回值: a promise that resolves when the event is emitted.

```js
const Hapi = require('hapi');

async function example() {

    const server = Hapi.server({ port: 80 });
    server.event('test');
    const pending = server.events.once('test');
    await server.events.emit('test', 'hello');
    const update = await pending;
}
```

### <a name="server.expose()" /> `server.expose(key, value)`

Used within a plugin to expose a property via [`server.plugins[name]`](#server.plugins) where:

- `key` - the key assigned ([`server.plugins[name][key]`](#server.plugins)).
- `value` - the value assigned.

返回值: none.

```js
exports.plugin =
    name: 'example',
    register: function (server, options) {

        server.expose('util', () => console.log('something'));
    }
};
```

### <a name="server.expose.obj()" /> `server.expose(obj)`

Merges an object into to the existing content of [`server.plugins[name]`](#server.plugins) where:

- `obj` - the object merged into the exposed properties container.

返回值: none.

```js
exports.plugin = {
    name: 'example',
    register: function (server, options) {

        server.expose({ util: () => console.log('something') });
    }
};
```

Note that all the properties of `obj` are deeply cloned into [`server.plugins[name]`](#server.plugins),
so avoid using this method for exposing large objects that may be expensive to clone or singleton
objects such as database client objects. Instead favor [`server.expose(key, value)`](#server.expose()),
which only copies a reference to `value`.

### <a name="server.ext()" /> `server.ext(events)`

Registers an extension function in one of the [request lifecycle](#request-lifecycle) extension
points where:

- `events` - an object or array of objects with the following:

    - `type` - (required) the extension point event name. The available extension points include
      the [request extension points](#request-lifecycle) as well as the following server extension
      points:

        - `'onPreStart'` - called before the connection listeners are started.
        - `'onPostStart'` - called after the connection listeners are started.
        - `'onPreStop'` - called before the connection listeners are stopped.
        - `'onPostStop'` - called after the connection listeners are stopped.

    - `method` - (required) a function or an array of functions to be executed at a specified point
      during request processing. The required extension function signature is:

        - server extension points: `async function(server)` where:

            - `server` - the server object.
            - `this` - the object provided via `options.bind` or the current active context set
              with [`server.bind()`](#server.bind()).

        - request extension points: a [lifecycle method](#lifecycle-methods).

    - `options` - (可选) an object with the following:

        - `before` - a string or array of strings of plugin names this method must execute before
          (on the same event). Otherwise, extension methods are executed in the order added.

        - `after` - a string or array of strings of plugin names this method must execute after (on
          the same event). Otherwise, extension methods are executed in the order added.

        - `bind` - a context object passed back to the provided method (via `this`) when called.
           Ignored if the method is an arrow function.

        - `sandbox` - if set to `'plugin'` when adding a [request extension points](#request-lifecycle)
          the extension is only added to routes defined by the current plugin. Not allowed when
          configuring route-level extensions, or when adding server extensions. Defaults to
          `'server'` which applies to any route added to the server the extension is added to.

返回值: none.

```js
const Hapi = require('hapi');

async function example() {

    const server = Hapi.server({ port: 80 });

    server.ext({
        type: 'onRequest',
        method: function (request, h) {

            // Change all requests to '/test'

            request.setUrl('/test');
            return h.continue;
        }
    });

    server.route({ method: 'GET', path: '/test', handler: () => 'ok' });
    await server.start();

    // All requests will get routed to '/test'
}
```

### <a name="server.ext.args()" /> `server.ext(event, method, [options])`

Registers a single extension event using the same properties as used in
[`server.ext(events)`](#server.ext()), but passed as arguments.

返回值: none.

```js
const Hapi = require('hapi');

async function example() {

    const server = Hapi.server({ port: 80 });

    server.ext('onRequest', function (request, h) {

        // Change all requests to '/test'

        request.setUrl('/test');
        return h.continue;
    });

    server.route({ method: 'GET', path: '/test', handler: () => 'ok' });
    await server.start();

    // All requests will get routed to '/test'
}
```

### <a name="server.initialize()" /> `await server.initialize()`

Initializes the server (starts the caches, finalizes plugin registration) but does not start
listening on the connection port.

返回值: none.

Note that if the method fails and throws an error, the server is considered to be in an undefined
state and should be shut down. In most cases it would be impossible to fully recover as the various
plugins, caches, and other event listeners will get confused by repeated attempts to start the
server or make assumptions about the healthy state of the environment. It is recommended to abort
the process when the server fails to start properly. If you must try to resume after an error, call
[`server.stop()`](#server.stop()) first to reset the server state.

```js
const Hapi = require('hapi');
const Hoek = require('hoek');

async function example() {

    const server = Hapi.server({ port: 80 });
    await server.initialize();
}
```

### <a name="server.inject()" /> `await server.inject(options)`

Injects a request into the server simulating an incoming HTTP request without making an actual
socket connection. Injection is useful for testing purposes as well as for invoking routing logic
internally without the overhead and limitations of the network stack.

The method utilizes the [**shot**](https://github.com/hapijs/shot) module for performing
injections, with some additional options and response properties:

- `options` - can be assigned a string with the requested URI, or an object with:

    - `method` - (可选) the request HTTP method (e.g. `'POST'`). Defaults to `'GET'`.

    - `url` - (required) the request URL. If the URI includes an authority
      (e.g. `'example.com:8080'`), it is used to automatically set an HTTP 'Host' header, unless
      one was specified in `headers`.

    - `headers` - (可选) an object with optional request headers where each key is the header
      name and the value is the header content. Defaults to no additions to the default **shot**
      headers.

    - `payload` - (可选) an string, buffer or object containing the request payload. In case of
      an object it will be converted to a string for you. Defaults to no payload. Note that payload
      processing defaults to `'application/json'` if no 'Content-Type' header provided.

    - `credentials` - (可选) an credentials object containing authentication information. The
      `credentials` are used to bypass the default authentication strategies, and are validated
      directly as if they were received via an authentication scheme. Defaults to no credentials.

    - `artifacts` - (可选) an artifacts object containing authentication artifact information.
      The `artifacts` are used to bypass the default authentication strategies, and are validated
      directly as if they were received via an authentication scheme. Ignored if set without
      `credentials`. Defaults to no artifacts.

    - `app` - (可选) sets the initial value of `request.app`, defaults to `{}`.

    - `plugins` - (可选) sets the initial value of `request.plugins`, defaults to `{}`.

    - `allowInternals` - (可选) allows access to routes with `config.isInternal` set to `true`.
      Defaults to `false`.

    - `remoteAddress` - (可选) sets the remote address for the incoming connection.

    - `simulate` - (可选) an object with options used to simulate client request stream
      conditions for testing:

        - `error` - if `true`, emits an `'error'` event after payload transmission (if any).
          Defaults to `false`.

        - `close` - if `true`, emits a `'close'` event after payload transmission (if any).
          Defaults to `false`.

        - `end` - if `false`, does not end the stream. Defaults to `true`.

        - `split` - indicates whether the request payload will be split into chunks. Defaults to
          `undefined`, meaning payload will not be chunked.

    - `validate` - (可选) if `false`, the `options` inputs are not validated. This is
      recommended for run-time usage of `inject()` to make it perform faster where input validation
      can be tested separately.

返回值: a response object with the following properties:

- `statusCode` - the HTTP status code.

- `headers` - an object containing the headers set.

- `payload` - the response payload string.

- `rawPayload` - the raw response payload buffer.

- `raw` - an object with the injection request and response objects:

    - `req` - the simulated node request object.
    - `res` - the simulated node response object.

- `result` - the raw handler response (e.g. when not a stream or a view) before it is
    serialized for transmission. If not available, the value is set to `payload`. Useful for
    inspection and reuse of the internal objects returned (instead of parsing the response
    string).

- `request` - the [request object](#request).

```js
const Hapi = require('hapi');

async function example() {

    const server = Hapi.server({ port: 80 });
    server.route({ method: 'GET', path: '/', handler: () => 'Success!' });

    const res = await server.inject('/');
    console.log(res.result);                // 'Success!'
}
```

### <a name="server.log()" /> `server.log(tags, [data, [timestamp]])`

记录无法与特定请求关联【associated】的服务器事件。当被调用时，服务器发出一个 `'log'` 事件，可以被其他侦听器或 [plugins](#plugins) 用来将信息或输出记录到控制台。参数有：

- `tags` - (必须) 字符串或字符串数组 (例如 `['error', 'database', 'read']`) 用于识别事件. 使用标签代替日志级别，并为描述和过滤事件提供更具表现力的机制【mechanism】。服务器内部生成的任何日志都包含 `'hapi'` 标签以及特定于事件的信息。

- `data` - (可选) 记录应用程序数据的消息字符串或对象。 如果 `data` 为一个函数, 函数签名为 `function()` 并且它调用一次来生成 (返回值) 发送给侦听器的实际数据。 如果没有侦听器匹配该事件，则不会调用 `data` 函数。

- `timestamp` - (可选) 以毫秒表示的时间戳。 默认为 `Date.now()` (当前).

返回值: none.

```js
const Hapi = require('hapi');
const server = Hapi.server({ port: 80 });

server.events.on('log', (event, tags) => {

    if (tags.error) {
        console.log(event);
    }
});

server.log(['test', 'error'], 'Test event');
```

### <a name="server.lookup()" /> `server.lookup(id)`

查找路径配置 其中：

- `id` - the [route identifier](#route.options.id).

返回值: 找到的 [route information](#request.route), 否则为 `null`。

```js
const Hapi = require('hapi');
const server = Hapi.server();
server.route({
    method: 'GET',
    path: '/',
    config: {
        id: 'root',
        handler: () => 'ok'
    }
});

const route = server.lookup('root');
```

### <a name="server.match()" /> `server.match(method, path, [host])`

查找路径配置 其中：

- `method` - HTTP 方法 (e.g. 'GET', 'POST')。
- `path` - 请求的路径 (必须以 '/' 开头)。
- `host` - (可选) hostname (匹配针对带有 `vhost` 的路由).

返回值: 找到的 [route information](#request.route), 否则为 `null`。

```js
const Hapi = require('hapi');
const server = Hapi.server();
server.route({
    method: 'GET',
    path: '/',
    config: {
        id: 'root',
        handler: () => 'ok'
    }
});

const route = server.match('get', '/');
```

### <a name="server.method()" /> `server.method(name, method, [options])`

注册一个 [server method](#server.methods) 其中：

- `name` - a unique method name used to invoke the method via [`server.methods[name]`](#server.method).

- `method` - the method function with a signature `async function(...args, [flags])` where:
    - `...args` - the method function arguments (can be any number of arguments or none).
    - `flags` - when caching is enabled, an object used to set optional method result flags:
        - `ttl` - `0` if result is valid but cannot be cached. Defaults to cache policy.

- `options` - (可选) configuration object:

    - `bind` - a context object passed back to the method function (via `this`) when called.
      Defaults to active context (set via [`server.bind()`](#server.bind()) when the method is
      registered. Ignored if the method is an arrow function.

    - `cache` - the same cache configuration used in [`server.cache()`](#server.cache()). The
      `generateTimeout` option is required.

    - `generateKey` - a function used to generate a unique key (for caching) from the arguments
      passed to the method function (the `flags` argument is not passed as input). The server
      will automatically generate a unique key if the function's arguments are all of types
      `'string'`, `'number'`, or `'boolean'`. However if the method uses other types of arguments,
      a key generation function must be provided which takes the same arguments as the function and
      returns a unique string (or `null` if no key can be generated).

返回值: none.

方法名称可以嵌套 (举例 `utils.users.get`) 它将自动在 [`server.methods`](#server.methods) (举例 通过 `server.methods.utils.users.get` 访问) 下创建完整路径.

配置启用缓存时, `server.methods[name].cache` 被赋予一个具有以下属性和方法的对象:
    - `await drop(...args)` - 一个函数，可用于清除给定键的缓存。
    - `stats` - 具有缓存统计信息的对象, 请参阅 **catbox** 获取统计文档。

单个参数的例子:

```js
const Hapi = require('hapi');

async function example() {

    const server = Hapi.server({ port: 80 });

    const add = (a, b) => (a + b);
    server.method('sum', add, { cache: { expiresIn: 2000, generateTimeout: 100 } });

    console.log(await server.methods.sum(4, 5));          // 9
}
```

对象参数的例子:

```js
const Hapi = require('hapi');

async function example() {

    const server = Hapi.server({ port: 80 });

    const addArray = function (array) {

        let sum = 0;
        array.forEach((item) => {

            sum += item;
        });

        return sum;
    };

    const options = {
        cache: { expiresIn: 2000, generateTimeout: 100 },
        generateKey: (array) => array.join(',')
    };

    server.method('sumObj', addArray, options);

    console.log(await server.methods.sumObj([5, 6]));     // 11
}
```

### <a name="server.method.array()" /> `server.method(methods)`

使用配置对象注册服务器方法函数，如 [`server.method()`](#server.method()) 中所述，其中：

- `methods` - 对象或对象数组，其中每个对象包含：

    - `name` - 方法名称.
    - `method` - 方法函数.
    - `options` - (可选) 设置.

返回值: none.

```js
const add = function (a, b) {

    return a + b;
};

server.method({
    name: 'sum',
    method: add,
    options: {
        cache: {
            expiresIn: 2000,
            generateTimeout: 100
        }
    }
});
```

### <a name="server.path()" /> `server.path(relativeTo)`

设置用于在使用相对路径时定位静态资源（文件和视图模板）的路径前缀：

- `relativeTo` - 路径前缀，附加到任意带有 `'.'` 的相对文件路径。

返回值: none.

请注意，在插件中设置路径仅适用于插件方法访问的资源。如果未设置路径，则服务器默认为 [route configuration](#server.options.routes) 使用
[`files.relativeTo`](#route.options.files) 设置. 该路径仅适用于设置后添加的路径。

```js
exports.plugin = {
    name: 'example',
    register: function (server, options) {

        // Assuming the Inert plugin was registered previously

        server.path(__dirname + '../static');
        server.route({ path: '/file', method: 'GET', handler: { file: './test.html' } });
    }
};
```

### <a name="server.register()" /> `await server.register(plugins, [options])`

Registers a plugin where:

- `plugins` - one or an array of:

    - a [plugin object](#plugins).

    - an object with the following:
        - `plugin` - a [plugin object](#plugins).
        - `options` - (可选) options passed to the plugin during registration.
        - `once`, `routes` - (可选) plugin-specific registration options as defined below.

- `options` - (可选) registration options (different from the options passed to the
  registration function):

    - `once` - if `true`, subsequent registrations of the same plugin are skipped without error.
      Cannot be used with plugin options. Defaults to `false`.
      If not set to `true`, an error will be thrown the second time a plugin is registered on the server.

    - `routes` - modifiers applied to each route added by the plugin:

        - `prefix` - string added as prefix to any route path (must begin with `'/'`). If a plugin
          registers a child plugin the `prefix` is passed on to the child or is added in front of
          the child-specific prefix.
        - `vhost` - virtual host string (or array of strings) applied to every route. The
          outer-most `vhost` overrides the any nested configuration.

返回值: none.

```js
async function example() {

    await server.register({ plugin: require('plugin_name'), options: { message: 'hello' } });
}
```

### <a name="server.route()" /> `server.route(route)`

Adds a route where:

- `route` - a route configuration object or an array of configuration objects where each object
  contains:

    - `path` - (required) the absolute path used to match incoming requests (must begin with '/').
      Incoming requests are compared to the configured paths based on the server's
      [`router`](#server.options.router) configuration. The path can include named parameters
      enclosed in `{}` which  will be matched against literal values in the request as described in
      [Path parameters](#path-parameters).

    - `method` - (required) the HTTP method. Typically one of 'GET', 'POST', 'PUT', 'PATCH',
      'DELETE', or 'OPTIONS'. Any HTTP method is allowed, except for 'HEAD'. Use `'*'` to match
      against any HTTP method (only when an exact match was not found, and any match with a
      specific method will be given a higher priority over a wildcard match). Can be assigned an
      array of methods which has the same result as adding the same route with different methods
      manually.

    - `vhost` - (可选) a domain string or an array of domain strings for limiting the route to
      only requests with a matching host header field. Matching is done against the hostname part
      of the header only (excluding the port). Defaults to all hosts.

    - `handler` - (required when [`handler`](#route.options.handler) is not set) the route
      handler function called to generate the response after successful authentication and
      validation.

    - `options` - additional [route options](#route-options). The `options` value can be an object
      or a function that returns an object using the signature `function(server)` where `server` is
      the server the route is being added to and `this` is bound to the current
      [realm](#server.realm)'s `bind` option.

    - `rules` - route custom rules object. The object is passed to each rules processor registered
      with [`server.rules()`](#server.rules()). Cannot be used if
      [`route.options.rules`](#route.options.rules) is defined.

返回值: none.

Note that the `options` object is deeply cloned (with the exception of `bind` which is shallowly
copied) and cannot contain any values that are unsafe to perform deep copy on.

```js
const Hapi = require('hapi');
const server = Hapi.server({ port: 80 });

// Handler in top level

server.route({ method: 'GET', path: '/status', handler: () => 'ok' });

// Handler in config

const user = {
    cache: { expiresIn: 5000 },
    handler: function (request, h) {

        return { name: 'John' };
    }
};

server.route({ method: 'GET', path: '/user', config: user });

// An array of routes

server.route([
    { method: 'GET', path: '/1', handler: function (request, h) { return 'ok'; } },
    { method: 'GET', path: '/2', handler: function (request, h) { return 'ok'; } }
]);
```

#### 路径参数

Parameterized paths are processed by matching the named parameters to the content of the incoming
request path at that path segment. For example, '/book/{id}/cover' will match '/book/123/cover' and
`request.params.id` will be set to `'123'`. Each path segment (everything between the opening '/'
and the closing '/' unless it is the end of the path) can only include one named parameter. A
parameter can cover the entire segment ('/{param}') or part of the segment ('/file.{ext}').  A path
parameter may only contain letters, numbers and underscores, e.g. '/{file-name}' is invalid
and '/{file_name}' is valid.

An optional '?' suffix following the parameter name indicates an optional parameter (only allowed
if the parameter is at the ends of the path or only covers part of the segment as in
'/a{param?}/b'). For example, the route '/book/{id?}' matches '/book/' with the value of
`request.params.id` set to an empty string `''`.

```js
const Hapi = require('hapi');
const server = Hapi.server({ port: 80 });

const getAlbum = function (request, h) {

    return 'You asked for ' +
        (request.params.song ? request.params.song + ' from ' : '') +
        request.params.album;
};

server.route({
    path: '/{album}/{song?}',
    method: 'GET',
    handler: getAlbum
});
```

In addition to the optional `?` suffix, a parameter name can also specify the number of matching
segments using the `*` suffix, followed by a number greater than 1. If the number of expected parts
can be anything, then use `*` without a number (matching any number of segments can only be used in
the last path segment).

```js
const Hapi = require('hapi');
const server = Hapi.server({ port: 80 });

const getPerson = function (request, h) {

    const nameParts = request.params.name.split('/');
    return { first: nameParts[0], last: nameParts[1] };
};

server.route({
    path: '/person/{name*2}',   // Matches '/person/john/doe'
    method: 'GET',
    handler: getPerson
});
```

#### Path matching order

The router iterates through the routing table on each incoming request and executes the first (and
only the first) matching route. Route matching is done based on the combination of the request path
and the HTTP verb (e.g. 'GET, 'POST'). The query is excluded from the routing logic. Requests are
matched in a deterministic order where the order in which routes are added does not matter.

Routes are matched based on the specificity of the route which is evaluated at each segment of the
incoming request path. Each request path is split into its segment (the parts separated by `'/'`).
The segments are compared to the routing table one at a time and are matched against the most
specific path until a match is found. If no match is found, the next match is tried.

When matching routes, string literals (no path parameter) have the highest priority, followed by
mixed parameters (`'/a{p}b'`), parameters (`'/{p}'`), and then wildcard (`/{p*}`).

Note that mixed parameters are slower to compare as they cannot be hashed and require an array
iteration over all the regular expressions representing the various mixed parameter at each
routing table node.

#### Catch all route

If the application needs to override the default Not Found (404) error response, it can add a
catch-all route for a specific method or all methods. Only one catch-all route can be defined.

```js
const Hapi = require('hapi');
const server = Hapi.server({ port: 80 });

const handler = function (request, h) {

    return h.response('The page was not found').code(404);
};

server.route({ method: '*', path: '/{p*}', handler });
```

### <a name="server.rules()" /> `server.rules(processor, [options])`

定义路由规则处理器，用于将路由规则对象转换为路由配置：

- `processor` - 一个函数签名 `function(rules, info)` 其中:
    - `rules` -
    - `info` - 具有以下属性的对象：
        - `method` - 路由方法.
        - `path` - 路由路径.
        - `vhost` - 路由虚拟 host (如果有定义).
    - 返回一个路由配置对象.

- `options` - 可选设置:
    - `validate` - rules object validation:
        - `schema` - **joi** schema.
        - `options` - optional **joi** validation options. Defaults to `{ allowUnknown: true }`.

请注意，根服务器和每个插件服务器实例只能注册一个规则处理器。如果在配置规则后添加路由，则不会包含规则配置。插件添加的路由将规则应用于从根到路由域的每个父域规则。
这意味着如果它们重叠【overlap】，插件定义的处理器会覆盖根处理器生成的配置。
如果重叠，路由 `config` 会覆盖规则配置。


### <a name="server.start()" /> `await server.start()`

Starts the server by listening for incoming requests on the configured port (unless the connection
was configured with [`autoListen`](#server.options.autoListen) set to `false`).

返回值: none.

Note that if the method fails and throws an error, the server is considered to be in an undefined
state and should be shut down. In most cases it would be impossible to fully recover as the various
plugins, caches, and other event listeners will get confused by repeated attempts to start the
server or make assumptions about the healthy state of the environment. It is recommended to abort
the process when the server fails to start properly. If you must try to resume after an error, call
[`server.stop()`](#server.stop()) first to reset the server state.

If a started server is started again, the second call to `server.start()` is ignored. No events
will be emitted and no extension points invoked.

```js
const Hapi = require('hapi');

async function example() {

    const server = Hapi.server({ port: 80 });
    await server.start();
    console.log('Server started at: ' + server.info.uri);
}
```

### <a name="server.state()" /> `server.state(name, [options])`

[HTTP state management](https://tools.ietf.org/html/rfc6265) uses client cookies to persist a state
across multiple requests. Registers a cookie definitions where:

- `name` - the cookie name string.

- `options` - are the optional cookie settings:

    - `ttl` - time-to-live in milliseconds. Defaults to `null` (session time-life - cookies are
      deleted when the browser is closed).

    - `isSecure` - sets the 'Secure' flag. Defaults to `true`.

    - `isHttpOnly` - sets the 'HttpOnly' flag. Defaults to `true`.

    - `isSameSite` - sets the ['SameSite' flag](https://www.owasp.org/index.php/SameSite).  The value must be one of:

        - `false` - no flag.
        - `'Strict'` - sets the value to `'Strict'` (this is the 默认值).
        - `'Lax'` - sets the value to `'Lax'`.

    - `path` - the path scope. Defaults to `null` (no path).

    - `domain` - the domain scope. Defaults to `null` (no domain).

    - `autoValue` - if present and the cookie was not received from the client or explicitly set by
      the route handler, the cookie is automatically added to the response with the provided value.
      The value can be a function with signature `async function(request)` where:

        - `request` - the [request object](#request).

    - `encoding` - encoding performs on the provided value before serialization. Options are:

        - `'none'` - no encoding. When used, the cookie value must be a string. This is the default
          value.
        - `'base64'` - string value is encoded using Base64.
        - `'base64json'` - object value is JSON-stringified then encoded using Base64.
        - `'form'` - object value is encoded using the _x-www-form-urlencoded_ method.
        - `'iron'` - Encrypts and sign the value using
          [**iron**](https://github.com/hueniverse/iron).

    - `sign` - an object used to calculate an HMAC for cookie integrity validation. This does not
      provide privacy, only a mean to verify that the cookie value was generated by the server.
      Redundant when `'iron'` encoding is used. Options are:

        - `integrity` - algorithm options. Defaults to
          [`require('iron').defaults.integrity`](https://github.com/hueniverse/iron#options).
        - `password` - password used for HMAC key generation (must be at least 32 characters long).

    - `password` - password used for `'iron'` encoding (must be at least 32 characters long).

    - `iron` - options for `'iron'` encoding. Defaults to
       [`require('iron').defaults`](https://github.com/hueniverse/iron#options).

    - `ignoreErrors` - if `true`, errors are ignored and treated as missing cookies.

    - `clearInvalid` - if `true`, automatically instruct the client to remove invalid
      cookies. Defaults to `false`.

    - `strictHeader` - if `false`, allows any cookie value including values in
      violation of [RFC 6265](https://tools.ietf.org/html/rfc6265). Defaults to `true`.

    - `passThrough` - used by proxy plugins (e.g. [**h2o2**](https://github.com/hapijs/h2o2)).

返回值: none.

State defaults can be modified via the [server.options.state](#server.options.state) configuration
option.

```js
const Hapi = require('hapi');
const server = Hapi.server({ port: 80 });

// Set cookie definition

server.state('session', {
    ttl: 24 * 60 * 60 * 1000,     // One day
    isSecure: true,
    path: '/',
    encoding: 'base64json'
});

// Set state in route handler

const handler = function (request, h) {

    let session = request.state.session;
    if (!session) {
        session = { user: 'joe' };
    }

    session.last = Date.now();

    return h.response('Success').state('session', session);
};
```

Registered cookies are automatically parsed when received. Parsing rules depends on the route
[`state.parse`](#route.options.state) configuration. If an incoming registered cookie fails parsing,
it is not included in [`request.state`](#request.state), regardless of the
[`state.failAction`](#route.options.state.failAction) setting. When [`state.failAction`](#route.options.state.failAction)
is set to `'log'` and an invalid cookie value is received, the server will emit a
[`'request'` event](#server.events.request). To capture these errors subscribe to the `'request'`
event on the `'internal'` channel and filter on `'error'` and `'state'` tags:

```js
const Hapi = require('hapi');
const server = Hapi.server({ port: 80 });

server.events.on({ name: 'request', channels: 'internal' }, (request, event, tags) => {

    if (tags.error && tags.state) {
        console.error(event);
    }
});
```

### <a name="server.states.add()" /> `server.states.add(name, [options])`

访问： 只读。

Same as calling [`server.state()`](#server.state()).

### <a name="server.states.format()" /> `await server.states.format(cookies)`

Formats an HTTP 'Set-Cookie' header based on the [`server.options.state`](#server.options.state)
where:

- `cookies` - a single object or an array of object where each contains:
    - `name` - the cookie name.
    - `value` - the cookie value.
    - `options` - cookie configuration to override the server settings.

返回值: a header string.

Note that this utility uses the server configuration but does not change the server state. It is
provided for manual cookie formating (e.g. when headers are set manually).

### <a name="server.states.parse()" /> `await server.states.parse(header)`

Parses an HTTP 'Cookies' header based on the [`server.options.state`](#server.options.state) where:

- `header` - the HTTP header.

返回值: an object where each key is a cookie name and value is the parsed cookie.

Note that this utility uses the server configuration but does not change the server state. It is
provided for manual cookie parsing (e.g. when server parsing is disabled).

### <a name="server.stop()" /> `await server.stop([options])`

Stops the server's listener by refusing to accept any new connections or requests (existing
connections will continue until closed or timeout), where:

- `options` - (可选) object with:

    - `timeout` - overrides the timeout in millisecond before forcefully terminating a connection.
      Defaults to `5000` (5 seconds).

返回值: none.

```js
const Hapi = require('hapi');

async function example() {

    const server = Hapi.server({ port: 80 });
    await server.start();
    await server.stop({ timeout: 60 * 1000 });
    console.log('Server stopped');
}
```

### <a name="server.table()" /> `server.table([host])`

Returns a copy of the routing table where:

- `host` - (可选) host to filter routes matching a specific virtual host. Defaults to all
  virtual hosts.

返回值: an array of routes where each route contains:
- `settings` - the route config with defaults applied.
- `method` - the HTTP method in lower case.
- `path` - the route path.

```js
const Hapi = require('hapi');
const server = Hapi.server({ port: 80 });
server.route({ method: 'GET', path: '/example', handler: () => 'ok' });

const table = server.table();
```

## 路由选项

每个路由可进行定制，以改变请求生命周期的默认行为。

### <a name="route.options.app" /> `route.options.app`

应用程序特定的路由配置状态。 不应该被 [plugins](#plugins) 使用，应该用 `options.plugins[name]` 替代。

### <a name="route.options.auth" /> `route.options.auth`

路由验证配置。 值可以是：

- 如果设置了默认的验证策略，则为 `false` 以关闭身份验证

- 字符串。使用 [`server.auth.strategy()`](#server.auth.strategy()) 注册的验证名称。该策略将被设置为 `'required'` 模式

- [authentication configuration object](#authentication-options).

#### <a name="route.options.auth.access" /> `route.options.auth.access`

默认值: none.

指定路由访问规则的对象或对象数组。 每个规则针对传入的请求判断，如果规则中至少一个相匹配则允许访问。每个规则至少包含一个 [`scope`](#route.options.auth.access.scope) 或 [`entity`](#route.options.auth.access.entity)。

#### <a name="route.options.auth.access.scope" /> `route.options.auth.access.scope`

默认值: `false` (没有范围要求【requirement】).

访问路由所需的应用程序范围。值可以是一个范围的字符串或者是一个范围字符串的的数组。当身份认证时，凭证对象 `scope` 属性必须包含至少一个已定义的用于访问路由的范围。

如果作用域字符串以 `+` 开头，则该作用域是必需的。如果作用域字符串以 `!` 开头，则禁止该作用域。例如，`['!a', '+b', 'c', 'd']` 表示 传入的请求凭证的 `scope` 必须不包含 'a', 必须包含 'b', 而且必须需要包含 'c' 或者 'd' 其中一个。

你还可以访问请求对象上的属性(`query`, `params`, `payload`, 和 `credentials`)，使用属性名包含 '{' 和 '}' 字符填充动态范围，例如 `'user-{params.id}'`。

#### <a name="route.options.auth.access.entity" /> `route.options.auth.access.entity`

默认值: `'any'`.

所需认证的实体【entity】类型. 如果设置，则必须匹配请求身份验证凭据的 `entity` 值。可选值：

- `'any'` - 身份验证可以代表【behalf】用户或应用程序。
- `'user'` - 身份验证必须代表用户，该用户通过身份验证策略返回的 `credentials` 对象中存在【presence】`'user'` 属性来识别。
- `'app'` - 身份验证必须代表一个应用程序，该应用程序由身份验证策略返回的 `credentials` 对象中缺少的 `user` 属性来识别。

#### <a name="route.options.auth.mode" /> `route.options.auth.mode`

默认值: `'required'`.

身份验证模式。 可用值：

- `'required'` - 身份验证是必需的。
- `'optional'` - 身份验证是可选的 - 请求必须包含有效凭据或根本不包含凭据。
- `'try'` - 类似于【similar】`'optional'`, 任何请求凭据都是尝试身份验证, 但如果凭证无效, 无论身份验证错误如何，请求都会继续。

#### <a name="route.options.auth.payload" /> `route.options.auth.payload`

默认值: `false`, 除非该方案需要有效 payload 认证。

如果设置，则在处理传入请求有效 payload 后对其进行身份验证。需要具有有效 payload 身份验证支持的策略 (例如 [Hawk](#https://github.com/hueniverse/hawk))。当方案将认证 `options.payload` 设置为 `true` 时，不能将其设置为 `'required'` 以外的值。

可用值：

- `false` - 没有 payload 身份认证.
- `'required'` - 需要有效的 payload 身份认证.
- `'optional'` - 仅在客户端包含有效 payload 认证信息时执行有效 payload 认证 （例如在 Hawk 中带有 `hash` 属性）。

#### <a name="route.options.auth.strategies" /> `route.options.auth.strategies`

默认值: 默认的策略，通过设置 [`server.auth.default()`](#server.auth.default()).

包含策略名称字符串的数组，它们会被按顺序尝试认证。不能与 [`strategy`](#route.options.auth.strategy) 一同使用

#### <a name="route.options.auth.strategy" /> `route.options.auth.strategy`

默认值: 默认的策略，通过设置 [`server.auth.default()`](#server.auth.default()).

策略名称 - 字符串。不能与 [`strategies`](#route.options.auth.strategies) 一同使用

### <a name="route.options.bind" /> `route.options.bind`

默认值: `null`.

一个对象在被调用时传递回提供的 `handler`（通过 `this` ）。 如果方法是箭头函数，则忽略。

### <a name="route.options.cache" /> `route.options.cache`

默认值: `{ privacy: 'default', statuses: [200], otherwise: 'no-cache' }`.

If the route method is 'GET', the route can be configured to include HTTP caching directives in the
response. Caching can be customized using an object with the following options:

- `privacy` - determines the privacy flag included in client-side caching using the 'Cache-Control'
  header. Values are:

    - `'default'` - no privacy flag.
    - `'public'` - mark the response as suitable for public caching.
    - `'private'` - mark the response as suitable only for private caching.

- `expiresIn` - relative expiration expressed in the number of milliseconds since the
  item was saved in the cache. Cannot be used together with `expiresAt`.

- `expiresAt` - time of day expressed in 24h notation using the 'HH:MM' format, at which
  point all cache records for the route expire. Cannot be used together with `expiresIn`.

- `statuses` - an array of HTTP response status code numbers (e.g. `200`) which are allowed to
  include a valid caching directive.

- `otherwise` - a string with the value of the 'Cache-Control' header when caching is disabled.

The default `Cache-Control: no-cache` header can be disabled by setting `cache` to `false`.

### <a name="route.options.compression" /> `route.options.compression`

一个对象，其中每个键是内容编码名称，每个值是具有所需【desired】编码器设置的对象。注意，解码器设置是在 [`compression`](#route.options.payload.compression) 中设置。

### <a name="route.options.cors" /> `route.options.cors`

默认值: `false` (无跨域头).

The [Cross-Origin Resource Sharing](https://www.w3.org/TR/cors/) protocol allows browsers to make
cross-origin API calls. CORS is required by web applications running inside a browser which are
loaded from a different domain than the API server. To enable, set `cors` to `true`, or to an
object with the following options:

- `origin` - an array of allowed origin servers strings ('Access-Control-Allow-Origin'). The array
  can contain any combination of fully qualified origins along with origin strings containing a
  wildcard `'*'` character, or a single `'*'` origin string. If set to `'ignore'`, any incoming
  Origin header is ignored (present or not) and the 'Access-Control-Allow-Origin' header is set to
  `'*'`. Defaults to any origin `['*']`.

- `maxAge` - number of seconds the browser should cache the CORS response
  ('Access-Control-Max-Age'). The greater the value, the longer it will take before the browser
  checks for changes in policy. Defaults to `86400` (one day).

- `headers` - a strings array of allowed headers ('Access-Control-Allow-Headers'). Defaults to
  `['Accept', 'Authorization', 'Content-Type', 'If-None-Match']`.

- `additionalHeaders` - a strings array of additional headers to `headers`. Use this to keep the
  default headers in place.

- `exposedHeaders` - a strings array of exposed headers ('Access-Control-Expose-Headers').
  Defaults to `['WWW-Authenticate', 'Server-Authorization']`.

- `additionalExposedHeaders` - a strings array of additional headers to `exposedHeaders`. Use this
  to keep the default headers in place.

- `credentials` - if `true`, allows user credentials to be sent
  ('Access-Control-Allow-Credentials'). Defaults to `false`.

### <a name="route.options.description" /> `route.options.description`

默认值: none.

用于生成文档的路由描述（字符串）。

使用 [`server.options.routes`](#server.options.routes) 设置服务器路由默认值时，此设置不可用。

### <a name="route.options.ext" /> `route.options.ext`

默认值: none.

Route-level [request extension points](#request-lifecycle) by setting the option to an object with
a key for each of the desired extension points (`'onRequest'` is not allowed), and the value is the
same as the [`server.ext(events)`](#server.ext()) `event` argument.

### <a name="route.options.files" /> `route.options.files`

默认值: `{ relativeTo: '.' }`.

Defines the behavior for accessing files:

- `relativeTo` - determines the folder relative paths are resolved against.

### <a name="route.options.handler" /> `route.options.handler`

默认值: none.

路由处理函数执行【performs】路由的主要业务逻辑并设置响应。
`handler` 可以被指定为:

- [lifecycle method](#lifecycle-methods).

- 一个具有单个属性的对象，使用 [`server.decorate()`](#server.decorate()) 方法注册的处理程序类型名称。匹配的属性值作为选项传递给已注册的处理程序生成器。

```js
const handler = function (request, h) {

    return 'success';
};
```

注意：使用箭头函数的处理程序不能绑定到任何 `bind` 属性。相反，绑定上下文在 [`h.context`](#h.context) 下可用。

### <a name="route.options.id" /> `route.options.id`

默认值: none.

用于使用 [`server.lookup()`](#server.lookup()) 查找路由的可选唯一标识符。
无法分配给添加了方法数组的路由。

### <a name="route.options.isInternal" /> `route.options.isInternal`

默认值: `false`.

如果为 `true`, 路由不能通过 HTTP 侦听器访问，而只能通过 [`server.inject()`](#server.inject()) 接口访问，并且 `allowInternals` 选项设置为 `true`。
用于外部世界无法访问的内部路由。

### <a name="route.options.json" /> `route.options.json`

默认值: none.

在将对象或错误响应转换为字符串有效内容或在字符串化后转义它时，可选参数传递给  `JSON.stringify()` 。支持以下内容：

- `replacer` - replacer 函数或数组。 默认为无操作。

- `space` - 缩进嵌套对象 key 的空格数。 默认为无缩进。

- `suffix` - 转换为JSON字符串后添加字符串后缀。 默认为无后缀。

- `escape` - 转换为 JSON 字符串后调用 [`Hoek.jsonEscape()`](https://github.com/hapijs/hoek/blob/master/API.md#escapejsonstring)。 默认为 `false`.

### <a name="route.options.jsonp" /> `route.options.jsonp`

默认值: none.

启用 JSONP 支持，通过将值设置为包含用于包装相应有效内容的函数名称的查询参数名称。

举个例子，如果值为 `'callback'`，请求过来带着 `'callback=me'`，那么 JSON 相应是 `'{ "a":"b" }'`，有效内容将为 `'me({ "a":"b" });'`。不能用于流相应。

'Content-Type' 响应头设置为 `'text/javascript'` 和 'X-Content-Type-Options' 相应头设置为 `'nosniff'`，并且即使由 [`response.type()`](#response.type()) 显式设置，也会覆盖这些头。

### <a name="route.options.log" /> `route.options.log`

默认值: `{ collect: false }`.

请求日志选项：

- `collect` - 如果为 `true`, 请求级别 日志 (内部和应用) 会通过 [`request.logs`](#request.logs) 收集.

### <a name="route.options.notes" /> `route.options.notes`

默认值: none.

用于生成文档的路由注释（字符串或字符串数组）。

使用 [`server.options.routes`](#server.options.routes) 设置服务器路由默认值时，此设置不可用。

### <a name="route.options.payload" /> `route.options.payload`

确定【Determines】如何处理请求有效内容。

#### <a name="route.options.payload.allow" /> `route.options.payload.allow`

默认值:允许解析以下 mime 类型：
- application/json
- application/*+json
- application/octet-stream
- application/x-www-form-urlencoded
- multipart/form-data
- text/*

A string or an array of strings with the allowed mime types for the endpoint. Use this settings to
limit the set of allowed mime types. Note that allowing additional mime types not listed above will
not enable them to be parsed, and if [`parse`](#route.options.payload.parse) is `true`, the request
will result in an error response.

#### <a name="route.options.payload.compression" /> `route.options.payload.compression`

默认值: none.

一个对象，其中每个键是内容编码名称，每个值是具有所需解码器设置的对象。请注意编码器在 [`compression`](#server.options.compression) 中设置。

#### <a name="route.options.payload.defaultContentType" /> `route.options.payload.defaultContentType`

默认值: `'application/json'`.

如果缺少 'Content-Type' 请求头，则为默认内容类型。

#### <a name="route.options.payload.failAction" /> `route.options.payload.failAction`

默认值: `'error'` (返回错误请求（400）错误响应)。

[`failAction` value](#lifecycle-failAction) 它确定如何处理有效负载解析错误。

#### <a name="route.options.payload.maxBytes" /> `route.options.payload.maxBytes`

默认值: `1048576` (1MB).

将传入有效负载的大小限制为指定的字节数。 允许非常大的有效负载可能导致服务器内存不足。

#### <a name="route.options.payload.multipart" /> `route.options.payload.multipart`

默认值: none.

Overrides payload processing for multipart requests. Value can be one of:

- `false` - disable multipart processing.

- an object with the following required options:

    - `output` - same as the [`output`](#route.options.payload.output) option with an additional
      value option:
        - `annotated` - wraps each multipart part in an object with the following keys:

            - `headers` - the part headers.
            - `filename` - the part file name.
            - `payload` - the processed part payload.

#### <a name="route.options.payload.output" /> `route.options.payload.output`

默认值: `'data'`.

The processed payload format. The value must be one of:

- `'data'` - the incoming payload is read fully into memory. If [`parse`](#route.options.payload.parse)
  is `true`, the payload is parsed (JSON, form-decoded, multipart) based on the 'Content-Type'
  header. If [`parse`](#route.options.payload.parse) is `false`, a raw `Buffer` is returned.

- `'stream'` - the incoming payload is made available via a `Stream.Readable` interface. If the
  payload is 'multipart/form-data' and [`parse`](#route.options.payload.parse) is `true`, field
  values are presented as text while files are provided as streams. File streams from a
  'multipart/form-data' upload will also have a `hapi` property containing the `filename` and
  `headers` properties. Note that payload streams for multipart payloads are a synthetic interface
  created on top of the entire mutlipart content loaded into memory. To avoid loading large
  multipart payloads into memory, set [`parse`](#route.options.payload.parse) to `false` and handle
  the multipart payload in the handler using a streaming parser (e.g. [**pez**](https://github.com/hapijs/pez)).

- `'file'` - the incoming payload is written to temporary file in the directory specified by the
  [`uploads`](#route.options.payload.uploads) settings. If the payload is 'multipart/form-data' and
  [`parse`](#route.options.payload.parse) is `true`, field values are presented as text while files
  are saved to disk. Note that it is the sole responsibility of the application to clean up the
  files generated by the framework. This can be done by keeping track of which files are used (e.g.
  using the `request.app` object), and listening to the server `'response'` event to perform
  cleanup.

#### <a name="route.options.payload.override" /> `route.options.payload.override`

默认值: none.

A mime type string overriding the 'Content-Type' header value received.

#### <a name="route.options.payload.parse" /> `route.options.payload.parse`

默认值: `true`.

Determines if the incoming payload is processed or presented raw. Available values:

- `true` - if the request 'Content-Type' matches the allowed mime types set by
  [`allow`](#route.options.payload.allow) (for the whole payload as well as parts), the payload is
  converted into an object when possible. If the format is unknown, a Bad Request (400) error
  response is sent. Any known content encoding is decoded.

- `false` - the raw payload is returned unmodified.

- `'gunzip'` - the raw payload is returned unmodified after any known content encoding is decoded.

#### <a name="route.options.payload.timeout" /> `route.options.payload.timeout`

默认值: to `10000` (10 seconds).

Payload reception timeout in milliseconds. Sets the maximum time allowed for the client to transmit
the request payload (body) before giving up and responding with a Request Timeout (408) error
response.

Set to `false` to disable.

#### <a name="route.options.payload.uploads" /> `route.options.payload.uploads`

默认值: `os.tmpdir()`.

The directory used for writing file uploads.

### <a name="route.options.plugins" /> `route.options.plugins`

默认值: `{}`.

Plugin-specific configuration. `plugins` is an object where each key is a plugin name and the value
is the plugin configuration.

### <a name="route.options.pre" /> `route.options.pre`

默认值: none.

The `pre` option allows defining methods for performing actions before the handler is called. These
methods allow breaking the handler logic into smaller, reusable components that can be shared
across routes, as well as provide a cleaner error handling of prerequisite operations (e.g. load
required reference data from a database).

`pre` is assigned an ordered array of methods which are called serially in order. If the `pre`
array contains another array of methods as one of its elements, those methods are called in
parallel. Note that during parallel execution, if any of the methods error, return a
[takeover response](#takeover-response), or abort signal, the other parallel methods will continue
to execute but will be ignored once completed.

`pre` can be assigned a mixed array of:

- an array containing the elements listed below, which are executed in parallel.

- an object with:
    - `method` - a [lifecycle method](#lifecycle-methods).
    - `assign` - key name used to assign the response of the method to in [`request.pre`](#request.pre)
      and [`request.preResponses`](#request.preResponses).
    - `failAction` - A [`failAction` value](#lifecycle-failAction) which determine what to do when
      a pre-handler method throws an error. If `assign` is specified and the `failAction` setting
      is not `'error'`, the error will be assigned.

- a method function - same as including an object with a single `method` key.

Note that pre-handler methods do not behave the same way other [lifecycle methods](#lifecycle-methods)
do when a value is returned. Instead of the 返回值 becoming the new response payload, the
value is used to assign the corresponding [`request.pre`](#request.pre) and
[`request.preResponses`](#request.preResponses) properties. Otherwise, the handling of errors,
[takeover response](#takeover-response) response, or abort signal behave the same as any other
[lifecycle methods](#lifecycle-methods).

```js
const Hapi = require('hapi');
const server = Hapi.server({ port: 80 });

const pre1 = function (request, h) {

    return 'Hello';
};

const pre2 = function (request, h) {

    return 'World';
};

const pre3 = function (request, h) {

    return request.pre.m1 + ' ' + request.pre.m2;
};

server.route({
    method: 'GET',
    path: '/',
    config: {
        pre: [
            [
                // m1 and m2 executed in parallel
                { method: pre1, assign: 'm1' },
                { method: pre2, assign: 'm2' }
            ],
            { method: pre3, assign: 'm3' },
        ],
        handler: function (request, h) {

            return request.pre.m3 + '!\n';
        }
    }
});
```

### <a name="route.options.response" /> `route.options.response`

Processing rules for the outgoing response.

#### <a name="route.options.response.emptyStatusCode" /> `route.options.response.emptyStatusCode`

 默认值: `200`.

The default HTTP status code when the payload is considered empty. Value can be `200` or `204`.
Note that a `200` status code is converted to a `204` only at the time of response transmission
(the response status code will remain `200` throughout the request lifecycle unless manually set).

#### <a name="route.options.response.failAction" /> `route.options.response.failAction`

默认值: `'error'` (return an Internal Server Error (500) error response).

A [`failAction` value](#lifecycle-failAction) which defines what to do when a response fails
payload validation.

#### <a name="route.options.response.modify" /> `route.options.response.modify`

默认值: `false`.

If `true`, applies the validation rule changes to the response payload.

#### <a name="route.options.response.options" /> `route.options.response.options`

默认值: none.

[**joi**](https://github.com/hapijs/joi) options object pass to the validation function. Useful to
set global options such as `stripUnknown` or `abortEarly` (the complete list is available
[here](https://github.com/hapijs/joi/blob/master/API.md#validatevalue-schema-options-callback)).
If a custom validation function is defined via [`schema`](#route.options.response.schema) or
[`status`](#route.options.response.status) then `options` can an arbitrary object that will be
passed to this function as the second argument.

#### <a name="route.options.response.ranges" /> `route.options.response.ranges`

默认值: `true`.

If `false`, payload [range](https://tools.ietf.org/html/rfc7233#section-3) support is disabled.

#### <a name="route.options.response.sample" /> `route.options.response.sample`

默认值: `100` (all responses).

The percent of response payloads validated (0 - 100). Set to `0` to disable all validation.

#### <a name="route.options.response.schema" /> `route.options.response.schema`

默认值: `true` (no validation).

The default response payload validation rules (for all non-error responses) expressed as one of:

- `true` - any payload allowed (no validation).

- `false` - no payload allowed.

- a [**joi**](https://github.com/hapijs/joi) validation object. The [`options`](#route.options.response.options)
  along with the request context (`{ headers, params, query, payload, app, auth }`) are passed to
  the validation function.

- a validation function using the signature `async function(value, options)` where:

    - `value` - the pending response payload.
    - `options` - The [`options`](#route.options.response.options) along with the request context
      (`{ headers, params, query, payload, app, auth }`).

    - if the function returns a value and [`modify`](#route.options.response.modify) is `true`,
      the value is used as the new response. If the original response is an error, the return
      value is used to override the original error `output.payload`. If an error is thrown, the
      error is processed according to [`failAction`](#route.options.response.failAction).

#### <a name="route.options.response.status" /> `route.options.response.status`

默认值: none.

Validation schemas for specific HTTP status codes. Responses (excluding errors) not matching the
listed status codes are validated using the default [`schema`](#route.options.response.schema).

`status` is set to an object where each key is a 3 digit HTTP status code and the value has the
same definition as [`schema`](#route.options.response.schema).

### <a name="route.options.rules" /> `route.options.rules`

默认值: none.

A custom rules object passed to each rules processor registered with [`server.rules()`](#server.rules()).

### <a name="route.options.security" /> `route.options.security`

默认值: `false` (security headers disabled).

Sets common security headers. To enable, set `security` to `true` or to an object with the
following options:

- `hsts` - controls the 'Strict-Transport-Security' header, where:

    - `true` - the header will be set to `max-age=15768000`. This is the 默认值.
    - a number - the maxAge parameter will be set to the provided value.

    - an object with the following fields:
        - `maxAge` - the max-age portion of the header, as a number. Default is `15768000`.
        - `includeSubDomains` - a boolean specifying whether to add the `includeSubDomains` flag to
          the header.
        - `preload` - a boolean specifying whether to add the `'preload'` flag (used to submit
          domains inclusion in Chrome's HTTP Strict Transport Security (HSTS) preload list) to the
          header.

- `xframe` - controls the 'X-Frame-Options' header, where:

    - `true` - the header will be set to `'DENY'`. This is the 默认值.
    - `'deny'` - the headers will be set to `'DENY'`.
    - `'sameorigin'` - the headers will be set to `'SAMEORIGIN'`.

    - an object for specifying the 'allow-from' rule, where:
        - `rule` - one of:
            - `'deny'`
            - `'sameorigin'`
            - `'allow-from'`
        - `source` - when `rule` is `'allow-from'` this is used to form the rest of the header,
          otherwise this field is ignored. If `rule` is `'allow-from'` but `source` is unset, the
          rule will be automatically changed to `'sameorigin'`.

- `xss` - boolean that controls the 'X-XSS-PROTECTION' header for Internet Explorer. Defaults to
  `true` which sets the header to equal `'1; mode=block'`.
    - Note: this setting can create a security vulnerability in versions of Internet Exploere below
      8, as well as unpatched versions of IE8. See [here](https://hackademix.net/2009/11/21/ies-xss-filter-creates-xss-vulnerabilities/)
      and [here](https://technet.microsoft.com/library/security/ms10-002) for more information. If
      you actively support old versions of IE, it may be wise to explicitly set this flag to
      `false`.

- `noOpen` - boolean controlling the 'X-Download-Options' header for Internet Explorer, preventing
  downloads from executing in your context. Defaults to `true` setting the header to `'noopen'`.

- `noSniff` - boolean controlling the 'X-Content-Type-Options' header. Defaults to `true` setting
  the header to its only and default option, `'nosniff'`.

- `referrer` - controls the ['Referrer-Policy'](https://www.w3.org/TR/referrer-policy/) header, which has the following possible values.
    - `false` - the 'Referrer-Policy' header will not be sent to clients with responses. This is the 默认值.
    - `''` - instructs clients that the Referrer-Policy will be [defined elsewhere](https://www.w3.org/TR/referrer-policy/#referrer-policy-empty-string), such as in a meta html tag.
    - `'no-referrer'` - instructs clients to never include the referrer header when making requests.
    - `'no-referrer-when-downgrade'` - instructs clients to never include the referrer when navigating from HTTPS to HTTP.
    - `'same-origin'` - instructs clients to only include the referrer on the current site origin.
    - `'origin'` - instructs clients to include the referrer but strip off path information so that the value is the current origin only.
    - `'strict-origin'` - same as `'origin'` but instructs clients to omit the referrer header when going from HTTPS to HTTP.
    - `'origin-when-cross-origin'` - instructs clients to include the full path in the referrer header for same-origin requests but only the origin components of the URL are included for cross origin requests.
    - `'strict-origin-when-cross-origin'` - same as `'origin-when-cross-origin'` but the client is instructed to omit the referrer when going from HTTPS to HTTP.
    - `'unsafe-url'` - instructs the client to always include the referrer with the full URL.

### <a name="route.options.state" /> `route.options.state`

默认值: `{ parse: true, failAction: 'error' }`.

HTTP state management (cookies) allows the server to store information on the client which is sent
back to the server with every request (as defined in [RFC 6265](https://tools.ietf.org/html/rfc6265)).
`state` supports the following options:

- `parse` - determines if incoming 'Cookie' headers are parsed and stored in the
  [`request.state`](#request.state) object.

- `failAction` - A [`failAction` value](#lifecycle-failAction) which determines how to handle
  cookie parsing errors. Defaults to `'error'` (return a Bad Request (400) error response).

### <a name="route.options.tags" /> `route.options.tags`

默认值: none.

Route tags used for generating documentation (array of strings).

This setting is not available when setting server route defaults using
[`server.options.routes`](#server.options.routes).

### <a name="route.options.timeout" /> `route.options.timeout`

默认值: `{ server: false }`.

Timeouts for processing durations.

#### <a name="route.options.timeout.server" /> `route.options.timeout.server`

默认值: `false`.

Response timeout in milliseconds. Sets the maximum time allowed for the server to respond to an
incoming request before giving up and responding with a Service Unavailable (503) error response.

#### <a name="route.options.timeout.socket" /> `route.options.timeout.socket`

默认值: none (use node default of 2 minutes).

By default, node sockets automatically timeout after 2 minutes. Use this option to override this
behavior. Set to `false` to disable socket timeouts.

### <a name="route.options.validate" /> `route.options.validate`

默认值: `{ headers: true, params: true, query: true, payload: true, failAction: 'error' }`.

Request input validation rules for various request components.

#### <a name="route.options.validate.errorFields" /> `route.options.validate.errorFields`

默认值: none.

An optional object with error fields copied into every validation error response.

#### <a name="route.options.validate.failAction" /> `route.options.validate.failAction`

默认值: `'error'` (return a Bad Request (400) error response).

A [`failAction` value](#lifecycle-failAction) which determines how to handle failed validations.
When set to a function, the `err` argument includes the type of validation error under
`err.output.payload.validation.source`.

#### <a name="route.options.validate.headers" /> `route.options.validate.headers`

默认值: `true` (no validation).

Validation rules for incoming request headers:

- `true` - any headers allowed (no validation performed).

- a [**joi**](https://github.com/hapijs/joi) validation object.

- a validation function using the signature `async function(value, options)` where:

    - `value` - the [`request.headers`](#request.headers) object containing the request headers.
    - `options` - [`options`](#route.options.validate.options).
    - if a value is returned, the value is used as the new [`request.headers`](#request.headers)
      value and the original value is stored in [`request.orig.headers`](#request.orig).
      Otherwise, the headers are left unchanged. If an error is thrown, the error is handled
      according to [`failAction`](#route.options.validate.failAction).

Note that all header field names must be in lowercase to match the headers normalized by node.

#### <a name="route.options.validate.options" /> `route.options.validate.options`

默认值: none.

An options object passed to the [**joi**](https://github.com/hapijs/joi) rules or the custom
validation methods. Used for setting global options such as `stripUnknown` or `abortEarly` (the
complete list is available [here](https://github.com/hapijs/joi/blob/master/API.md#validatevalue-schema-options-callback)).

If a custom validation function (see `headers`, `params`, `query`, or `payload` above) is defined
then `options` can an arbitrary object that will be passed to this function as the second
parameter.

The values of the other inputs (i.e. `headers`, `query`, `params`, `payload`, `app`, and `auth`)
are added to the `options` object under the validation `context` (accessible in rules as
`Joi.ref('$query.key')`).

Note that validation is performed in order (i.e. headers, params, query, and payload) and if type
casting is used (e.g. converting a string to a number), the value of inputs not yet validated will
reflect the raw, unvalidated and unmodified values.

If the validation rules for `headers`, `params`, `query`, and `payload` are defined at both the
server [`routes`](#server.options.routes) level and at the route level, the individual route
settings override the routes defaults (the rules are not merged).

#### <a name="route.options.validate.params" /> `route.options.validate.params`

默认值: `true` (no validation).

Validation rules for incoming request path parameters, after matching the path against the route,
extracting any parameters, and storing them in [`request.params`](#request.params), where:

- `true` - any path parameter value allowed (no validation performed).

- a [**joi**](https://github.com/hapijs/joi) validation object.

- a validation function using the signature `async function(value, options)` where:

    - `value` - the [`request.params`](#request.params) object containing the request path
      parameters.
    - `options` - [`options`](#route.options.validate.options).
    - if a value is returned, the value is used as the new [`request.params`](#request.params)
      value and the original value is stored in [`request.orig.params`](#request.orig). Otherwise,
      the path parameters are left unchanged. If an error is thrown, the error is handled according
      to [`failAction`](#route.options.validate.failAction).

Note that failing to match the validation rules to the route path parameters definition will cause
all requests to fail.

#### <a name="route.options.validate.payload" /> `route.options.validate.payload`

默认值: `true` (no validation).

Validation rules for incoming request payload (request body), where:

- `true` - any payload allowed (no validation performed).
- `false` - no payload allowed.

- a [**joi**](https://github.com/hapijs/joi) validation object.
    - Note that empty payloads are represented by a `null` value. If a validation schema is
      provided and empty payload are allowed, the schema must be explicitly defined by setting the
      rule to a **joi** schema with `null` allowed (e.g.
      `Joi.object({ /* keys here */ }).allow(null)`).

- a validation function using the signature `async function(value, options)` where:

    - `value` - the [`request.payload`](#request.payload) object containing the request payload.
    - `options` - [`options`](#route.options.validate.options).
    - if a value is returned, the value is used as the new [`request.payload`](#request.payload)
      value and the original value is stored in [`request.orig.payload`](#request.orig). Otherwise,
      the payload is left unchanged. If an error is thrown, the error is handled according to
      [`failAction`](#route.options.validate.failAction).

Note that validating large payloads and modifying them will cause memory duplication of the payload
(since the original is kept), as well as the significant performance cost of validating large
amounts of data.

#### <a name="route.options.validate.query" /> `route.options.validate.query`

默认值: `true` (no validation).

Validation rules for incoming request URI query component (the key-value part of the URI between
'?' and '#'). The query is parsed into its individual key-value pairs, decoded, and stored in
[`request.query`](#request.query) prior to validation. Where:

- `true` - any query parameter value allowed (no validation performed).
- `false` - no query parameter value allowed.

- a [**joi**](https://github.com/hapijs/joi) validation object.

- a validation function using the signature `async function(value, options)` where:

    - `value` - the [`request.query`](#request.query) object containing the request query
      parameters.
    - `options` - [`options`](#route.options.validate.options).
    - if a value is returned, the value is used as the new [`request.query`](#request.query) value
      and the original value is stored in [`request.orig.query`](#request.orig). Otherwise, the
      query parameters are left unchanged. If an error is thrown, the error is handled according to
      [`failAction`](#route.options.validate.failAction).

Note that changes to the query parameters will not be reflected in [`request.url`](#request.url).

## Request lifecycle

Each incoming request passes through the request lifecycle. The specific steps vary based on the
server and route configurations, but the order in which the applicable steps are executed is always
the same. The following is the complete list of steps a request can go through:

- _**onRequest**_
    - always called when `onRequest` extensions exist.
    - the request path and method can be modified via the [`request.setUrl()`](#request.setUrl())
      and [`request.setMethod()`](#request.setMethod()) methods. Changes to the request path or
      method will impact how the request is routed and can be used for rewrite rules.
    - [`request.route`](#request.route) is unassigned.
    - JSONP configuration is ignored for any response returned from the extension point since no
      route is matched yet and the JSONP configuration is unavailable.

- _**Route lookup**_
    - lookup based on `request.path` and `request.method`.
    - skips to _**onPreResponse**_ if no route is found or if the path violates the HTTP
      specification.

- _**JSONP processing**_
    - based on the route [`jsonp`](#route.options.jsonp) option.
    - parses JSONP parameter from [`request.query`](#request.query).
    - skips to _**Response validation**_ on error.

- _**Cookies processing**_
    - based on the route [`state`](#route.options.state) option.
    - error handling based on [`failAction`](#route.options.state.failAction).

- _**onPreAuth**_
    - called regardless if authentication is performed.

- _**Authentication**_
    - based on the route [`auth`](#route.options.auth) option.

- _**Payload processing**_
    - based on the route [`state`](#route.options.payload) option.
    - error handling based on [`failAction`](#route.options.payload.failAction).

- _**Payload authentication**_
    - based on the route [`auth`](#route.options.auth) option.

- _**onCredentials**_
    - called only if authentication is performed.

- _**Authorization**_
    - based on the route authentication [`access`](#route.options.auth.access) option.

- _**onPostAuth**_
    - called regardless if authentication is performed.

- _**Headers validation**_
    - based on the route [`validate.headers`](#route.options.validate.headers) option.
    - error handling based on [`failAction`](#route.options.validate.failAction).

- _**Path parameters validation**_
    - based on the route [`validate.params`](#route.options.validate.params) option.
    - error handling based on [`failAction`](#route.options.validate.failAction).

- _**JSONP cleanup**_
    - based on the route [`jsonp`](#route.options.jsonp) option.
    - remove the JSONP parameter from [`request.query`](#request.query).

- _**Query validation**_
    - based on the route [`validate.query`](#route.options.validate.query) option.
    - error handling based on [`failAction`](#route.options.validate.failAction).

- _**Payload validation**_
    - based on the route [`validate.payload`](#route.options.validate.payload) option.
    - error handling based on [`failAction`](#route.options.validate.failAction).

- _**onPreHandler**_

- _**Pre-handler methods**_
    - based on the route [`pre`](#route.options.pre) option.
    - error handling based on each pre-handler method's `failAction` setting.

- _**Route handler**_
    - executes the route [`handler`](#route.options.handler).

- _**onPostHandler**_
    - the response contained in [`request.response`](#request.response) may be modified (but not
      assigned a new value). To return a different response type (for example, replace an error
      with an HTML response), return a new response value.

- _**Response validation**_
    - error handling based on [`failAction`](#route.options.response.failAction).

- _**onPreResponse**_
    - always called, unless the request is aborted.
    - the response contained in [`request.response`](#request.response) may be modified (but not
      assigned a new value). To return a different response type (for example, replace an error
      with an HTML response), return a new response value. Note that any errors generated will not
      be passed back to _**onPreResponse**_ to prevent an infinite loop.

- _**Response transmission**_
    - may emit a [`'request'` event](#server.events.request) on the `'error'` channel.

- _**Finalize request**_
    - emits `'response'` event.

### Lifecycle methods

Lifecycle methods are the interface between the framework and the application. Many of the request
lifecycle steps: [extensions](#server.ext()), [authentication](#authentication-scheme),
[handlers](#route.options.handler), [pre-handler methods](#route.options.pre), and
[`failAction` function values](#lifecycle-failAction) are lifecyle methods provided by the
developer and executed by the framework.

Each lifecycle method is a function with the signature `await function(request, h, [err])` where:
- `request` - the [request object](#request).
- `h` - the [response toolkit](#response-toolkit) the handler must call to set a response and
  return control back to the framework.
- `err` - an error object available only when the method is used as a
  [`failAction` value](#lifecycle-failAction).

Each lifecycle method must return a value or a promise that resolves into a value. If a lifecycle
method returns without a value or resolves to an `undefined` value, an Internal Server Error (500)
error response is sent.

The 返回值 must be one of:
- Plain value:
    - `null`
    - string
    - number
    - boolean
- `Buffer` object
- `Error` object
    - plain `Error`.
    - a [`Boom`](https://github.com/hapijs/boom) object.
- `Stream` object
    - must be compatible with the "streams2" API and not be in `objectMode`.
    - if the stream object has a `statusCode` property, that status code will be used as
      the default response code based on the [`passThrough`](#response.settings.passThrough)
      option.
    - if the stream object has a `headers` property, the headers will be included in the response
      based on the [`passThrough`](#response.settings.passThrough) option.
    - if the stream object has a function property `setCompressor(compressor)` and the response
      passes through a compressor, a reference to the compressor stream will be passed to the
      response stream via this method.
- any object or array
    - must not include circular references.
- a toolkit signal:
    - [`h.abandon`](#h.abandon) - abort processing the request.
    - [`h.close`](#h.close) - abort processing the request and call `end()` to ensure the response
      is closed.
    - [`h.continue`](#h.continue) - continue processing the request lifecycle without changing the
      response.
- a toolkit method response:
    - [`h.response()`](#h.response()) - wraps a plain response in a [response object](#response-object).
    - [`h.redirect()`](#h.redirect()) - wraps a plain response with a redirection directive.
    - [`h.authenticated()`](#h.authenticated()) - indicate request authenticated successfully
      (auth scheme only).
    - [`h.unauthenticated()`](#h.unauthenticated()) - indicate request failed to authenticate
      (auth scheme only).
- a promise object that resolve to any of the above values

Any error thrown by a lifecycle method will be used as the reponse object. While errors and valid
values can be returned, it is recommended to throw errors. Throwing non-error values will generate
a Bad Implementation (500) error response.

```js
const handler = function (request, h) {

    if (request.query.forbidden) {
        throw Boom.badRequest();
    }

    return 'success';
};
```

If the route has a [`bind`](#route.options.bind) option or [`server.bind()`](#server.bind()) was
called, the lifecycle method will be bound to the provided context via `this` as well as accessible
via [`h.context`](#h.context).

#### Lifecycle workflow

The flow between each lifecyle step depends on the value returned by each lifecycle method as
follows:

- an error:
    - the lifecycle skips to the **_Response validation**_ step.
    - if returned by the _**onRequest**_ step it skips to the _**onPreResponse**_ step.
    - if returned by the _**Response validation**_ step it skips to the _**onPreResponse**_ step.
    - if returned by the _**onPreResponse**_ step it skips to the _**Response transmission**_ step.

- an abort signal ([`h.abandon`](#h.abandon) or [`h.close`](#h.close)):
    - skips to the _**Finalize request**_ step.

- a [`h.continue`](#h.continue) signal:
    - continues processing the request lifecycle without changing the request response.
    - cannot be used by the [`authenticate()`](#authentication-scheme) scheme method.

- a [takeover response](#takeover-response):
    - overrides the request response with the provided value and skips to the
      _**Response validation**_ step.
    - if returned by the _**Response validation**_ step it skips to the _**onPreResponse**_ step.
    - if returned by the _**onPreResponse**_ step it skips to the _**Response transmission**_ step.

- any other response:
    - overrides the request response with the provided value and continues processing the request
      lifecycle.
    - cannot be returned from any step prior to the _**Pre-handler methods**_ step.

The [`authenticate()`](#authentication-scheme) method has access to two additional 返回值s:
    - [`h.authenticated()`](#h.authenticated()) - indicate request authenticated successfully.
    - [`h.unauthenticated()`](#h.unauthenticated()) - indicate request failed to authenticate.

Note that these rules apply somewhat differently when used in a [pre-handler method](#route.options.pre).

#### Takeover response

A takeover response is a [`response object`](#response-object) on which [`response.takeover()`](#response.takever())
was called to signal that the [lifecycle method](#lifecycle-methods) 返回值 should be set as
the response and skip to immediately validate and trasmit the value, bypassing other lifecycle
steps.

#### <a name="lifecycle-failAction" /> `failAction` configuration

Various configuration options allows defining how errors are handled. For example, when invalid
payload is received or malformed cookie, instead of returning an error, the framework can be
configured to perform another action. When supported the `failAction` option supports the following
values:

- `'error'` - return the error object as the response.
- `'log'` - report the error but continue processing the request.
- `'ignore'` - take no action and continue processing the request.

- a [lifecycle method](#lifecycle-methods) with the signature `async function(request, h, err)`
  where:
    - `request` - the [request object](#request).
    - `h` - the [response toolkit](#response-toolkit).
    - `err` - the error object.

#### Errors

**hapi** uses the [**boom**](https://github.com/hapijs/boom) error library for all its internal
error generation. **boom** provides an expressive interface to return HTTP errors. Any error
thrown by a [lifecycle method](#lifecycle-methods) is converted into a **boom** object and defaults to status
code `500` if the error is not already a **boom** object.

When the error is sent back to the client, the response contains a JSON object with the
`statusCode`, `error`, and `message` keys.

```js
const Hapi = require('hapi');
const Boom = require('boom');

const server = Hapi.server();

server.route({
    method: 'GET',
    path: '/badRequest',
    handler: function (request, h) {

        throw Boom.badRequest('Unsupported parameter');     // 400
    }
});

server.route({
    method: 'GET',
    path: '/internal',
    handler: function (request, h) {

        throw new Error('unexpect error');                  // 500
    }
});
```

##### Error transformation

Errors can be customized by changing their `output` content. The **boom** error object includes the
following properties:

- `isBoom` - if `true`, indicates this is a `Boom` object instance.

- `message` - the error message.

- `output` - the formatted response. Can be directly manipulated after object construction to
  return a custom error response. Allowed root keys:

    - `statusCode` - the HTTP status code (typically 4xx or 5xx).

    - `headers` - an object containing any HTTP headers where each key is a header name and value
      is the header content.

    - `payload` - the formatted object used as the response payload (stringified). Can be directly
      manipulated but any changes will be lost
      if `reformat()` is called. Any content allowed and by default includes the following content:

        - `statusCode` - the HTTP status code, derived from `error.output.statusCode`.

        - `error` - the HTTP status message (e.g. 'Bad Request', 'Internal Server Error') derived
          from `statusCode`.

        - `message` - the error message derived from `error.message`.

- inherited `Error` properties.

It also supports the following method:

- `reformat()` - rebuilds `error.output` using the other object properties.

```js
const Boom = require('boom');

const handler = function (request, h) {

    const error = Boom.badRequest('Cannot feed after midnight');
    error.output.statusCode = 499;    // Assign a custom error code
    error.reformat();
    error.output.payload.custom = 'abc_123'; // Add custom key
    throw error;
});
```

When a different error representation is desired, such as an HTML page or a different payload
format, the `'onPreResponse'` extension point may be used to identify errors and replace them with
a different response object, as in this example using [Vision's](https://github.com/hapijs/vision)
`.view()` [response toolkit](#response-toolkit) property.

```js
const Hapi = require('hapi');
const Vision = require('vision');

const server = Hapi.server({ port: 80 });
server.register(Vision, (err) => {
    server.views({
        engines: {
            html: require('handlebars')
        }
    });
});

const preResponse = function (request, h) {

    const response = request.response;
    if (!response.isBoom) {
        return h.continue;
    }

    // Replace error with friendly HTML

      const error = response;
      const ctx = {
          message: (error.output.statusCode === 404 ? 'page not found' : 'something went wrong')
      };

      return h.view('error', ctx).code(error.output.statusCode);
};

server.ext('onPreResponse', preResponse);
```

### Response Toolkit

访问： 只读。

The response toolkit is a collection of properties and utilities passed to every
[lifecycle method](#lifecycle-methods). It is somewhat hard to define as it provides both
utilities for manipulating responses as well as other information. Since the toolkit is passed
as a function argument, developers can name it whatever they want. For the purpose of this document
the `h` notation is used. It is named in the spirit of the RethinkDB `r` method, with `h` for
**h**api.

#### Toolkit properties

##### <a name="h.abandon" /> `h.abandon`

访问： 只读。

A response symbol. When returned by a lifecycle method, the request lifecycle skips to the
finalizing step without further interaction with the node response stream. It is the developer's
responsibility to write and end the response directly via [`request.raw.res`](#request.raw).

##### <a name="h.close" /> `h.close`

访问： 只读。

A response symbol. When returned by a lifecycle method, the request lifecycle skips to the
finalizing step after calling `request.raw.res.end())` to close the the node response stream.

##### <a name="h.context" /> `h.context`

访问： read / write (will impact the shared context if the object is modified).

A response symbol. Provides access to the route or server context set via the route
[`bind`](#route.options.bind) option or [`server.bind()`](#server.bind()).

##### <a name="h.continue" /> `h.continue`

访问： 只读。

A response symbol. When returned by a lifecycle method, the request lifecycle continues without
changing the response.

##### <a name="h.realm" /> `h.realm`

访问： 只读。

The [server realm](#server.realm) associated with the matching route. Defaults to the root server
realm in the _**onRequest**_ step.

##### <a name="h.request" /> `h.request`

访问： read only and public request interface.

The [request] object. This is a duplication of the `request` lifecycle method argument used by
[toolkit decorations](#server.decorate()) to access the current request.

#### <a name="h.authenticated()" /> `h.authenticated(data)`

Used by the [authentication] method to pass back valid credentials where:

- `data` - an object with:

    - `credentials` - (required) object representing the authenticated entity.
    - `artifacts` - (可选) authentication artifacts object specific to the authentication
      scheme.

返回值: an internal authentication object.

#### <a name="h.entity()" /> `h.entity(options)`

Sets the response 'ETag' and 'Last-Modified' headers and checks for any conditional request headers
to decide if the response is going to qualify for an HTTP 304 (Not Modified). If the entity values
match the request conditions, `h.entity()` returns a response object for the lifecycle method to
return as its value which will set a 304 response. Otherwise, it sets the provided entity headers
and returns `undefined`. The method argumetns are:

- `options` - a required configuration object with:
    - `etag` - the ETag string. Required if `modified` is not present. Defaults to no header.
    - `modified` - the Last-Modified header value. Required if `etag` is not present. Defaults to
      no header.
    - `vary` - same as the [`response.etag()`](#response.etag()) option. Defaults to `true`.

返回值:
    - a [response object](#response-object) if the response is unmodified.
    - `undefined` if the response has changed.

If `undefined` is returned, the developer must return a valid lifecycle method value. If a response
is returned, it should be used as the 返回值 (but may be customize using the response
methods).

```js
const Hapi = require('hapi');
const server = Hapi.server({ port: 80 });

server.route({
    method: 'GET',
    path: '/',
    config: {
        cache: { expiresIn: 5000 },
        handler: function (request, h) {

            const response = h.entity({ etag: 'abc' });
            if (response) {
                response.header('X', 'y');
                return response;
            }

            return 'ok';
        }
    }
});
```

#### <a name="h.redirect()" /> `h.redirect(uri)`

Redirects the client to the specified uri. Same as calling `h.response().redirect(uri)`.

Returns a [response object](#response-object).

```js
const handler = function (request, h) {

    return h.redirect('http://example.com');
};
```

#### <a name="h.response()" /> `h.response([value])`

Wraps the provided value and returns a [`response`](#response-object) object which allows
customizing the response (e.g. setting the HTTP status code, custom headers, etc.), where:

- `value` - (可选) 返回值. Defaults to `null`.

Returns a [response object](#response-object).

```js
// Detailed notation

const handler = function (request, h) {

    const response = h.response('success');
    response.type('text/plain');
    response.header('X-Custom', 'some-value');
    return response;
};

// Chained notation

const handler = function (request, h) {

    return h.response('success')
        .type('text/plain')
        .header('X-Custom', 'some-value');
};
```

#### <a name="h.state()" /> `h.state(name, value, [options])`

Sets a response cookie using the same arguments as [`response.state()`](#response.state()).

返回值: none.

```js
const ext = function (request, h) {

    h.state('cookie-name', 'value');
    return h.continue;
};
```

#### <a name="h.unauthenticated()" /> `h.unauthenticated(error, [data])`

Used by the [authentication] method to indicate authentication failed and pass back the credentials
received where:
- `error` - (required) the authentication error.
- `data` - (可选) an object with:
    - `credentials` - (required) object representing the authenticated entity.
    - `artifacts` - (可选) authentication artifacts object specific to the authentication
      scheme.

The method is used to pass both the authentication error and the credentials. For example, if a
request included expired credentials, it allows the method to pass back the user information
(combined with a `'try'` authentication [`mode`](#route.options.auth.mode)) for error customization.

There is no difference between throwing the error or passing it with the `h.unauthenticated()`
method if no credentials are passed, but it might still be helpful for code clarity.

#### <a name="h.unstate()" /> `h.unstate(name, [options])`

Clears a response cookie using the same arguments as [`response.unstate()`](#response.unstate()).

```js
const ext = function (request, h) {

    h.unstate('cookie-name');
    return h.continue;
};
```

### Response object

The response object contains the request response value along with various HTTP headers and flags.
When a [lifecycle method](#lifecycle-methods) returns a value, the value is wrapped in a response
object along with some default flags (e.g. `200` status code). In order to customize a response
before it is returned, the [`h.response()`](#h.response()) method is provided.

#### Response properties

##### <a name="response.app" /> `response.app`

访问： read / write.

默认值: `{}`.

Application-specific state. Provides a safe place to store application data without potential
conflicts with the framework. Should not be used by [plugins](#plugins) which should use
[`plugins[name]`](#response.plugins).

##### <a name="response.events" /> `response.events`

访问： read only and the public **podium** interface.

The `response.events` object supports the following events:

- `'peek'` - emitted for each chunk of data written back to the client connection. The event method
  signature is `function(chunk, encoding)`.

- `'finish'` - emitted when the response finished writing but before the client response connection
  is ended. The event method signature is `function ()`.

```js
const Crypto = require('crypto');
const Hapi = require('hapi');
const server = Hapi.server({ port: 80 });

const preResponse = function (request, h) {

    const response = request.response;
    if (response.isBoom) {
        return null;
    }

    const hash = Crypto.createHash('sha1');
    response.events.on('peek', (chunk) => {

        hash.update(chunk);
    });

    response.events.once('finish', () => {

        console.log(hash.digest('hex'));
    });

    return h.continue;
};

server.ext('onPreResponse', preResponse);
```

##### <a name="response.headers" /> `response.headers`

访问： 只读。

默认值: `{}`.

An object containing the response headers where each key is a header field name and the value is
the string header value or array of string.

Note that this is an incomplete list of headers to be included with the response. Additional
headers will be added once the response is prepared for transmission.

##### <a name="response.plugins" /> `response.plugins`

访问： read / write.

默认值: `{}`.

Plugin-specific state. Provides a place to store and pass request-level plugin data. `plugins` is
an object where each key is a plugin name and the value is the state.

##### <a name="response.settings" /> `response.settings`

访问： 只读。

Object containing the response handling flags.

###### <a name="response.settings.passThrough" /> `response.settings.passThrough`

访问： 只读。

Defaults value: `true`.

If `true` and [`source`](#response.source) is a `Stream`, copies the `statusCode` and `headers`
properties of the stream object to the outbound response.

###### <a name="response.settings.stringify" /> `response.settings.stringify`

访问： 只读。

默认值: `null` (use route defaults).

Override the route [`json`](#route.options.json) options used when [`source`](#response.source)
value requires stringification.

###### <a name="response.settings.ttl" /> `response.settings.ttl`

访问： 只读。

默认值: `null` (use route defaults).

If set, overrides the route [`cache`](#route.options.cache) with an expiration value in
milliseconds.

###### <a name="response.settings.varyEtag" /> `response.settings.varyEtag`

默认值: `false`.

If `true`, a suffix will be automatically added to the 'ETag' header at transmission time
(separated by a `'-'` character) when the HTTP 'Vary' header is present.

##### <a name="response.source" /> `response.source`

访问： 只读。

The raw value returned by the [lifecycle method](#lifecycle-methods).

##### <a name="response.statusCode" /> `response.statusCode`

访问： 只读。

默认值: `200`.

The HTTP response status code.

##### <a name="response.variety" /> `response.variety`

访问： 只读。

A string indicating the type of [`source`](#response.source) with available values:

- `'plain'` - a plain response such as string, number, `null`, or simple object.
- `'buffer'` - a `Buffer`.
- `'stream'` - a `Stream`.

#### <a name="response.bytes()" /> `response.bytes(length)`

Sets the HTTP 'Content-Length' header (to avoid chunked transfer encoding) where:

- `length` - the header value. Must match the actual payload size.

返回值: the current response object.

#### <a name="response.charset()" /> `response.charset(charset)`

Sets the 'Content-Type' HTTP header 'charset' property where:

- `charset` - the charset property value.

返回值: the current response object.

#### <a name="response.code()" /> `response.code(statusCode)`

Sets the HTTP status code where:

- `statusCode` - the HTTP status code (e.g. 200).

返回值: the current response object.

#### <a name="response.message()" /> `response.message(httpMessage)`

Sets the HTTP status message where:

- `httpMessage` - the HTTP status message (e.g. 'Ok' for status code 200).

返回值: the current response object.

#### <a name="response.created()" /> `response.created(uri)`

Sets the HTTP status code to Created (201) and the HTTP 'Location' header where:

- `uri` - an absolute or relative URI used as the 'Location' header value.

返回值: the current response object.

#### <a name="response.encoding()" /> `response.encoding(encoding)`

Sets the string encoding scheme used to serial data into the HTTP payload where:
- `encoding` - the encoding property value (see [node Buffer encoding](https://nodejs.org/api/buffer.html#buffer_buffers_and_character_encodings)).

返回值: the current response object.

#### <a name="response.etag()" /> `response.etag(tag, options)`

Sets the representation [entity tag](https://tools.ietf.org/html/rfc7232#section-2.3) where:

- `tag` - the entity tag string without the double-quote.

- `options` - (可选) settings where:

    - `weak` - if `true`, the tag will be prefixed with the `'W/'` weak signifier. Weak tags will
      fail to match identical tags for the purpose of determining 304 response status. Defaults to
      `false`.

    - `vary` - if `true` and content encoding is set or applied to the response (e.g 'gzip' or
      'deflate'), the encoding name will be automatically added to the tag at transmission time
      (separated by a `'-'` character). Ignored when `weak` is `true`. Defaults to `true`.

返回值: the current response object.

#### <a name="response.header()" /> `response.header(name, value, options)`

Sets an HTTP header where:

- `name` - the header name.

- `value` - the header value.

- `options` - (可选) object where:

    - `append` - if `true`, the value is appended to any existing header value using `separator`.
      Defaults to `false`.

    - `separator` - string used as separator when appending to an existing value. Defaults to `','`.

    - `override` - if `false`, the header value is not set if an existing value present. Defaults
      to `true`.

    - `duplicate` - if `false`, the header value is not modified if the provided value is already
      included. Does not apply when `append` is `false` or if the `name` is `'set-cookie'`.
      Defaults to `true`.

返回值: the current response object.

#### <a name="response.location()" /> `response.location(uri)`

Sets the HTTP 'Location' header where:

- `uri` - an absolute or relative URI used as the 'Location' header value.

返回值: the current response object.

#### <a name="response.redirect()" /> `response.redirect(uri)`

Sets an HTTP redirection response (302) and decorates the response with additional methods, where:

- `uri` - an absolute or relative URI used to redirect the client to another resource.

返回值: the current response object.

Decorates the response object with the [`response.temporary()`](#response.temporary()),
[`response.permanent()`](#response.permanent()), and [`response.rewritable()`](#response.rewritable())
methods to easily change the default redirection code (302).

|                |  Permanent | Temporary |
| -------------- | ---------- | --------- |
| Rewritable     | 301        | 302       |
| Non-rewritable | 308        | 307       |

#### <a name="response.replacer()" /> `response.replacer(method)`

Sets the `JSON.stringify()` `replacer` argument where:

- `method` - the replacer function or array. Defaults to none.

返回值: the current response object.

#### <a name="response.spaces()" /> `response.spaces(count)`

Sets the `JSON.stringify()` `space` argument where:

- `count` - the number of spaces to indent nested object keys. Defaults to no indentation.

返回值: the current response object.

#### <a name="response.state()" /> `response.state(name, value, [options])`

Sets an HTTP cookie where:

- `name` - the cookie name.

- `value` - the cookie value. If no `options.encoding` is defined, must be a string. See
  [`server.state()`](#server.state()) for supported `encoding` values.

- `options` - (可选) configuration. If the state was previously registered with the server
  using [`server.state()`](#server.state()), the specified keys in `options` are merged with the
  default server definition.

返回值: the current response object.

#### <a name="response.suffix()" /> `response.suffix(suffix)`

Sets a string suffix when the response is process via `JSON.stringify()` where:

- `suffix` - the string suffix.

返回值: the current response object.

#### <a name="response.ttl()" /> `response.ttl(msec)`

Overrides the default route cache expiration rule for this response instance where:

- `msec` - the time-to-live value in milliseconds.

返回值: the current response object.

#### <a name="response.type()" /> `response.type(mimeType)`

Sets the HTTP 'Content-Type' header where:

- `value` - is the mime type.

返回值: the current response object.

Should only be used to override the built-in default for each response type.

#### <a name="response.unstate()" /> `response.unstate(name, [options])`

Clears the HTTP cookie by setting an expired value where:
- `name` - the cookie name.
- `options` - (可选) configuration for expiring cookie. If the state was previously registered
  with the server using [`server.state()`](#serverstatename-options), the specified `options` are
  merged with the server definition.

返回值: the current response object.

#### <a name="response.vary()" /> `response.vary(header)`

Adds the provided header to the list of inputs affected the response generation via the HTTP 'Vary'
header where:

- `header` - the HTTP request header name.

返回值: the current response object.

#### <a name="response.takeover()" /> `response.takeover()`

Marks the response object as a [takeover response](#takeover-response).

返回值: the current response object.

#### <a name="response.temporary()" /> `response.temporary(isTemporary)`

Sets the status code to `302` or `307` (based on the [`response.rewritable()`](#response.rewriteable())
setting) where:

- `isTemporary` - if `false`, sets status to permanent. Defaults to `true`.

返回值: the current response object.

Only available after calling the [`response.redirect()`](#response.redirect()) method.

#### <a name="response.permanent()" /> `response.permanent(isPermanent)`

Sets the status code to `301` or `308` (based on the [`response.rewritable()`](#response.rewritable())
setting) where:

- `isPermanent` - if `false`, sets status to temporary. Defaults to `true`.

返回值: the current response object.

Only available after calling the [`response.redirect()`](#response.redirect()) method.

#### <a name="response.rewritable()" /> `response.rewritable(isRewritable)`

Sets the status code to `301`/`302` for rewritable (allows changing the request method from 'POST'
to 'GET') or `307`/`308` for non-rewritable (does not allow changing the request method from 'POST'
to 'GET'). Exact code based on the [`response.temporary()`](#response.temporary()) or
[`response.permanent()`](#response.permanent()) setting. Arguments:

- `isRewritable` - if `false`, sets to non-rewritable. Defaults to `true`.

返回值: the current response object.

Only available after calling the [`response.redirect()`](#response.redirect()) method.

## 请求

在内部为每个传入请求创建请求对象。它与从节点HTTP服务器回调接收的对象不同 (可以通过 [`request.raw.req`](#request.raw))。请求属性在 [request lifecycle](#request-lifecycle) 中发生改变。

### 请求属性

#### <a name="request.app" /> `request.app`

访问： read / write.

Application-specific state. Provides a safe place to store application data without potential
conflicts with the framework. Should not be used by [plugins](#plugins) which should use
`plugins[name]`.

#### <a name="request.auth" /> `request.auth`

访问： 只读。

认证信息:

- `artifacts` - an artifact object received from the authentication strategy and used in
  authentication-related actions.

- `credentials` - the `credential` object received during the authentication process. The
  presence of an object does not mean successful authentication.

- `error` - 验证错误失败，模式设置为 `'try'`。

- `isAuthenticated` - `true` if the request has been successfully authenticated, otherwise `false`.

- `isAuthorized` - `true` is the request has been successfully authorized against the route
  authentication [`access`](#route.options.auth.access) configuration. If the route has not
  access rules defined or if the request failed authorization, set to `false`.

- `mode` - 路由认证模式。

- `strategy` - 所用策略的名称。

#### <a name="request.events" /> `request.events`

访问： read only and the public **podium** interface.

The `request.events` supports the following events:

- `'peek'` - emitted for each chunk of payload data read from the client connection. The event
  method signature is `function(chunk, encoding)`.

- `'finish'` - emitted when the request payload finished reading. The event method signature is
  `function ()`.

- `'disconnect'` - emitted when a request errors or aborts unexpectedly.

```js
const Crypto = require('crypto');
const Hapi = require('hapi');
const server = Hapi.server({ port: 80 });

const onRequest = function (request, h) {

    const hash = Crypto.createHash('sha1');
    request.events.on('peek', (chunk) => {

        hash.update(chunk);
    });

    request.events.once('finish', () => {

        console.log(hash.digest('hex'));
    });

    request.events.once('disconnect', () => {

        console.error('request aborted');
    });

    return h.continue;
};

server.ext('onRequest', onRequest);
```

#### <a name="request.headers" /> `request.headers`

访问： 只读。

The raw request headers (references `request.raw.req.headers`).

#### <a name="request.info" /> `request.info`

访问： 只读。

Request information:

- `acceptEncoding` - the request preferred encoding.

- `cors` - if CORS is enabled for the route, contains the following:
    - `isOriginMatch` - `true` if the request 'Origin' header matches the configured CORS
      restrictions. Set to `false` if no 'Origin' header is found or if it does not match.
      Note that this is only available after the `'onRequest'` extension point as CORS is
      configured per-route and no routing decisions are made at that point in the request
      lifecycle.

- `host` - content of the HTTP 'Host' header (e.g. 'example.com:8080').

- `hostname` - the hostname part of the 'Host' header (e.g. 'example.com').

- `id` - a unique request identifier (using the format '{now}:{connection.info.id}:{5 digits counter}').

- `received` - request reception timestamp.

- `referrer` - content of the HTTP 'Referrer' (or 'Referer') header.

- `remoteAddress` - remote client IP address.

- `remotePort` - remote client port.

- `responded` - request response timestamp (`0` is not responded yet).

Note that the `request.info` object is not meant to be modified.

#### <a name="request.logs" /> `request.logs`

访问： 只读。

An array containing the logged request events.

Note that this array will be empty if route [`log.collect`](#route.options.log) is set to `false`.

#### <a name="request.method" /> `request.method`

访问： 只读。

The request method in lower case (e.g. `'get'`, `'post'`).

#### <a name="request.mime" /> `request.mime`

访问： 只读。

The parsed content-type header. Only available when payload parsing enabled and no
  payload error occurred.

#### <a name="request.orig" /> `request.orig`

访问： 只读。

An object containing the values of `params`, `query`, and `payload` before any validation
modifications made. Only set when input validation is performed.

#### <a name="request.params" /> `request.params`

访问： 只读。

An object where each key is a path parameter name with matching value as described in
[Path parameters](#path-parameters).

#### <a name="request.paramsArray" /> `request.paramsArray`

访问： 只读。

An array containing all the path `params` values in the order they appeared in the path.

#### <a name="request.path" /> `request.path`

访问： 只读。

The request URI's [pathname](https://nodejs.org/api/url.html#url_urlobject_pathname) component.

#### <a name="request.payload" /> `request.payload`

访问： 只读。

The request payload based on the route `payload.output` and `payload.parse` settings.

#### <a name="request.plugins" /> `request.plugins`

访问： read / write.

Plugin-specific state. Provides a place to store and pass request-level plugin data. The `plugins`
is an object where each key is a plugin name and the value is the state.

#### <a name="request.pre" /> `request.pre`

访问： 只读。

An object where each key is the name assigned by a [route pre-handler methods](#route.options.pre)
function. The values are the raw values provided to the continuation function as argument. For the
wrapped response object, use `responses`.

#### <a name="request.response" /> `request.response`

访问： read / write (see limitations below).

The response object when set. The object can be modified but must not be assigned another object.
To replace the response with another from within an [extension point](#server.ext()), return a new response value. Contains `null` when no response has
been set (e.g. when a request terminates prematurely when the client disconnects).

#### <a name="request.preResponses" /> `request.preResponses`

访问： 只读。

Same as `pre` but represented as the response object created by the pre method.

#### <a name="request.query" /> `request.query`

访问： 只读。

By default the object outputted from [node's URL parse()](https://nodejs.org/docs/latest/api/url.html#url_urlobject_query)
method.  Might also be set indirectly via [request.setUrl](#request.setUrl())
in which case it may be a `string` (if `url` is set to an object with the `query` attribute as an
unparsed string).

#### <a name="request.raw" /> `request.raw`

访问： 只读。

An object containing the Node HTTP server objects. **Direct interaction with these raw objects is
not recommended.**
- `req` - the node request object.
- `res` - the node response object.

#### <a name="request.route" /> `request.route`

访问： 只读。

The request route information object, where:
- `method` - the route HTTP method.
- `path` - the route path.
- `vhost` - the route vhost option if configured.
- `realm` - the [active realm](#server.realm) associated with the route.
- `settings` - the [route options](#route-options) object with all defaults applied.
- `fingerprint` - the route internal normalized string representing the normalized path.

#### <a name="request.server" /> `request.server`

访问： read only and the public server interface.

The server object.

#### <a name="request.state" /> `request.state`

访问： 只读。

An object containing parsed HTTP state information (cookies) where each key is the cookie name and
value is the matching cookie content after processing using any registered cookie definition.

#### <a name="request.url" /> `request.url`

访问： 只读。

The parsed request URI.

### <a name="request.generateResponse()" /> `request.generateResponse(source, [options])`

Returns a [`response`](#response-object) which you can pass into the [reply interface](#response-toolkit) where:
- `source` - the value to set as the source of the [reply interface](#response-toolkit), optional.
- `options` - optional object with the following optioal properties:
    - `variety` - a sting name of the response type (e.g. `'file'`).
    - `prepare` - a function with the signature `async function(response)` used to prepare the
      response after it is returned by a [lifecycle method](#lifecycle-methods) such as setting a
      file descriptor, where:
        - `response` - the response object being prepared.
        - must return the prepared response object (new object or `response`).
        - may throw an error which is used as the prepared response.
    - `marshal` - a function with the signature `async function(response)` used to prepare the
      response for transmission to the client before it is sent, where:
        - `response` - the response object being marshaled.
        - must return the prepared value (not as response object) which can be any value accepted
          by the [`h.response()`](#h.response()) `value` argument.
        - may throw an error which is used as the marshaled value.
    - `close` - a function with the signature `function(response)` used to close the resources
      opened by the response object (e.g. file handlers), where:
        - `response` - the response object being marshaled.
        - should not throw errors (which are logged but otherwise ignored).

### <a name="request.log()" /> `request.log(tags, [data])`

Logs request-specific events. When called, the server emits a [`'request'` event](#server.events.request)
on the `'app'` channel which can be used by other listeners or [plugins](#plugins). The arguments
are:
- `tags` - a string or an array of strings (e.g. `['error', 'database', 'read']`) used to identify
  the event. Tags are used instead of log levels and provide a much more expressive mechanism for
  describing and filtering events.
- `data` - (可选) an message string or object with the application data being logged. If `data`
  is a function, the function signature is `function()` and it called once to generate (return
  value) the actual data emitted to the listeners.

```js
const Hapi = require('hapi');
const server = Hapi.server({ port: 80, routes: { log: { collect: true } } });

server.events.on({ name: 'request', channels: 'app' }, (request, event, tags) => {

    if (tags.error) {
        console.log(event);
    }
});

const handler = function (request, h) {

    request.log(['test', 'error'], 'Test event');
    return null;
};

Note that any logs generated by the server internally will be emitted using the
[`'request'` event](#server.events.request) on the `'internal'` channel.

```js
server.events.on({ name: 'request', channels: 'internal' }, (request, event, tags) => {

    console.log(event);
});
```

### <a name="request.route.auth.access()" /> `request.route.auth.access(request)`

Validates a request against the route's authentication [`access`](#route.options.auth.access)
configuration, where:

- `request` - the [request object](#request).

返回值: `true` if the `request` would have passed the route's access requirements.

Note that the route's authentication mode and strategies are ignored. The only match is made
between the `request.auth.credentials` scope and entity information and the route
[`access`](#route.options.auth.access) configuration.

If the route uses dynamic scopes, the scopes are constructed against the [`request.query`](#request.query),
[`request.params`](#request.params), [`request.payload`](#request.payload), and
[`request.auth.credentials`](#request.auth) which may or may not match between the route and the
request's route. If this method is called using a request that has not been authenticated (yet or
not at all), it will return `false` if the route requires any authentication.

### <a name="request.setMethod()" /> `request.setMethod(method)`

在路由器开始处理请求之前更改请求方法，其中：

- `method` - 请求 HTTP 方法 (例如 `'GET'`).

```js
const Hapi = require('hapi');
const server = Hapi.server({ port: 80 });

const onRequest = function (request, h) {

    // Change all requests to 'GET'
    request.setMethod('GET');
    return h.continue;
};

server.ext('onRequest', onRequest);
```

只能从 `'onRequest'` 扩展方法调用。

### <a name="request.setUrl()" /> `request.setUrl(url, [stripTrailingSlash]`

在路由器开始处理请求之前更改请求 URI，其中：

 - `url` - 新的请求 URI. 如果 `url` 是一个字符串, 用 [node's **URL**
 `parse()`](https://nodejs.org/docs/latest/api/url.html#url_url_parse_urlstring_parsequerystring_slashesdenotehost)
 带有 `parseQueryString` 为 `true` 方法解析它 with `parseQueryString`。 `url` 也可以设置为与 node 的 **URL** `parse()` 方法输出兼容的对象。
 - `stripTrailingSlash` - 如果为 `true`, 从路径中删除尾部斜杠。 默认为 `false`.

```js
const Hapi = require('hapi');
const server = Hapi.server({ port: 80 });

const onRequest = function (request, h) {

    // Change all requests to '/test'
    request.setUrl('/test');
    return h.continue;
};

server.ext('onRequest', onRequest);
```

使用另一个 query string 解析器:

```js
const Url = require('url');
const Hapi = require('hapi');
const Qs = require('qs');

const server = Hapi.server({ port: 80 });

const onRequest = function (request, h) {

    const uri = request.url.href;
    const parsed = Url.parse(uri, false);
    parsed.query = Qs.parse(parsed.query);
    request.setUrl(parsed);

    return h.continue;
};

server.ext('onRequest', onRequest);
```

只能从 `'onRequest'` 扩展方法调用

## 插件

Plugins provide a way to organize application code by splitting the server logic into smaller
components. Each plugin can manipulate the server through the standard server interface, but with
the added ability to sandbox certain properties. For example, setting a file path in one plugin
doesn't affect the file path set in another plugin.

A plugin is an object with the following properties:

- `register` - (required) the registration function with the signature
  `async function(server, options)` where:

    - `server` - the server object with a plugin-specific [`server.realm`](#server.realm).
    - `options` - any options passed to the plugin during registration via [`server.register()`](#server.register()).

- `name` - (required) the plugin name string. The name is used as a unique key. Published plugins
  (e.g. published in the npm registry) should  use the same name as the name field in their
  'package.json' file. Names must be unique within each application.

- `version` - (可选) plugin version string. The version is only used informatively to enable
  other plugins to find out the versions loaded. The version should be the same as the one
  specified in the plugin's 'package.json' file.

- `multiple` - (可选) if `true`, allows the plugin to be registered multiple times with the same server.
  Defaults to `false`.

- `dependencies` - (可选) a string or an array of strings indicating a plugin dependency. Same
  as setting dependencies via [`server.dependency()`](#server.dependency()).

- `once` - (可选) if `true`, will only register the plugin once per server. If set, overrides
  the `once` option passed to [`server.register()`](#server.register()). Defaults to no override.

```js
const plugin = {
    name: 'test',
    version: '1.0.0',
    register: function (server, options) {

        server.route({
            method: 'GET',
            path: '/test',
            handler: function (request, h) {

                return 'ok';
            }
        });
    }
};
```

Alternatively, the `name` and `version` can be included via the `pkg` property containing the
'package.json' file for the module which already has the name and version included:

```js
const plugin = {
    pkg: require('./package.json'),
    register: function (server, options) {

        server.route({
            method: 'GET',
            path: '/test',
            handler: function (request, h) {

                return 'ok';
            }
        });
    }
};
```


## WARNING

本文档使用`Google 翻译`并由个人整理，并不具有专业性，如有异议，请以原文为主。

目前进度 1/5
