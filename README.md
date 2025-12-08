<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Reinforcement Learning for Agentic AI Systems - README</title>
</head>
<body>

<h1>Reinforcement Learning for Agentic AI Systems</h1>
<h2>Take-Home Final – Northeastern University</h2>
<h3>Author: <b>Nithin Yash Menezes</b></h3>
<hr>

<h2>🎯 Project Overview</h2>
<p>
This project implements a <b>Reinforcement Learning–powered Agentic AI Research Workflow System</b>.
The goal is to enable autonomous agents to learn through experience and optimize:
</p>

<ul>
    <li>Which information sources to query</li>
    <li>When to keep searching</li>
    <li>When to summarize and stop</li>
    <li>How to balance quality vs. computational cost</li>
</ul>

<p>The system uses:</p>
<ul>
    <li><b>Q-Learning</b> – workflow decision-making</li>
    <li><b>UCB1 Bandit</b> – best source selection</li>
    <li><b>Agent-based orchestration</b></li>
</ul>

<p>This creates an adaptive, self-improving research agent.</p>

<hr>

<h2>🧠 Core Idea</h2>
<p>Traditional workflows are static. This system replaces them with a learning controller:</p>

<table border="1" cellpadding="8">
<tr><th>Component</th><th>Learns</th></tr>
<tr><td>Q-Learning</td><td>Best action (search_more / summarize / stop)</td></tr>
<tr><td>UCB1 Bandit</td><td>Best information source</td></tr>
<tr><td>Reward Function</td><td>Balance of quality and cost</td></tr>
</table>

<hr>

<h2>🏗️ System Architecture</h2>

<pre>
User Task Input
        ↓
RL Controller (Q-Learning + UCB Bandit)
        ↓                     ↓
 Search Agent → Sources (Wiki / Blogs / Scholar / News)
        ↓
 Summarizer Agent
        ↓
 Reward Computation (Quality – Cost)
        ↓
Q-Table & UCB Update
        ↺ (feedback loop)
</pre>

<hr>

<h2>📁 Project Structure</h2>

<pre>
rl_agentic_final_latest/
│
├── src/
│   ├── main.py                # RL training pipeline
│   ├── main_fixed.py          # Baseline system (no learning)
│   ├── agents.py              # Agents + RL Controller 
│   ├── bandit.py              # UCB1 implementation
│   ├── qlearning.py           # Q-Learning implementation
│   ├── environment.py         # Reward model + environment logic
│   ├── plot_learning_curve.py # Matplotlib learning plots
│   └── app.py                 # Streamlit interactive dashboard
│
├── logs/
│   ├── rl_metrics.csv         # Logged episode rewards + searches
│   ├── learning_curve_reward.png
│   └── learning_curve_searches.png
│
├── tasks.json                 # Task dataset (3 tasks)
├── requirements.txt           # Dependencies
└── README.md                  # This file
</pre>

<hr>

<h2>⚙️ Installation</h2>

<h3>1️⃣ Clone Repository</h3>
<pre>git clone &lt;your-repo-url&gt;
cd rl_agentic_final_latest</pre>

<h3>2️⃣ Create Virtual Environment</h3>
<pre>python3 -m venv env
source env/bin/activate</pre>

<h3>3️⃣ Install Dependencies</h3>
<pre>pip install -r requirements.txt</pre>

<hr>

<h2>▶️ Running the System</h2>

<h3>Baseline (No RL)</h3>
<pre>python3 -m src.main_fixed</pre>

<h3>RL Agent (Q-Learning + UCB)</h3>
<pre>python3 -m src.main</pre>

<p>Produces:</p>
<ul>
    <li>Episode rewards</li>
    <li>Episode searches</li>
    <li>rl_metrics.csv</li>
</ul>

<hr>

<h2>📊 Generate Learning Curves</h2>

<pre>python3 -m src.plot_learning_curve</pre>

<p>Creates:</p>
<ul>
    <li>learning_curve_reward.png</li>
    <li>learning_curve_searches.png</li>
</ul>

<hr>

<h2>📺 Streamlit Dashboard</h2>

<pre>streamlit run src/app.py</pre>

<p>The dashboard shows:</p>
<ul>
    <li>Reward learning curve</li>
    <li>Search-efficiency curve</li>
    <li>Episode metrics</li>
</ul>

<hr>

<h2>🧪 Experimental Setup</h2>

<table border="1" cellpadding="8">
<tr><th>Parameter</th><th>Value</th></tr>
<tr><td>Episodes</td><td>50</td></tr>
<tr><td>Learning Rate</td><td>0.1</td></tr>
<tr><td>Discount Factor</td><td>0.9</td></tr>
<tr><td>Max Searches</td><td>3</td></tr>
<tr><td>Exploration</td><td>UCB1 Bandit</td></tr>
<tr><td>Tasks</td><td>3 research questions</td></tr>
</table>

<hr>

<h2>📈 Results Summary</h2>

<h3>1. Reward Learning Curve</h3>
<ul>
    <li>Rewards increase over time</li>
    <li>Shows convergence of Q-Learning</li>
</ul>

<h3>2. Search Efficiency</h3>
<ul>
    <li>Searches stabilize to ~1.5–2.3 per episode</li>
    <li>Indicates improved workflow</li>
</ul>

<h3>3. Baseline vs RL</h3>
<table border="1" cellpadding="8">
<tr><th>Metric</th><th>Baseline</th><th>RL System</th></tr>
<tr><td>Adaptation</td><td>No</td><td>Yes</td></tr>
<tr><td>Source Selection</td><td>Fixed</td><td>Adaptive</td></tr>
<tr><td>Workflow Decisions</td><td>Hardcoded</td><td>Learned</td></tr>
<tr><td>Performance</td><td>Medium</td><td><b>High</b></td></tr>
</table>

<hr>

<h2>🧠 Mathematical Formulation</h2>

<h3>Q-Learning</h3>
<pre>
Q(s,a) ← Q(s,a) + α [r + γ max Q(s’,a’) – Q(s,a)]
</pre>

<h3>UCB1</h3>
<pre>
UCB = avg reward + sqrt(2 ln N / n)
</pre>

<hr>

<h2>🛠️ Technologies Used</h2>
<ul>
    <li>Python</li>
    <li>Q-Learning</li>
    <li>UCB Bandit</li>
    <li>Streamlit</li>
    <li>Matplotlib</li>
    <li>JSON tasks</li>
</ul>

<hr>

<h2>🔮 Future Work</h2>
<ul>
    <li>Add PPO / REINFORCE</li>
    <li>Multi-Agent RL</li>
    <li>Real web search APIs</li>
    <li>RLHF (Human Feedback)</li>
    <li>Transfer learning</li>
</ul>

<hr>

<h2>👤 Author</h2>
<p><b>Nithin Yash Menezes</b><br>
MS in Information Systems<br>
Northeastern University (2024–2026)</p>

<hr>

<h2>📘 License</h2>
<p>This project is submitted for the <b>Take-Home Final: Reinforcement Learning for Agentic AI Systems</b> course.</p>

</body>
</html>
