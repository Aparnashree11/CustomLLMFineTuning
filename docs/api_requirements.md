# API Requirements (MVP)

| Page | Endpoint | Method | Request | Response |
|------|----------|--------|---------|----------|
| Login | /auth/login | POST | { email, password } | { accessToken, refreshToken, user } |
| Datasets List | /datasets | GET | ?cursor=&limit=&language= | { items: Dataset[], nextCursor } |
| Dataset Upload | /datasets/upload | POST (multipart) | file[], language | Dataset |
| Dataset Details | /datasets/{id} | GET | path id | Dataset & { versions, preview[] } |
| Preprocess | /datasets/{id}/preprocess | POST | path id | { jobId } |
| Training Config | /training/configure | POST | TrainingConfig | TrainingConfig |
| Start Job | /training/jobs | POST | { configId } | { jobId } |
| Jobs List | /training/jobs | GET | ?status= | { items: Job[], nextCursor } |
| Job Details | /training/jobs/{id} | GET | path id | JobDetail |
| Models List | /models | GET | — | { items: Model[], nextCursor } |
| Model Details | /models/{id} | GET | path id | Model (TBD extras) |
| Inference | /inference/generate | POST | { prompt, temperature?, top_p?, max_tokens? } | { output, tokens, latencyMs } |

**Error shape (uniform)**
```json
{ "error": { "code": "STRING", "message": "Readable message", "details": {}, "requestId": "uuid" } }
