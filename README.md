# Line-Based Payload API
FastAPI service to parse a single multiline payload (header, body rows, trailer).
Validates format, stores payloads and records in SQLite (`records.db`) with SQLAlchemy.
Response includes overall status and per-line errors for invalid body rows.

**Docs:** visit `/docs` or `/redoc` after starting the server.
**Endpoint:** `POST /interface/001` with JSON `{ "payload": "<multiline text>" }`.
**Header line:** `1|<Amount>|<Timestamp>` where Amount > 0 and Timestamp `YYYY-MM-DD HH:MM:SS`.
**Body line:** `2|<Title>|<Author>[|<PublishDate>]` with Title, Author required.
**PublishDate:** optional, must be `YYYY-MM-DD` if present.
**Trailer line:** `99|<BodyCount>`; BodyCount must equal the number of body lines.
