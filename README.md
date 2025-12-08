<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">

</head>
<body>

<h1>Reinforcement Learning for Agentic AI Systems</h1>
<h2>Take-Home Final – Northeastern University</h2>
<h3><strong>Author: Nithin Yash Menezes</strong></h3>
<hr>

<h2>🎯 Project Overview</h2>
<p>
This project implements a <strong>Reinforcement Learning–powered Agentic AI Research Workflow System</strong>.
The goal is to enable autonomous agents to learn through experience and optimize:
</p>
<ul>
  <li>Which information sources to query</li>
  <li>When to keep searching</li>
  <li>When to summarize and stop</li>
  <li>How to balance quality vs. computational cost</li>
</ul>

<p>The final system uses:</p>
<ul>
  <li><strong>Q-Learning</strong> (workflow decision-making)</li>
  <li><strong>UCB1 Bandit</strong> (best source selection)</li>
  <li><strong>Agent orchestration</strong> (Search Agent + Summarizer Agent + RL Controller)</li>
</ul>

<hr>

<h2>🧠 Core Idea</h2>
<p>Traditional agent workflows are static and rule-based. This project replaces static logic with an <strong>RL Controller</strong> that improves over time.</p>

<table border="1" cellpadding="6" cellspacing="0">
  <tr>
    <th>Component</th>
    <th>Learns</th>
  </tr>
  <tr>
    <td>Q-Learning</td>
    <td>Best workflow action</td>
  </tr>
  <tr>
    <td>UCB1 Bandit</td>
    <td>Best information source</td>
  </tr>
  <tr>
    <td>Reward Function</td>
    <td>Balance accuracy &amp; efficiency</td>
  </tr>
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
│   ├── rl_metrics.csv
│   ├── learning_curve_reward.png
│   └── learning_curve_searches.png
│
├── tasks.json
├── requirements.txt
└── README.md
</pre>

<hr>

<h2>⚙️ Installation</h2>

<h3>1️⃣ Clone the Repository</h3>
<pre>git clone &lt;your-repo-url&gt;
cd rl_agentic_final_latest</pre>

<h3>2️⃣ Create Virtual Environment</h3>
<pre>python3 -m venv env
source env/bin/activate</pre>

<h3>3️⃣ Install Dependencies</h3>
<pre>pip install -r requirements.txt</pre>

<hr>

<h2>▶️ Running the System</h2>

<h3>Run Baseline (Non-RL Pipeline)</h3>
<pre>python3 -m src.main_fixed</pre>

<h3>Run Reinforcement Learning (Q-Learning + UCB)</h3>
<pre>python3 -m src.main</pre>

<p>Outputs:</p>
<ul>
  <li>Episode rewards</li>
  <li>Average searches</li>
  <li><code>rl_metrics.csv</code></li>
</ul>

<hr>

<h2>📊 Generate Learning Curves</h2>

<pre>python3 -m src.plot_learning_curve</pre>

<p>Creates images inside <code>logs/</code>:</p>
<ul>
  <li><code>learning_curve_reward.png</code></li>
  <li><code>learning_curve_searches.png</code></li>
</ul>

<hr>

<h2>📺 Running the Streamlit Dashboard (Important Section)</h2>

<h3>Launch the dashboard:</h3>
<pre>streamlit run src/app.py</pre>

<p>When you run this, Streamlit shows a standard onboarding message:</p>

<pre>
👋 Welcome to Streamlit!

If you'd like to receive helpful onboarding emails, news, offers, promotions,
and the occasional swag, please enter your email address below. Otherwise,
leave this field blank.

Email:  mark2pm@gmail.com
</pre>

<h3>LibreSSL Warning on macOS</h3>
<p>You may see a warning like:</p>

<pre>
/Users/.../urllib3/__init__.py:35: NotOpenSSLWarning:
urllib3 v2 only supports OpenSSL 1.1.1+, currently the 'ssl' module is compiled
with 'LibreSSL 2.8.3'. See: https://github.com/urllib3/urllib3/issues/3020
</pre>

<p>This is expected on macOS and does <strong>not</strong> affect the project.</p>

<h3>Streamlit Privacy Notice</h3>
<pre>
Summary:
- This open source library collects usage statistics.
- Streamlit cannot see and does not store the content inside your app
  (text, charts, images, etc.).
