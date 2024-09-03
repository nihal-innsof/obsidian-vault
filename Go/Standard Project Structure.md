---
id: Standard Project Structure
aliases: []
tags: []
---

# 1. [Github link](https://medium.com/@rayato159/how-to-implement-clean-architecture-in-golang-en-f50d66378ebf)

```zsh
📂config/
├─ 📄config.go
📂server/
├─ 📄echoServer.go
├─ 📄server.go -> interface
📂database/
├─ 📄database.go -> interface
├─ 📄postgres.go
📂cockroach/
├─ 📂tests/
│  ├─ 📄cockroach..._test.go -> need to add _test.go at the end of the file
├─ 📂migrations/
│  ├─ 📄cockroachMigration.go
│  📂entities/
│  ├─ 📄cockroachEntitiy.go
├─ 📂models/
│  ├─ 📄cockroachModel.go
├─ 📂handlers/
│  ├─ 📄cockroachHandler.go -> interface
│  ├─ 📄cockroachHttp.go
│  ├─ 📄cockroachResponse.go
├─ 📂usecases/
│  ├─ 📄cockroachUsecase.go -> interface
│  ├─ 📄cockroachUsecaseImpl.go
├─ 📂repositories/
│  ├─ 📄cockroachRepository.go -> interface
│  ├─ 📄cockroachMessaging.go -> interface
│  ├─ 📄cockroachPostgresRepository.go
│  ├─ 📄cockroachFCMMessaging.go
📄main.go
📄config.yaml
```
