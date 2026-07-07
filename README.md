multi-env-webapp/
│
├── app/
│   ├── index.html
│   └── Dockerfile
│
├── helm/
│   └── webapp/
│       ├── Chart.yaml
│       ├── values.yaml
│       ├── values-dev.yaml
│       ├── values-prod.yaml
│       └── templates/
│            ├── deployment.yaml
│            ├── service.yaml
│            ├── ingress.yaml
│            ├── configmap.yaml
│            └── _helpers.tpl
│
└── README.md
