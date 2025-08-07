# 🔴 Redstone

_A blazingly fast, zero-cost web framework for Zig inspired by Hono's developer experience_

[![Zig](https://img.shields.io/badge/zig-0.13+-orange.svg)](https://ziglang.org/)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Build Status](https://img.shields.io/badge/build-in--progress-yellow.svg)](https://github.com/yourusername/redstone)

> **"Wire your web APIs with the same precision and modularity that makes Minecraft's Redstone legendary."**

Redstone brings Hono's exceptional developer experience to Zig, combining **zero-cost abstractions**, **compile-time safety**, and **competitive performance**.

## 🎯 **Vision**

- **🚀 Performance**: Competitive with top-tier frameworks (Axum, Gin) while maintaining excellent DX
- **🛡️ Safety**: Leverage Zig's compile-time guarantees without runtime cost
- **🎭 Developer Experience**: Build production APIs in minutes, not hours
- **🧩 Zero-Cost Abstractions**: Rich APIs that compile to optimal machine code

---

## 📋 **Development Roadmap & Feature Checklist**

### **Phase 0: Foundation** 🏗️

_Core architecture and basic HTTP handling_

- [ ] **Project Structure**
  - [ ] Build system (`build.zig`)
  - [ ] CI/CD pipeline (GitHub Actions)
  - [ ] Basic documentation structure
  - [ ] License and contributing guidelines

- [ ] **Core Types**
  - [ ] `Context` struct (request/response wrapper)
  - [ ] `Router` struct (route storage and matching)
  - [ ] `App` struct (main application interface)
  - [ ] `Handler` function signature
  - [ ] `Middleware` function signature

- [ ] **Basic HTTP Server**
  - [ ] TCP listener integration
  - [ ] HTTP request parsing
  - [ ] HTTP response writing
  - [ ] Connection management
  - [ ] Error handling framework

- [ ] **Simple Routing**
  - [ ] Static route registration (`/about`)
  - [ ] Static route matching (exact path)
  - [ ] Basic route storage (ArrayList)
  - [ ] Route dispatch to handlers

### **Phase 1: Advanced Routing** 🛣️

_Complete routing system with parameters and patterns_

- [ ] **Path Parameters**
  - [ ] Parameter extraction (`:id`, `:name`)
  - [ ] Parameter storage in Context
  - [ ] `ctx.param("name")` getter
  - [ ] `ctx.paramAs(T, "name")` typed conversion
  - [ ] Multiple parameters in single route

- [ ] **Wildcard Routes**
  - [ ] Single wildcard (`/files/*path`)
  - [ ] Greedy path capture
  - [ ] Directory traversal protection
  - [ ] URL decoding for captured paths

- [ ] **Route Constraints**
  - [ ] Regex patterns (`/posts/:id(\\d+)`)
  - [ ] Compile-time regex compilation
  - [ ] Custom constraint functions
  - [ ] Constraint validation performance

- [ ] **HTTP Methods**
  - [ ] `.get()`, `.post()`, `.put()`, `.delete()`
  - [ ] `.patch()`, `.head()`, `.options()`
  - [ ] `.all()` (method-agnostic routes)
  - [ ] Custom HTTP methods support

- [ ] **Route Organization**
  - [ ] Route groups (`app.group("/api")`)
  - [ ] Nested groups (`/api/v1/admin`)
  - [ ] Route prefixes and middleware inheritance
  - [ ] Sub-application mounting (`app.mount()`)

- [ ] **Route Performance**
  - [ ] Trie-based route storage
  - [ ] O(1) static route lookup
  - [ ] Route priority system (static > param > wildcard)
  - [ ] Benchmarking suite

### **Phase 2: Context & Request/Response API** 🎭

_Rich request/response handling with zero-copy optimizations_

- [ ] **Request Data Access**
  - [ ] Headers (`ctx.getHeader()`, `ctx.hasHeader()`)
  - [ ] Query parameters (`ctx.query()`, `ctx.queryAs()`)
  - [ ] Path parameters (from Phase 1)
  - [ ] HTTP method and URL access
  - [ ] Raw request body access

- [ ] **Response Helpers**
  - [ ] `ctx.json(value)` - JSON serialization
  - [ ] `ctx.text(content)` - Plain text
  - [ ] `ctx.html(content)` - HTML responses
  - [ ] `ctx.status(code)` - Status code setting
  - [ ] `ctx.setHeader(name, value)` - Response headers

- [ ] **Advanced Response Features**
  - [ ] `ctx.redirect(url, status)` - HTTP redirects
  - [ ] `ctx.file(path)` - Static file serving
  - [ ] `ctx.stream(writer_fn)` - Streaming responses
  - [ ] Response chaining (`ctx.status(201).json(data)`)
  - [ ] Custom response writers

- [ ] **Body Parsing**
  - [ ] `ctx.body.json(T)` - JSON deserialization
  - [ ] `ctx.body.text()` - Raw text content
  - [ ] `ctx.body.raw()` - Raw bytes
  - [ ] Body size limits and validation
  - [ ] Streaming body parser

- [ ] **Cookie Support**
  - [ ] `ctx.getCookie(name)` - Cookie parsing
  - [ ] `ctx.setCookie(name, value, opts)` - Cookie setting
  - [ ] Secure, HttpOnly, SameSite attributes
  - [ ] Cookie signing and encryption
  - [ ] Cookie jar management

- [ ] **Variable Store**
  - [ ] `ctx.set(key, value)` - Type-safe storage
  - [ ] `ctx.get(T, key)` - Type-safe retrieval
  - [ ] Request-scoped data sharing
  - [ ] Middleware communication

### **Phase 3: Core Middleware System** 🧩

_Essential middleware with zero-cost composition_

- [ ] **Middleware Architecture**
  - [ ] Middleware function signature
  - [ ] `next()` continuation handling
  - [ ] Middleware composition pipeline
  - [ ] Error propagation through middleware
  - [ ] Middleware ordering and priority

- [ ] **Development Middleware**
  - [ ] `logger()` - Request logging
    - [ ] Configurable log formats (JSON, text)
    - [ ] Request ID correlation
    - [ ] Response time tracking
    - [ ] Custom log fields
  - [ ] `requestId()` - Request ID generation
  - [ ] `timing()` - Server-Timing headers

- [ ] **Security Middleware**
  - [ ] `cors()` - CORS handling
    - [ ] Origins, methods, headers configuration
    - [ ] Preflight request handling
    - [ ] Credentials support
    - [ ] Custom CORS policies
  - [ ] `secureHeaders()` - Security headers
    - [ ] Content Security Policy (CSP)
    - [ ] X-Frame-Options, X-XSS-Protection
    - [ ] HSTS (HTTP Strict Transport Security)
    - [ ] Custom security headers
  - [ ] `rateLimiter()` - Rate limiting
    - [ ] Token bucket algorithm
    - [ ] Memory-based storage
    - [ ] Per-IP and per-key limiting
    - [ ] Custom key extraction
    - [ ] Rate limit headers

- [ ] **Performance Middleware**
  - [ ] `compress()` - Response compression
    - [ ] Gzip compression
    - [ ] Deflate compression
    - [ ] Compression level configuration
    - [ ] Content-type filtering
  - [ ] `etag()` - ETag generation
    - [ ] Weak and strong ETags
    - [ ] Conditional request handling
    - [ ] Cache validation
  - [ ] `cache()` - Response caching
    - [ ] In-memory cache store
    - [ ] TTL-based expiration
    - [ ] Cache key generation
    - [ ] Cache headers

- [ ] **Content Middleware**
  - [ ] `serveStatic()` - Static file serving
    - [ ] Directory serving with index files
    - [ ] MIME type detection
    - [ ] Range request support
    - [ ] Directory traversal protection
    - [ ] Compression integration
  - [ ] `bodyParser()` - Request body parsing
    - [ ] JSON parsing with size limits
    - [ ] URL-encoded form parsing
    - [ ] Multipart form data
    - [ ] File upload handling
    - [ ] Raw body parsing

### **Phase 4: Authentication & Authorization** 🔐

_Secure authentication patterns with crypto integration_

- [ ] **Basic Authentication**
  - [ ] `basicAuth()` middleware
  - [ ] Username/password validation
  - [ ] Realm configuration
  - [ ] Custom authentication functions

- [ ] **Token Authentication**
  - [ ] `bearerAuth()` middleware
  - [ ] Token extraction from headers
  - [ ] Custom token validation
  - [ ] Token prefix configuration

- [ ] **JWT Support**
  - [ ] `jwt()` middleware
  - [ ] Token signing and verification
  - [ ] Multiple algorithms (HS256, RS256)
  - [ ] Claims validation
  - [ ] Token refresh handling
  - [ ] Custom claims extraction

- [ ] **Session Management**
  - [ ] `session()` middleware
  - [ ] Session creation and validation
  - [ ] Multiple storage backends
  - [ ] Session encryption
  - [ ] CSRF protection

### **Phase 5: Real-Time Features** ⚡

_WebSocket, SSE, and streaming capabilities_

- [ ] **WebSocket Support**
  - [ ] WebSocket upgrade handling
  - [ ] `ctx.upgradeWebSocket(handler)`
  - [ ] Message routing and handling
  - [ ] Connection management
  - [ ] Broadcast capabilities
  - [ ] Room/channel support
  - [ ] WebSocket middleware

- [ ] **Server-Sent Events**
  - [ ] `ctx.sse` API
  - [ ] Event streaming
  - [ ] Connection keep-alive
  - [ ] Event formatting (data, event, id)
  - [ ] Retry configuration
  - [ ] Client reconnection handling

- [ ] **Streaming Responses**
  - [ ] Chunked transfer encoding
  - [ ] `ctx.stream(writer_fn)`
  - [ ] Backpressure handling
  - [ ] Stream error handling
  - [ ] Large file streaming

### **Phase 6: Advanced Features** 🚀

_Production-ready capabilities and developer experience_

- [ ] **Async Support**
  - [ ] Async handler functions
  - [ ] Non-blocking I/O integration
  - [ ] Concurrent request handling
  - [ ] Async middleware support
  - [ ] Structured concurrency

- [ ] **Input Validation**
  - [ ] Schema definition with structs
  - [ ] `validator()` middleware
  - [ ] Request validation (body, query, params)
  - [ ] Custom validation rules
  - [ ] Error message formatting
  - [ ] Sanitization support

- [ ] **Template Engine**
  - [ ] `ctx.render(template, data)`
  - [ ] Template compilation
  - [ ] Partial/component support
  - [ ] Template inheritance
  - [ ] Auto-escaping for security
  - [ ] Custom template functions

- [ ] **File Upload & Multipart**
  - [ ] `ctx.files` API
  - [ ] Multipart form parsing
  - [ ] File size limits
  - [ ] MIME type validation
  - [ ] Memory vs disk storage
  - [ ] File upload progress

### **Phase 7: Developer Experience** 🛠️

_Tooling and utilities for productivity_

- [ ] **CLI Tool**
  - [ ] `redstone new <project>` - Project scaffolding
  - [ ] `redstone dev` - Development server
  - [ ] `redstone build` - Production builds
  - [ ] Project templates
  - [ ] Hot reload support

- [ ] **Testing Framework**
  - [ ] `redstone.testing.testApp()`
  - [ ] Mock request/response objects
  - [ ] Test client for HTTP requests
  - [ ] Assertion helpers
  - [ ] Integration test utilities

- [ ] **OpenAPI Generation**
  - [ ] Compile-time route analysis
  - [ ] Automatic spec generation
  - [ ] Parameter and response schemas
  - [ ] Documentation integration
  - [ ] Client code generation

- [ ] **Development Middleware**
  - [ ] `prettyJSON()` - Beautiful JSON formatting
  - [ ] Error page middleware (dev mode)
  - [ ] Route listing and debugging
  - [ ] Performance profiling
  - [ ] Memory usage monitoring

### **Phase 8: Production & Performance** 🏭

_Enterprise-ready features and optimizations_

- [ ] **TLS/SSL Support**
  - [ ] HTTPS server integration
  - [ ] Certificate management
  - [ ] TLS configuration options
  - [ ] SNI (Server Name Indication)
  - [ ] Certificate auto-renewal hooks

- [ ] **HTTP/2 Support**
  - [ ] HTTP/2 protocol implementation
  - [ ] Request multiplexing
  - [ ] Server push capabilities
  - [ ] Header compression (HPACK)
  - [ ] Stream prioritization

- [ ] **Graceful Shutdown**
  - [ ] Signal handling (SIGTERM, SIGINT)
  - [ ] Connection draining
  - [ ] Request completion waiting
  - [ ] Cleanup callbacks
  - [ ] Zero-downtime deployments

- [ ] **Monitoring & Metrics**
  - [ ] `metrics()` middleware
  - [ ] Prometheus metrics format
  - [ ] Custom metric collectors
  - [ ] Health check endpoints
  - [ ] Performance counters

- [ ] **Production Middleware**
  - [ ] `recovery()` - Panic recovery
  - [ ] `timeout()` - Request timeouts
  - [ ] `circuitBreaker()` - Fault tolerance
  - [ ] `healthCheck()` - Health monitoring

### **Phase 9: Database & Integration** 🗄️

_Database connectivity and external service integration_

- [ ] **Database Integration**
  - [ ] Connection pool management
  - [ ] Query builder integration
  - [ ] Transaction support
  - [ ] Migration utilities
  - [ ] Multiple database adapters

- [ ] **Background Jobs**
  - [ ] `ctx.queue.push(job)`
  - [ ] Job processing workers
  - [ ] Job retry and error handling
  - [ ] Queue backends (Redis, database)
  - [ ] Scheduled jobs (cron-like)

- [ ] **External Services**
  - [ ] HTTP client integration
  - [ ] Service discovery
  - [ ] Circuit breaker patterns
  - [ ] Retry mechanisms
  - [ ] Load balancing

### **Phase 10: Ecosystem & Community** 🌟

_Plugin system and community features_

- [ ] **Plugin Architecture**
  - [ ] Plugin registration system
  - [ ] Plugin lifecycle management
  - [ ] Plugin configuration
  - [ ] Plugin marketplace/registry

- [ ] **Internationalization**
  - [ ] `ctx.t(key, params, locale)`
  - [ ] Translation loading
  - [ ] Locale detection
  - [ ] Pluralization support
  - [ ] Date/time formatting

- [ ] **Advanced Tooling**
  - [ ] Performance profiler
  - [ ] Memory analyzer
  - [ ] Load testing utilities
  - [ ] Deployment helpers
  - [ ] Configuration management

---

## 🏆 **Performance Targets**

> _Realistic goals that prioritize excellent developer experience with competitive performance_

- [ ] **Latency Goals**
  - [ ] Hello World: ~100μs P99 (competitive with Axum/Gin)
  - [ ] JSON API: ~500μs P99 (small payloads)
  - [ ] Static files: ~200μs P99 (with caching)
  - [ ] WebSocket: ~50μs message routing

- [ ] **Throughput Goals**
  - [ ] 50k+ req/s (hello world, single core)
  - [ ] 20k+ req/s (JSON API with middleware)
  - [ ] 5k+ concurrent WebSocket connections
  - [ ] 100k+ req/s (static files with compression)

- [ ] **Framework Overhead**
  - [ ] ~10-20% vs raw `std.http` (excellent for a framework)
  - [ ] Competitive with Axum, faster than Gin
  - [ ] Much faster than Node.js/Python frameworks

- [ ] **Resource Usage**
  - [ ] <50MB memory for 5k connections
  - [ ] <10MB binary size for typical app
  - [ ] <60s compile time for medium projects
  - [ ] Minimal allocations per request

---

## 🤝 **How to Contribute**

1. **Pick a feature** from the checklist above
2. **Check the issues** for that feature or create a new one
3. **Fork and implement** the feature
4. **Add tests** and update documentation
5. **Submit a PR** with clear description

**Priority areas for contributors:**

- Phase 1 (Advanced Routing) - Core functionality
- Phase 2 (Context API) - Developer experience
- Phase 3 (Core Middleware) - Essential features
<!--

## 📞 **Join the Community**

<!-- - **GitHub Discussions**: [Ask questions and share ideas](https://github.com/yourusername/redstone/discussions)
- **Discord**: [Join our server](https://discord.gg/redstone) for real-time chat
- **Issues**: [Report bugs or request features](https://github.com/yourusername/redstone/issues)

---

-->
<div align="center">

**⭐ Star this repo** to follow development progress!

**Current Phase**: 🏗️ Foundation (Phase 0)  
**Next Milestone**: Basic HTTP server and simple routing

</div>
