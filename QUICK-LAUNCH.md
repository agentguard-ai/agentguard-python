# Quick Launch Guide

Fast-track guide to launch the Python SDK.

## 1. Create GitHub Repository (2 minutes)

Go to: https://github.com/organizations/agentguard-ai/repositories/new

- Name: `agentguard-python`
- Description: `Python SDK for AI Agent Security Platform`
- Public
- **No README** (we have our own)
- Create

## 2. Push Code (1 minute)

```bash
cd packages/agentguard-python
git init
git add .
git commit -m "Initial commit: Python SDK v0.1.0"
git branch -M main
git remote add origin https://github.com/agentguard-ai/agentguard-python.git
git push -u origin main
```

## 3. Setup PyPI (5 minutes)

### Create Account
- Go to: https://pypi.org/account/register/
- Register with agentguard@proton.me
- Verify email

### Generate Token
- Go to: https://pypi.org/manage/account/token/
- Click "Add API token"
- Name: `GitHub Actions - agentguard-python`
- Scope: "Entire account"
- Copy token (starts with `pypi-`)

### Add to GitHub
- Go to: https://github.com/agentguard-ai/agentguard-python/settings/secrets/actions
- New repository secret
- Name: `PYPI_TOKEN`
- Value: Paste token
- Add secret

## 4. Create Release (2 minutes)

Go to: https://github.com/agentguard-ai/agentguard-python/releases/new

**Tag**: `v0.1.0`

**Title**: `v0.1.0 - Initial Release`

**Description**:
```markdown
🎉 Initial release of the AgentGuard Python SDK!

## Features
- 🛡️ Runtime security enforcement
- 📋 Policy-based access control
- 🔍 Comprehensive audit trails
- ⚡ <100ms latency
- 🔧 Full type hints
- 🔄 Async/sync support

## Installation
```bash
pip install agentguard
```

## Quick Start
```python
from agentguard import AgentGuard

guard = AgentGuard(
    api_key="your-api-key",
    ssa_url="https://ssa.agentguard.io"
)

result = await guard.execute_tool(
    tool_name="web-search",
    parameters={"query": "AI security"},
    context={"session_id": "session-123"}
)
```

## Links
- PyPI: https://pypi.org/project/agentguard/
- Docs: https://github.com/agentguard-ai/agentguard-python#readme
```

Click **Publish release** → GitHub Action will auto-publish to PyPI!

## 5. Enable Features (1 minute)

### Discussions
- Settings → General → Features → ✓ Discussions

### Topics
Click gear icon next to "About", add:
```
python sdk ai security agent langchain openai guardrails llm anthropic claude policy governance compliance audit
```

## 6. Verify (1 minute)

```bash
pip install agentguard
python -c "from agentguard import AgentGuard; print('✅ Success!')"
```

Check PyPI: https://pypi.org/project/agentguard/

## Done! 🎉

Total time: ~12 minutes

## Troubleshooting

**Push fails**: Check repository exists and you have access
**PyPI publish fails**: Verify PYPI_TOKEN is correct
**Import fails**: Wait 1-2 minutes for PyPI to propagate

## Next Steps

- Monitor PyPI downloads
- Respond to issues/discussions
- Share on social media
- Update TypeScript SDK README to mention Python SDK
