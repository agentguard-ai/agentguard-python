# AgentGuard Python SDK

> Enterprise-grade security for AI agents - Runtime protection, policy enforcement, and comprehensive audit trails

[![PyPI version](https://badge.fury.io/py/agentguard.svg)](https://pypi.org/project/agentguard/)
[![Python versions](https://img.shields.io/pypi/pyversions/agentguard.svg)](https://pypi.org/project/agentguard/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 🚀 Quick Start

```bash
pip install agentguard
```

```python
from agentguard import AgentGuard

# Initialize the security client
guard = AgentGuard(
    api_key="your-api-key",
    ssa_url="https://ssa.agentguard.io"
)

# Secure your agent tool calls
result = await guard.execute_tool(
    tool_name="web-search",
    parameters={"query": "AI agent security"},
    context={"session_id": "user-session-123"}
)

print(f"Secure result: {result.data}")
print(f"Security decision: {result.security_decision}")
```

## ✨ Features

- 🛡️ **Runtime Security Enforcement** - Mediate all agent tool/API calls through security policies
- 📋 **Policy-Based Access Control** - Define and enforce security policies with ease
- 🔍 **Comprehensive Audit Trails** - Track every agent action with tamper-evident logs
- ⚡ **High Performance** - <100ms latency for security decisions
- 🔧 **Type Hints** - Full type annotations for better IDE support
- 🎯 **Request Transformation** - Automatically transform risky requests into safer alternatives
- 🔐 **Zero-Trust Architecture** - Never trust, always verify
- 📊 **Real-time Monitoring** - Track agent behavior and security events
- 🔄 **Async Support** - Built-in async/await support for modern Python applications

## 📖 Installation

### Using pip

```bash
pip install agentguard
```

### Using poetry

```bash
poetry add agentguard
```

### From source

```bash
git clone https://github.com/agentguard-ai/agentguard-python.git
cd agentguard-python
pip install -e .
```

## 🎯 Usage Examples

### Basic Usage

```python
from agentguard import AgentGuard

guard = AgentGuard(
    api_key="your-api-key",
    ssa_url="http://localhost:3000"
)

# Synchronous execution
result = guard.execute_tool_sync(
    tool_name="file-write",
    parameters={
        "path": "/data/output.txt",
        "content": "Agent generated content"
    },
    context={
        "session_id": "agent-session-456",
        "user_id": "user-123"
    }
)

if result.success:
    print(f"Tool executed securely: {result.data}")
else:
    print(f"Security policy blocked: {result.error}")
```

### Async Usage

```python
import asyncio
from agentguard import AgentGuard

async def main():
    guard = AgentGuard(
        api_key="your-api-key",
        ssa_url="http://localhost:3000"
    )
    
    result = await guard.execute_tool(
        tool_name="database-query",
        parameters={"query": "SELECT * FROM users LIMIT 10"},
        context={"session_id": "session-789"}
    )
    
    print(result.data)

asyncio.run(main())
```

### Policy Testing

```python
from agentguard import PolicyTester

tester = PolicyTester()

# Test your policies before deployment
result = tester.test_policy(
    policy=my_policy,
    request={
        "tool_name": "database-query",
        "parameters": {"query": "SELECT * FROM users"}
    }
)

print(f"Policy decision: {result.decision}")
print(f"Reasoning: {result.reason}")
```

### Policy Builder

```python
from agentguard import PolicyBuilder

policy = (
    PolicyBuilder()
    .name("restrict-file-operations")
    .description("Prevent file write operations")
    .add_rule(
        condition={"tool_name": "file-write"},
        action="deny",
        reason="File write operations are not allowed"
    )
    .add_rule(
        condition={"tool_name": "file-read"},
        action="allow",
        reason="File read operations are permitted"
    )
    .build()
)

print(f"Policy created: {policy}")
```

## 🔧 Configuration

### Basic Configuration

```python
guard = AgentGuard(
    api_key="your-api-key",
    ssa_url="https://ssa.agentguard.io",
    timeout=5.0,
    max_retries=3
)
```

### Advanced Configuration

```python
guard = AgentGuard(
    api_key=os.getenv("AGENTGUARD_API_KEY"),
    ssa_url=os.getenv("AGENTGUARD_SSA_URL"),
    
    # Timeout settings
    timeout=10.0,
    max_retries=3,
    retry_delay=1.0,
    
    # Logging
    log_level="INFO",
    
    # Custom headers
    headers={
        "X-Custom-Header": "value"
    },
    
    # Callback hooks
    on_security_decision=lambda decision: print(f"Decision: {decision}"),
    on_error=lambda error: print(f"Error: {error}")
)
```

## 📚 Documentation

- [Getting Started Guide](https://github.com/agentguard-ai/agentguard-python#getting-started)
- [API Reference](https://github.com/agentguard-ai/agentguard-python/blob/main/docs/API.md)
- [Policy Configuration](https://github.com/agentguard-ai/agentguard-python/blob/main/docs/POLICIES.md)
- [Examples](https://github.com/agentguard-ai/agentguard-python/tree/main/examples)

## 🤝 Contributing

We welcome contributions! Please see our [Contributing Guide](CONTRIBUTING.md) for details.

## 📄 License

MIT © AgentGuard

## 🔒 Security

Security is our top priority. If you discover a security vulnerability, please email agentguard@proton.me instead of using the issue tracker.

See [SECURITY.md](SECURITY.md) for more details.

## 🌟 Why AgentGuard?

### The Problem

AI agents are powerful but pose significant security risks:
- Unrestricted access to tools and APIs
- No audit trail of agent actions
- Difficult to enforce security policies
- Hard to debug agent behavior

### The Solution

AgentGuard provides:
- ✅ **Runtime Security** - Every tool call is evaluated before execution
- ✅ **Policy Enforcement** - Define what agents can and cannot do
- ✅ **Audit Trails** - Complete visibility into agent actions
- ✅ **Request Transformation** - Automatically make risky requests safer
- ✅ **Zero-Trust** - Never trust, always verify

## 🚀 Roadmap

- [x] Core SDK with policy enforcement
- [x] Type hints and async support
- [x] Comprehensive test suite
- [ ] Drop-in integrations (LangChain, CrewAI, AutoGPT)
- [ ] Built-in guardrails library
- [ ] Cost monitoring and budget enforcement
- [ ] Visual policy management UI
- [ ] Real-time monitoring dashboard

## 💬 Community

- [GitHub Discussions](https://github.com/agentguard-ai/agentguard-python/discussions) - Ask questions and share ideas
- [GitHub Issues](https://github.com/agentguard-ai/agentguard-python/issues) - Report bugs and request features
- [Email](mailto:agentguard@proton.me) - Direct contact

---

**Built with ❤️ by the AgentGuard team**

[GitHub](https://github.com/agentguard-ai/agentguard-python) • [PyPI](https://pypi.org/project/agentguard/) • [Email](mailto:agentguard@proton.me)
