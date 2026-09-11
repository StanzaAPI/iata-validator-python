# IATA Air Cargo AWB & Aviation Validator — Python SDK

[![PyPI version](https://img.shields.io/pypi/v/stanzaapi-iata-validator.svg)](https://pypi.org/project/stanzaapi-iata-validator/)
[![Python Versions](https://img.shields.io/pypi/pyversions/stanzaapi-iata-validator.svg)](https://pypi.org/project/stanzaapi-iata-validator/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Stanza API](https://img.shields.io/badge/Powered%20by-Stanza-blue)](https://stanzaapi.com)

> Validate IATA Resolution 600a Air Waybills (11-digit MOD-7), e-tickets, and airline accounting prefixes in sub-5ms.

Official, zero-dependency Python 3.8+ client library for **IATA Air Cargo AWB & Aviation Validator**, built on the [Stanza Micro-API Network](https://stanzaapi.com). Intended for enterprise data pipelines, backend verification, and sub-5ms edge compute.

* 🌐 **Live Web Playground:** [Test your inputs online](https://stanzaapi.com/tools/iata-validator)
* 📚 **API Documentation:** [View full schema on Stanza](https://stanzaapi.com/tools/iata-validator)
* ⚡ **Platform Overview:** [Explore the Stanza Developer Network](https://stanzaapi.com)

---

## 📦 Installation

```bash
pip install stanzaapi-iata-validator
```

---

## 🚀 Quickstart

```python
import os
from stanzaapi_iata_validator import IataValidatorClient

# Initialize client (api_key optional for local evaluation)
client = IataValidatorClient(
    api_key=os.getenv("STANZA_API_KEY")
)

# Execute deterministic validation
response = client.validate("020-12345675")

if response.get("success"):
    print("Verification Success:", response["data"])
else:
    print("Validation Error:", response.get("error"), response.get("code"))
```

---

## 📄 Example Response

```json
{
  "success": true,
  "data": {
    "valid": true,
    "prefix": "020",
    "airline": "Lufthansa Cargo",
    "serial_number": "1234567",
    "check_digit": 5
  }
}
```

---

## ⚙️ Client Options

| Parameter | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `api_key` | `Optional[str]` | `os.getenv("STANZA_API_KEY")` | Your [Stanza API Key](https://stanzaapi.com). Required for production quotas. |
| `base_url` | `Optional[str]` | `"https://api.stanzaapi.com/iata-validator"` | Public edge API base URL. |
| `timeout` | `int` | `15` | Request timeout in seconds. |


---

## 🔗 Useful Links

* [IATA Air Cargo AWB & Aviation Validator Interactive Sandbox](https://stanzaapi.com/tools/iata-validator)
* [Stanza Developer Directory](https://stanzaapi.com)
* [Source Code & Issue Tracker](https://github.com/StanzaAPI/iata-validator-python)

## 📄 License

MIT © Stanza — Powered by [Stanza](https://stanzaapi.com).
