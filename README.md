# UploadKit

**Modular, framework-independent secure upload pipelines for Python.**

Validate once. Upload anywhere. Same policy across Django, FastAPI, Flask, aiohttp, and Odoo.

[Documentation](https://uploadkit.github.io/docs/) · [Website](https://uploadkit.github.io/) · [PyPI](https://pypi.org/project/uploadkit/)

---

## Package status

### uploadkit (core)

[![CI](https://github.com/uploadkit/uploadkit/actions/workflows/ci.yml/badge.svg)](https://github.com/uploadkit/uploadkit/actions/workflows/ci.yml)
[![Coverage](https://img.shields.io/badge/coverage-100%25-brightgreen)](https://github.com/uploadkit/uploadkit/actions/workflows/ci.yml)
[![Python](https://img.shields.io/badge/python-3.10%20%7C%203.11%20%7C%203.12%20%7C%203.13%20%7C%203.14-blue)](https://github.com/uploadkit/uploadkit/blob/main/pyproject.toml)

### uploadkit-django

[![CI](https://github.com/uploadkit/uploadkit-django/actions/workflows/ci.yml/badge.svg)](https://github.com/uploadkit/uploadkit-django/actions/workflows/ci.yml)
[![Coverage](https://img.shields.io/badge/coverage-100%25-brightgreen)](https://github.com/uploadkit/uploadkit-django/actions/workflows/ci.yml)
[![Python](https://img.shields.io/badge/python-3.10%20%7C%203.11%20%7C%203.12%20%7C%203.13-blue)](https://github.com/uploadkit/uploadkit-django/blob/main/pyproject.toml)
[![Django](https://img.shields.io/badge/django-4.2%2B-green)](https://github.com/uploadkit/uploadkit-django/blob/main/pyproject.toml)

### uploadkit-fastapi

[![CI](https://github.com/uploadkit/uploadkit-fastapi/actions/workflows/ci.yml/badge.svg)](https://github.com/uploadkit/uploadkit-fastapi/actions/workflows/ci.yml)
[![Coverage](https://img.shields.io/badge/coverage-100%25-brightgreen)](https://github.com/uploadkit/uploadkit-fastapi/actions/workflows/ci.yml)
[![Python](https://img.shields.io/badge/python-3.10%20%7C%203.11%20%7C%203.12%20%7C%203.13-blue)](https://github.com/uploadkit/uploadkit-fastapi/blob/main/pyproject.toml)
[![FastAPI](https://img.shields.io/badge/fastapi-0.110%2B-teal)](https://github.com/uploadkit/uploadkit-fastapi/blob/main/pyproject.toml)

### uploadkit-flask

[![CI](https://github.com/uploadkit/uploadkit-flask/actions/workflows/ci.yml/badge.svg)](https://github.com/uploadkit/uploadkit-flask/actions/workflows/ci.yml)
[![Coverage](https://img.shields.io/badge/coverage-100%25-brightgreen)](https://github.com/uploadkit/uploadkit-flask/actions/workflows/ci.yml)
[![Python](https://img.shields.io/badge/python-3.10%20%7C%203.11%20%7C%203.12%20%7C%203.13%20%7C%203.14-blue)](https://github.com/uploadkit/uploadkit-flask/blob/main/pyproject.toml)
[![Flask](https://img.shields.io/badge/flask-3.0%2B-black)](https://github.com/uploadkit/uploadkit-flask/blob/main/pyproject.toml)

### uploadkit-odoo

[![CI](https://github.com/uploadkit/uploadkit-odoo/actions/workflows/ci.yml/badge.svg)](https://github.com/uploadkit/uploadkit-odoo/actions/workflows/ci.yml)
[![Coverage](https://img.shields.io/badge/coverage-100%25-brightgreen)](https://github.com/uploadkit/uploadkit-odoo/actions/workflows/ci.yml)
[![Python](https://img.shields.io/badge/python-3.10%20%7C%203.11%20%7C%203.12-blue)](https://github.com/uploadkit/uploadkit-odoo/blob/main/pyproject.toml)
[![Odoo](https://img.shields.io/badge/odoo-17%20%7C%2018-purple)](https://github.com/uploadkit/uploadkit-odoo)

### uploadkit-pdf

[![CI](https://github.com/uploadkit/uploadkit-pdf/actions/workflows/ci.yml/badge.svg)](https://github.com/uploadkit/uploadkit-pdf/actions/workflows/ci.yml)
[![Coverage](https://img.shields.io/badge/coverage-85%25-brightgreen)](https://github.com/uploadkit/uploadkit-pdf/actions/workflows/ci.yml)
[![Python](https://img.shields.io/badge/python-3.10%20%7C%203.11%20%7C%203.12%20%7C%203.13%20%7C%203.14-blue)](https://github.com/uploadkit/uploadkit-pdf/blob/main/pyproject.toml)

### uploadkit-audio

[![CI](https://github.com/uploadkit/uploadkit-audio/actions/workflows/ci.yml/badge.svg)](https://github.com/uploadkit/uploadkit-audio/actions/workflows/ci.yml)
[![Coverage](https://img.shields.io/badge/coverage-81%25-brightgreen)](https://github.com/uploadkit/uploadkit-audio/actions/workflows/ci.yml)
[![Python](https://img.shields.io/badge/python-3.10%20%7C%203.11%20%7C%203.12%20%7C%203.13%20%7C%203.14-blue)](https://github.com/uploadkit/uploadkit-audio/blob/main/pyproject.toml)

### uploadkit-office

[![CI](https://github.com/uploadkit/uploadkit-office/actions/workflows/ci.yml/badge.svg)](https://github.com/uploadkit/uploadkit-office/actions/workflows/ci.yml)
[![Coverage](https://img.shields.io/badge/coverage-79%25-yellow)](https://github.com/uploadkit/uploadkit-office/actions/workflows/ci.yml)
[![Python](https://img.shields.io/badge/python-3.10%20%7C%203.11%20%7C%203.12%20%7C%203.13%20%7C%203.14-blue)](https://github.com/uploadkit/uploadkit-office/blob/main/pyproject.toml)

### uploadkit-cli

[![CI](https://github.com/uploadkit/uploadkit-cli/actions/workflows/ci.yml/badge.svg)](https://github.com/uploadkit/uploadkit-cli/actions/workflows/ci.yml)
[![Python](https://img.shields.io/badge/python-3.10%20%7C%203.11%20%7C%203.12%20%7C%203.13%20%7C%203.14-blue)](https://github.com/uploadkit/uploadkit-cli/blob/main/pyproject.toml)

---

## How the interface works

UploadKit separates **policy**, **validation**, **storage**, and **framework I/O** into clear seams. Core never depends on Django, FastAPI, Flask, Odoo, or any storage SDK.

```text
  Framework file ──► adapter (as_uploadable / as_async_source)
                              │
                              ▼
                     UploadPolicy
                   (size, ext, MIME,
                    validators / async_validators)
                              │
              ┌───────────────┴───────────────┐
              ▼                               ▼
         Uploader                      AsyncUploader
              │                               │
              ▼                               ▼
    StorageProvider.put          AsyncStorageProvider.open_write
              │                               │
              └───────────────┬───────────────┘
                              ▼
                        UploadResult
                              │
                              ▼
                     after_upload hook
                    (callback / Celery .delay)
```

### Core pieces

| Piece | Role |
|-------|------|
| `UploadPolicy` | Declares limits and which validators to run |
| `Uploader` / `AsyncUploader` | Runs validation, then stores the object |
| `UploadableFile` / `AsyncByteSource` | Protocols for the file/stream input |
| `StorageProvider` / `AsyncStorageProvider` | Protocols you implement (e.g. boto3 / aioboto3 → S3 or MinIO) |
| `UploadResult` | Bucket, object name, sha256, etag, … (`as_task_kwargs()` for queues) |
| `after_upload` | Optional hook after a successful store |
| `UploaderError` | Stable exception hierarchy; adapters map it to HTTP/JSON |

### Sync vs async

```text
Sync:  Uploader.upload → validators → StorageProvider.put → UploadResult → after_upload
Async: AsyncUploader.upload → async validators → AsyncStorageProvider writer → UploadResult → after_upload
```

### Minimal Core usage

```bash
pip install uploadkit uploadkit-security
```

```python
from uploadkit import Uploader, UploadPolicy
from uploadkit_security import default_validators

policy = UploadPolicy(
    max_size=5 * 1024 * 1024,
    allowed_extensions=frozenset({"png"}),
    allowed_mime_types=frozenset({"image/png"}),
    validators=default_validators(),
)
result = Uploader(policy, storage).upload(
    file,  # UploadableFile
    bucket="uploads",
    object_name="2026/file.png",
    after_upload=notify,  # optional callback or Celery-like .delay
)
# result.bucket, result.object_name, result.sha256, result.etag, …
```

You supply `storage` by implementing `StorageProvider.put(...)` (see the [Core README](https://github.com/uploadkit/uploadkit#storage-examples-aws-s3-and-minio) for AWS S3 / MinIO samples).

---

## Integrate with your project (frameworks)

Install the adapter for your framework plus `uploadkit-security`. Each adapter only bridges framework files ↔ Core and maps `UploaderError` to responses — policies and storage stay yours.

| Framework | Package | Docs |
|-----------|---------|------|
| Django | [`uploadkit-django`](https://github.com/uploadkit/uploadkit-django) | [Guide](https://uploadkit.github.io/docs/django/) |
| FastAPI | [`uploadkit-fastapi`](https://github.com/uploadkit/uploadkit-fastapi) | [Guide](https://uploadkit.github.io/docs/fastapi/) |
| Flask | [`uploadkit-flask`](https://github.com/uploadkit/uploadkit-flask) | [Guide](https://uploadkit.github.io/docs/flask/) |
| Odoo | [`uploadkit-odoo`](https://github.com/uploadkit/uploadkit-odoo) | [Guide](https://uploadkit.github.io/docs/odoo/) |
| aiohttp | Core `AsyncByteSource` directly | [Guide](https://uploadkit.github.io/docs/aiohttp/) |

### Django

```bash
pip install uploadkit-django uploadkit-security
```

```python
from django.conf import settings
from django.http import JsonResponse
from uploadkit import Uploader, UploadPolicy, UploaderError
from uploadkit_django import as_uploadable, get_storage_provider, json_error_response
from uploadkit_security import default_validators

def upload_view(request):
    storage = get_storage_provider()
    policy = UploadPolicy(
        max_size=5 * 1024 * 1024,
        allowed_extensions=frozenset({"png"}),
        allowed_mime_types=frozenset({"image/png"}),
        validators=default_validators(),
    )
    uploaded = request.FILES["file"]
    try:
        result = Uploader(policy, storage).upload(
            as_uploadable(uploaded),
            bucket=settings.UPLOADKIT_BUCKET,
            object_name=uploaded.name,
        )
    except UploaderError as exc:
        return json_error_response(exc)
    return JsonResponse({"object_name": result.object_name, "sha256": result.sha256})
```

Point `UPLOADKIT_STORAGE_PROVIDER` at your `StorageProvider` factory (boto3 for AWS/MinIO).

### FastAPI

```bash
pip install uploadkit-fastapi uploadkit-security
```

```python
from fastapi import BackgroundTasks, FastAPI, UploadFile
from uploadkit import AsyncUploader, UploadPolicy, UploaderError
from uploadkit_fastapi import as_async_source, background_after_upload, json_error_response
from uploadkit_security import default_async_validators

app = FastAPI()

@app.post("/upload")
async def upload(file: UploadFile, background_tasks: BackgroundTasks):
    policy = UploadPolicy(
        max_size=5 * 1024 * 1024,
        allowed_extensions=frozenset({"png"}),
        allowed_mime_types=frozenset({"image/png"}),
        async_validators=default_async_validators(),
    )
    try:
        result = await AsyncUploader(policy, async_storage).upload(
            as_async_source(file),
            bucket="uploads",
            object_name=file.filename or "object",
            after_upload=background_after_upload(background_tasks, notify),
        )
    except UploaderError as exc:
        return json_error_response(exc)
    return {"object_name": result.object_name, "sha256": result.sha256}
```

Use `Uploader` + `as_uploadable` + `run_sync_upload` when you prefer the sync stack inside an async route.

### Flask

```bash
pip install uploadkit-flask uploadkit-security
```

```python
from flask import current_app, jsonify, request
from uploadkit import Uploader, UploadPolicy, UploaderError
from uploadkit_flask import as_uploadable, get_storage_provider, json_error_response
from uploadkit_security import default_validators

@app.post("/upload")
def upload_view():
    storage = get_storage_provider()
    policy = UploadPolicy(
        max_size=5 * 1024 * 1024,
        allowed_extensions=frozenset({"png"}),
        allowed_mime_types=frozenset({"image/png"}),
        validators=default_validators(),
    )
    uploaded = request.files["file"]
    try:
        result = Uploader(policy, storage).upload(
            as_uploadable(uploaded),
            bucket=current_app.config["UPLOADKIT_BUCKET"],
            object_name=uploaded.filename,
        )
    except UploaderError as exc:
        return json_error_response(exc)
    return jsonify({"object_name": result.object_name, "sha256": result.sha256})
```

### Odoo

```bash
pip install uploadkit-odoo uploadkit-security
```

```python
from odoo import http
from odoo.http import request
from uploadkit import Uploader, UploadPolicy, UploaderError
from uploadkit_odoo import as_uploadable, json_error_response
from uploadkit_security import default_validators

class MyController(http.Controller):
    @http.route("/my/upload", type="http", auth="user", methods=["POST"], csrf=True)
    def upload(self, **kw):
        policy = UploadPolicy(
            max_size=5 * 1024 * 1024,
            allowed_extensions=frozenset({"png"}),
            allowed_mime_types=frozenset({"image/png"}),
            validators=default_validators(),
        )
        uploaded = kw.get("file")
        try:
            result = Uploader(policy, storage).upload(
                as_uploadable(uploaded),
                bucket="uploads",
                object_name=uploaded.filename,
            )
        except UploaderError as exc:
            return json_error_response(exc)
        return request.make_json_response(result.as_task_kwargs())
```

An optional Odoo 17/18 addon is included in the repo for settings and a thin upload service.

---

## Ecosystem packages

| Package | Role |
|---------|------|
| [`uploadkit`](https://github.com/uploadkit/uploadkit) | Core pipeline |
| [`uploadkit-security`](https://github.com/uploadkit/uploadkit-security) | MIME, filename, checksum validators |
| [`uploadkit-pdf`](https://github.com/uploadkit/uploadkit-pdf) / [`-office`](https://github.com/uploadkit/uploadkit-office) / [`-audio`](https://github.com/uploadkit/uploadkit-audio) | Feature policies |
| [`uploadkit-cli`](https://github.com/uploadkit/uploadkit-cli) | Developer CLI |
| [`uploadkit-testing`](https://github.com/uploadkit/uploadkit-testing) | Shared test utilities |
| [`uploadkit-specs`](https://github.com/uploadkit/uploadkit-specs) | RFCs & ADRs |
| [`uploadkit.github.io`](https://github.com/uploadkit/uploadkit.github.io) | Docs site |

## Links

- Docs: https://uploadkit.github.io/docs/
- Organization: https://github.com/uploadkit
