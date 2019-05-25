# OMS testing setup

This is a repository which hosts TeamCity setup for OMS

#### What's inside?

- TeamCity server
- 3 TeamCity agents
- PostgreSQL server (required by some test setups)

#### How do I start this?

```bash
docker network create teamcity # for creating network for these containers
docker-compose up -d           # to get it running
```

#### How TeamCity works
There are 2 types of software that are required to run TeamCity:
- TeamCity server - the server, which schedules tasks and exposes the frontend to the user
- TeamCity agent - the agent, where the tasks are actually run

TeamCity agents and server can be run at 2 different machines, if needed (in this setup they are run on the same machine).  
Also TeamCity free version (the one used here) allows to have 3 build agents and 100 build configurations, which should be way more tham enough.

#### Containers list
- **teamcity-server** - the actual server
- **teamcity-agent-X** (x = [1;3]) - TeamCity agents (built from the same `agent/Dockerfile`). Based on `teamcity-minimal-agent`, but with Node.js pre-installed
- `postgres` - used by some test setups.

#### Folders structure
- `agent/` - stores Dockerfile for TeamCity agent
- `data/` - stores configuration for everything (TeamCity agents, TeamCity server, PostgreSQL). Is under `.gitignore`
- `data/teamcity-server/data/plugins` - a folder to put `.zip` plugins for TeamCity. The server needs to be restarted to accept plugins.

#### Maintainers
This repository is created and maintained by [Sergey Peshkov](https://github.com/serge1peshcoff). Any contribution is welcome!