# FNU Tushar

Brooklyn, New York, United States

[tushardzig@gmail.com](mailto:tushardzig@gmail.com) | [Website](https://tushar-6666.vercel.app/) | [GitHub](https://github.com/gpu004) | [LinkedIn](https://www.linkedin.com/in/dahiya-tushar/)

[Download the resume PDF](basic/resume.pdf)

## Experience

**Instructor and Grader, Advanced Database Systems**, New York University | September 2026 - December 2026

New York, NY

- Taught graduate students to execute and analyze time-series queries using AQuery and q/kdb+, and reproduce database experiments with ReproZip.
- Reviewed and graded graduate-level database assignments and projects, evaluating query performance, indexing strategies, transaction processing, and distributed system implementations.

**Software Developer**, Qdata, Sirius Holdings | April 2025 - May 2026

Abu Dhabi, UAE

- Built and tested automated trading strategies for dozens of MetaTrader 5 accounts, with multi-leg position management, configurable execution rules, and dashboards for monitoring trades.
- Automated the deployment of 1,000+ concurrent AWS ECS workers using Terraform and connected them to on-premises servers over VPN, keeping restricted data on local infrastructure.
- Optimized SHA-256 CNF generation and SAT solvers in C++11/17, and built distributed worker coordination using CORBA/OmniORB for parallel computation.

**Independent Software Consultant**, Confidential Fintech Client | January 2026 - July 2026

Abu Dhabi, UAE

- Developed reinforcement-learning environments in Harbor, implementing task definitions, reward functions, and evaluation pipelines for training and evaluating OpenAI and Anthropic models.
- Built end-to-end marketplaces for a fintech platform focused on the financialization and trading of real-world assets.

**Backend and Data Engineer**, Zator | December 2024 - March 2025

- Developed data streaming pipelines in Go and Rust to ingest JSON and Protobuf data from APIs and Solana RPC.
- Built Kafka streaming workflows with custom producers and consumers for real-time data filtering and processing.

**Young Research Fellow**, IIIT Hyderabad IHub | July 2024 - November 2024

- Built a real-time IoT system to collect sensor data with MQTT, Fastify, and SQLite and display machine learning results in interactive visualizations.
- Researched and implemented on-device ML inference in React Native using a custom ML Kit wrapper, react-native-fast-tflite for TensorFlow Lite, and onnx-runtime-react-native for ONNX.

## Education

**Master of Science in Computer Science**, New York University | September 2026 - May 2028

**Bachelor of Engineering in Information Science and Engineering**, National Institute of Engineering, Mysore | January 2021 - August 2024

## Skills

- Programming languages: Python, Go, Rust, TypeScript, SQL, OCaml
- Frameworks and libraries: PyTorch, React Native, Fastify, ML Kit, TensorFlow Lite, ONNX Runtime
- Performance analysis: GPU roofline modeling, microbenchmarking, SIMD optimization
- Databases: SQLite, Postgres, ClickHouse, q/kdb+, TigerBeetle
- Tools and software: Kafka, Docker, Terraform, MT5, CORBA, OmniORB, Cargo
- Cloud platforms: AWS: EC2, ECS, ECR, S3, IAM, VPC, VPN, Lambda, CloudWatch. Cloudflare: R2, Workers. Modal.

## Projects

**[GPU Napkin Math](https://github.com/gpu004/napkin-math-gpu)**

- Built a Rust CLI for GPU roofline estimates and LLM prefill/decode analysis, modeling FLOPs, HBM traffic, KV-cache capacity, transfer latency, and multi-GPU memory fit.
- Added GPU cost modeling with utilization, startup and idle time, billing increments, and dated cloud prices to compare workload cost and tokens per dollar.
- Built Rust/CUDA microbenchmarks on Modal for A100, H100, B200, and B300; measured 1.82 PFLOP/s dense BF16 GEMM and 6.49 TB/s HBM copy bandwidth on B300, with correctness checks and separate vendor ceilings.

**[VLIW/SIMD Kernel Optimization](https://github.com/gpu004/original_performance_takehome)**

- Optimized Anthropic's simulated tree-traversal kernel from 147,734 to 2,910 cycles, a 50.8x speedup, using eight SIMD streams, register-resident state, software pipelining, and fused multiply-add instructions.
- Verified output correctness against the unchanged upstream frozen simulator and documented optimization steps and remaining gather-load bottlenecks.

**Monkey Compiler**

- Built an interpreter in Go with no external dependencies, supporting integers, booleans, functions, closures, conditionals, and lexical scoping.
