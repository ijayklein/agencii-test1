# Vibe Coding Skinny Instructions

This lightweight workflow is for **fast prototyping** with Agency Swarm. 
Use it when you just want to test ideas quickly without the full PRD + folder structure overhead.

---

## Step 1: Setup

1. Create or unzip a starter folder (see vibe-agency-starter.zip example).
2. Install requirements:

```bash
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
```

3. Copy the env file if needed:
```bash
cp .env.example .env
```

---

## Step 2: Quick Tool Drafting

- Keep all tools in **tools.py** for speed.
- Each tool should be atomic and runnable without mocks.
- Use `if __name__ == "__main__":` at the bottom of tools.py for smoke tests.

Example pattern:

```python
class EchoTool(BaseTool):
    text: str
    def run(self):
        return self.text
```

Run quick tests with:
```bash
python tools.py
```

---

## Step 3: Lightweight Agents

- Define agents in `agents/` with **inline instructions**. 
- Don’t bother with `instructions.md` files yet.
- Keep descriptions short and practical.

Example:
```python
agentA = Agent(
    name="Planner",
    description="Plans tasks",
    instructions="You plan step-by-step. Keep responses short.",
    tools_folder="./"
)
```

---

## Step 4: Agency Wiring

- Use `agency.py` to wire your agents. 
- Start with minimal communication flows (A ↔ B).

Run the demo:
```bash
python agency.py
```

---

## Step 5: Iterate Fast

Loop:
1. Edit `tools.py` or an agent file.
2. Run `python tools.py` for quick checks.
3. Run `python agency.py` to see changes live.

Keep cycles short (minutes, not hours).

---

## Step 6: Graduate Later

When the idea feels solid:
- Expand to full PRD.
- Split tools into per-agent folders.
- Add validation, tests, and `instructions.md` files.
- Define proper communication flows and shared instructions.

---

✅ Use this skinny version when you want to **vibe-test ideas fast** without bureaucracy.
