# Holy Grail Verification API v1.0

> Ancient structure analysis, Pythagorean comma verification,
> Serenal Framework consistency check.

## Quick Start

```bash
pip install flask
python api_grail.py --port 5002
```

Then visit `http://localhost:5002/api/v1/constants`.

## API Endpoints

| Endpoint | Method | Description |
|----------|--------|-------------|
| /api/v1/health | GET | Service status |
| /api/v1/constants | GET | All grail constants (computed live) |
| /api/v1/comma | GET | Pythagorean comma + proof |
| /api/v1/comma/verify | GET | Verify 531441/524288 numerically |
| /api/v1/structures | GET | List verified ancient structures |
| /api/v1/structure/analyze | POST | Analyze any structure's harmonic ratios |
| /api/v1/serenal/check | GET | Serenal Framework consistency |
| /api/v1/temple/simulate | POST | Simulate room acoustics (JSON: cubits, type, mode) |

## Try

```bash
# Verify the Pythagorean comma
curl http://localhost:5002/api/v1/comma/verify

# Analyze the Great Pyramid
curl -X POST http://localhost:5002/api/v1/structure/analyze \
  -H Content-Type:application/json \
  -d '{"name":"pyramid","dimensions":{"base":440,"height":280}}'

# Simulate Solomon's Temple acoustics (royal cubit)
curl -X POST http://localhost:5002/api/v1/temple/simulate \
  -H Content-Type:application/json \
  -d '{"cubits":20,"type":"royal","mode":"acoustics"}'
```
