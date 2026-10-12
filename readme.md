# FNU Tushar

Brooklyn, New York, United States

[tushardzig@gmail.com](mailto:tushardzig@gmail.com) | [Website](https://tushar-6666.vercel.app/) | [GitHub](https://github.com/gpu004) | [LinkedIn](https://www.linkedin.com/in/dahiya-tushar/)

[Download the resume PDF](basic/resume.pdf)

## Experience

**Instructor and Grader, Advanced Database Systems**, New York University | September 2026 - December 2026

New York, NY

- Led technical sessions for graduate students on AQuery, q/kdb+, and ReproZip, covering query execution, time-series data processing, and reproducible database experiments.
- Supported students with database-system assignments and projects involving transaction processing, performance tuning, indexing, and distributed systems.

**Software Developer**, Qdata, Sirius Holdings | April 2025 - May 2026

Abu Dhabi, UAE

- Implemented and tested custom MT5 trading algorithms; managed dozens of accounts with dashboards, automated multi-leg position management, and configurable execution and exit strategies.
- Built custom Terraform automation for 1,000+ concurrent AWS ECS workers and VPN connectivity between AWS and local servers, keeping restricted data on local servers.
- Optimized C++11 and C++17 SAT solvers and CNF generation; built SHA-256 and CORBA/OmniORB distributed systems.

**Independent Software Consultant**, Confidential Fintech Client | January 2026 - July 2026

Abu Dhabi, UAE

- Developed end-to-end marketplaces for a platform for the financialization and trading of real-world assets.
- Developed custom reinforcement-learning environments in Harbor, including task definitions, reward logic, and evaluation workflows for training and evaluating OpenAI and Anthropic models.

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

- Built a Python roofline estimator and interactive Astro dashboard to model GPU compute, HBM traffic, host transfers, peer copies, kernel overhead, and memory capacity.
- Calibrated the estimator with PyTorch microbenchmarks on two Modal H100 SXM GPUs; recorded 717 TFLOP/s dense BF16 GEMM and 3.00 TB/s HBM copy bandwidth. Distinguished measured H100 results from vendor ceilings for B200/B300.

**[VLIW/SIMD Kernel Optimization](https://github.com/gpu004/original_performance_takehome)**

- Optimized Anthropic's simulated tree-traversal kernel from 147,734 to 2,910 cycles, a 50.8x speedup, using eight SIMD streams, register-resident state, software pipelining, and fused multiply-add instructions.
- Verified output correctness against the unchanged upstream frozen simulator and documented optimization steps and remaining gather-load bottlenecks.

**Monkey Compiler**

- Built an interpreter in Go with no external dependencies, supporting integers, booleans, functions, closures, conditionals, and lexical scoping.
