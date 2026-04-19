project-root/
│
├── app/                        # Código principal
│   ├── main.py                 # Entrypoint FastAPI
│   │
│   ├── api/                   # Endpoints REST
│   │   ├── routes/
│   │   │   ├── comidas.py
│   │   │   ├── alimentos.py
│   │   │   └── salud.py
│   │   └── deps.py            # Dependencias (DB, auth, etc.)
│   │
│   ├── core/                  # Configuración global
│   │   ├── config.py
│   │   └── security.py
│   │
│   ├── models/                # Modelos DB (ORM)
│   │   ├── alimento.py
│   │   ├── comida.py
│   │   └── comida_detalle.py
│   │
│   ├── schemas/               # Pydantic (request/response)
│   │   ├── alimento.py
│   │   ├── comida.py
│   │   └── calculo.py
│   │
│   ├── services/              # Lógica de negocio
│   │   ├── calculo_insulina.py
│   │   ├── hidratos.py
│   │   └── analisis.py
│   │
│   ├── db/                    # DB setup
│   │   ├── session.py
│   │   ├── base.py
│   │   └── init_db.py
│   │
│   ├── llm/                   # Integración IA
│   │   ├── client.py          # LiteLLM wrapper
│   │   ├── prompts.py
│   │   └── analyzer.py
│   │
│   └── utils/                 # Helpers
│       ├── logger.py
│       └── constants.py
│
├── tests/                     # Tests
│   ├── test_calculo.py
│   └── test_api.py
│
├── docker/                    # Config Docker
│   ├── api.Dockerfile
│   ├── ollama.Dockerfile (opcional)
│   └── mysql/
│       └── init.sql
│
├── docker-compose.yml         # Orquestación
├── .env                       # Variables de entorno
├── .env.example               # Template
│
├── scripts/                   # Scripts útiles
│   ├── seed_data.py
│   └── backup.sh
│
├── migrations/                # Alembic (si usás)
│
├── docs/                      # Documentación
│   ├── arquitectura.md
│   └── decisiones.md
│
├── README.md
└── requirements.txt / pyproject.toml