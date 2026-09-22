
**One stage to build application and another stage to run it**

* Build tools are needed to create the app, but usually are not needed to run it

#### Without multi stage

```
Docker Image
├── Application
├── Compiler
├── Build tools
├── Source code
└── Dependencies
```

#### With multi stage

```
Stage 1: BUILD
├── Source code
├── Compiler
├── Build tools
└── Build application
          ↓
        COPY
          ↓
Stage 2: RUNTIME
├── Application
└── Runtime dependencies
```

