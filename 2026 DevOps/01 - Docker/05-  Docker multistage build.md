
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

### Hands on:

```
1. Create folder and tiny app
2. Build the FAT way first -- Single stage --> Measure size
3. Rewrite multi stage --> Measure size
4. Compare the two sizes side by side
5. Run the small image --> Prove it still works
```

