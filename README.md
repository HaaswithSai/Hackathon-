# MAC-Bench: Multi-Agent Coordination Benchmark

MAC-Bench is a comprehensive evaluation framework designed to test the coordination, negotiation, and reasoning capabilities of multi-agent systems. Single-agent benchmarks are blind to failure modes like echo chambers, information siloing, and role drift. MAC-Bench forces agents into coordination bottlenecks and rigorously classifies their failures.

## Architecture

MAC-Bench consists of three primary layers:
1. **Task Suites**: 50 highly asymmetric tasks across three archetypes (DPIP, Adversarial Scheduling, Cooperative Merge) guaranteeing single-agent failure.
2. **Orchestration Harness**: A Docker-isolated environment wrapping multi-agent frameworks (AutoGen, CrewAI, LangGraph) with an HTTP Interceptor Proxy that records an immutable transcript of every token and tool call.
3. **Evaluation Swarm**: A hybrid programmatic and LLM-as-a-judge system mapping runs to the 14-mode Multi-Agent System Taxonomy (MAST) of failures.

## Getting Started

1. Set up your environment:
```bash
cp .env.example .env
# Edit .env with your API keys
pip install -e ".[dev]"
```

2. Start the interceptor proxy in the background:
```bash
python -m harness.interceptor_proxy
```

3. Run a specific framework against a task:
```bash
mac-bench tasks/dpip.py --framework autogen --model gpt-4o
```

## Reading Transcripts & Results
- Raw execution traces are saved to `transcripts/raw/`.
- The evaluation swarm can be executed over these traces via the `detectors.aggregator` to generate the final Leaderboard Failure Heatmaps.
"# Hackathon-" 
