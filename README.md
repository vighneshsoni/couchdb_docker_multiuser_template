# CouchDB Multiuser Docker Template

This repository is a **template to quickly launch a CouchDB multiuser container** with:

- Automatic creation of `_users` and `_replicator` databases
- Enabling `couch_peruser` **after the creation of \_users database**
- Variables in `.env`

## 📁 Repository Structure

```text
.
├── docker-compose.yml       # Defines CouchDB container and init container
├── config/
│   └── local.ini            # CouchDB configuration
├── .env.example             # Environment variables template
└── README.md
```

## Usefull commands:

**Launch container**

```
docker compose up -d
```

\
**Delete containers and volumes**

```
docker compose down -v
```

## Verifications

**Check databases**

```bash
curl -u username:password http://localhost:5984/_all_dbs
```

**expected output:**

```json
["_replicator", "_users"]
```

\
**Check `couch_peruser` configuration:**

```bash
curl -u username:password http://localhost:5984/_node/_local/_config/couch_peruser
```

**expected output:**

```json
{
  "enable": "true",
  "delete_dbs": "true"
}
```
## Web Interface (Fauxton)
You can find the CouchDB web interface (Fauxton) at `http://localhost:5984/_utils/` or at the port you configured.
