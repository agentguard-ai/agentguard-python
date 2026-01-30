# PyPI Publishing Guide

Quick guide to publish the AgentGuard Python SDK to PyPI.

## Prerequisites

1. **PyPI Account**: Create account at https://pypi.org/account/register/
2. **API Token**: Generate at https://pypi.org/manage/account/token/
3. **Install Tools**:
   ```bash
   pip install build twine
   ```

## Publishing Steps

### 1. Build the Package

```bash
cd packages/agentguard-python
python -m build
```

This creates `dist/` with `.whl` and `.tar.gz` files.

### 2. Test Upload (Optional)

Test on TestPyPI first:

```bash
twine upload --repository testpypi dist/*
```

### 3. Upload to PyPI

```bash
twine upload dist/*
```

Enter your PyPI username (`__token__`) and API token when prompted.

### 4. Verify Installation

```bash
pip install agentguard
```

## GitHub Actions (Automated)

The `.github/workflows/publish.yml` workflow automates publishing:

1. **Add PyPI Token to GitHub**:
   - Go to: Settings → Secrets and variables → Actions
   - Click "New repository secret"
   - Name: `PYPI_TOKEN`
   - Value: Your PyPI API token

2. **Create Release**:
   - Go to: Releases → Create new release
   - Tag: `v0.1.0`
   - Title: `v0.1.0`
   - Description: Release notes
   - Publish release

The workflow automatically builds and publishes to PyPI.

## Version Updates

Update version in `pyproject.toml`:

```toml
[project]
version = "0.1.1"
```

## Troubleshooting

- **403 Error**: Check API token permissions
- **File exists**: Version already published, increment version
- **Build fails**: Check `pyproject.toml` syntax

## Resources

- PyPI: https://pypi.org/
- Packaging Guide: https://packaging.python.org/
- Twine Docs: https://twine.readthedocs.io/
