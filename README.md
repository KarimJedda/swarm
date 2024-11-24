
# Swarm (experimental, educational)

OpenAI fork, with pinned dependencies and made to work with Python 3. Highly experimental. 

## Install

Requires Python 3+

```shell
pip install git+ssh://git@github.com/KarimJedda/swarm.git
```

or

```shell
pip install git+https://github.com/KarimJedda/swarm.git
```

## Usage

```python
from swarm import Swarm, Agent

client = Swarm()

def transfer_to_agent_b():
    return agent_b


agent_a = Agent(
    name="Agent A",
    instructions="You are a helpful agent.",
    functions=[transfer_to_agent_b],
)

agent_b = Agent(
    name="Agent B",
    instructions="Only speak in Haikus.",
)

response = client.run(
    agent=agent_a,
    messages=[{"role": "user", "content": "I want to talk to agent B."}],
)

print(response.messages[-1]["content"])
```

```
Hope glimmers brightly,
New paths converge gracefully,
What can I assist?
```

OG repo here: https://github.com/openai/swarm


# Work with local OpenWebUI 

You can customize any model that runs behind the scenes. 

This opens up further tool use and cross model swarms. 

```
from openai import OpenAI
from swarm import Swarm, Agent

# localhost:3000 has an OpenWebUI instance running
openai_api = OpenAI(
    base_url="http://localhost:3000/api/", 
    api_key="XXXX"
)

client = Swarm(client=openai_api)

def transfer_to_agent_b():
    return agent_b


agent_a = Agent(
    name="Agent A",
    instructions="You are a helpful agent.",
    functions=[transfer_to_agent_b],
)

agent_b = Agent(
    name="Agent B",
    instructions="Only speak in Haikus.",
)

response = client.run(
    agent=agent_a,
    messages=[{"role": "user", "content": "I want to talk to agent B."}],
)

print(response.messages[-1]["content"])
```

# Core Contributors

- Ilan Bigio - [ibigio](https://github.com/ibigio)
- James Hills - [jhills20](https://github.com/jhills20)
- Shyamal Anadkat - [shyamal-anadkat](https://github.com/shyamal-anadkat)
- Charu Jaiswal - [charuj](https://github.com/charuj)
- Colin Jarvis - [colin-openai](https://github.com/colin-openai)
- Katia Gil Guzman - [katia-openai](https://github.com/katia-openai)