- Telemetry data is stored on servers in the United States.

To opt out, create or edit:
~/.streamlit/config.toml

[browser]
gatherUsageStats = false
</pre>

<h3>Streamlit App URLs</h3>
<pre>
You can now view your Streamlit app in your browser.

Local URL: http://localhost:8501
Network URL: http://10.0.0.174:8501
</pre>

<p>Open the <strong>Local URL</strong> in your browser to view:</p>
<ul>
  <li>Reward learning curve</li>
  <li>Policy efficiency curve</li>
  <li>Episode metrics table</li>
</ul>

<h3>Optional: Enable Faster Refresh (Watchdog)</h3>
<p>For better performance, you can install Watchdog:</p>
<pre>
xcode-select --install
pip install watchdog
</pre>

<hr>

<h2>🧪 Experimental Setup</h2>

<table border="1" cellpadding="6" cellspacing="0">
  <tr>
    <th>Parameter</th>
    <th>Value</th>
  </tr>
  <tr>
    <td>Episodes</td>
    <td>50</td>
  </tr>
  <tr>
    <td>Learning Rate</td>
    <td>0.1</td>
  </tr>
  <tr>
    <td>Discount Factor</td>
    <td>0.9</td>
  </tr>
  <tr>
    <td>Max Searches</td>
    <td>3</td>
  </tr>
  <tr>
    <td>Exploration</td>
    <td>UCB1 Bandit</td>
  </tr>
  <tr>
    <td>Tasks</td>
    <td>3 research prompts</td>
  </tr>
</table>

<hr>

<h2>📈 Results Summary</h2>

<h3>1. Reward Learning Curve</h3>
<ul>
  <li>Rewards increase steadily over episodes</li>
  <li>Shows policy improvement and Q-Learning convergence</li>
</ul>

<h3>2. Search Efficiency Curve</h3>
<ul>
  <li>Average searches stabilize at approximately 1.5–2.3</li>
  <li>Indicates improved workflow and less redundant searching</li>
</ul>

<h3>3. Baseline vs RL Comparison</h3>
<table border="1" cellpadding="6" cellspacing="0">
  <tr>
    <th>Metric</th>
    <th>Baseline</th>
    <th>RL System</th>
  </tr>
  <tr>
    <td>Adaptation</td>
    <td>None</td>
    <td>Learns over time</td>
  </tr>
  <tr>
    <td>Source Selection</td>
    <td>Fixed</td>
    <td>Adaptive (UCB)</td>
  </tr>
  <tr>
    <td>Workflow Decisions</td>
    <td>Hardcoded</td>
    <td>Learned policy</td>
  </tr>
  <tr>
    <td>Performance</td>
    <td>Medium</td>
    <td><strong>High</strong></td>
  </tr>
</table>

<hr>

<h2>🧠 RL Math (Short Version)</h2>

<h3>Q-Learning</h3>
<pre>
Q(s,a) ← Q(s,a) + α [r + γ max Q(s’,a’) – Q(s,a)]
</pre>

<h3>UCB1</h3>
<pre>
UCB = average_reward + sqrt(2 ln N / n)
</pre>

<hr>

<h2>🛠️ Technologies Used</h2>
<ul>
  <li>Python</li>
  <li>Q-Learning (value-based RL)</li>
  <li>UCB Multi-Armed Bandit</li>
  <li>Streamlit</li>
  <li>Matplotlib</li>
  <li>JSON-based task dataset</li>
</ul>

<hr>

<h2>🔮 Future Enhancements</h2>
<ul>
  <li>Add PPO or REINFORCE (policy gradient methods)</li>
  <li>Introduce multi-agent RL extensions</li>
  <li>Integrate real web search APIs</li>
  <li>Use RLHF (Reinforcement Learning from Human Feedback)</li>
  <li>Apply transfer learning to new domains</li>
</ul>

<hr>

<h2>👤 Author</h2>
<p>
<strong>Nithin Yash Menezes</strong><br>
MS in Information Systems<br>
Northeastern University
</p>

<hr>

<h2>📘 License</h2>
<p>
This project is part of the <strong>Take-Home Final: Reinforcement Learning for Agentic AI Systems</strong> assignment.
It is intended for academic use only.
</p>

</body>
</html>
