# n8n Zero to Hero

A comprehensive guide to mastering n8n workflow automation from the basics to advanced implementations.

## What is n8n?

[n8n](https://n8n.io/) is a powerful, open-source workflow automation tool that allows you to connect different services and automate tasks without writing code. It's designed to be both powerful for developers and accessible for non-technical users.

### Key Features

- **Visual Workflow Builder**: Drag-and-drop interface for creating complex workflows
- **200+ Built-in Nodes**: Connect to popular services like Slack, GitHub, Google Sheets, and more
- **Self-Hosted**: Run n8n on your own infrastructure for complete data control
- **Open Source**: Free to use and modify under the Apache 2.0 license
- **Webhook Support**: Trigger workflows via HTTP requests
- **Scheduling**: Run workflows on a schedule using cron expressions
- **Error Handling**: Built-in retry mechanisms and error handling
- **Data Transformation**: Powerful tools for manipulating data between nodes

### Use Cases

- **Data Synchronization**: Sync data between different applications
- **API Integration**: Connect multiple APIs and services
- **Notification Systems**: Send alerts and notifications across platforms
- **Data Processing**: Transform and process data automatically
- **Task Automation**: Automate repetitive business processes
- **Web Scraping**: Extract data from websites and process it

## Workflows vs Agents in n8n

Understanding the difference between workflows and agents is crucial for effective n8n usage:

### Workflows

**Workflows** are the traditional n8n automation sequences that you create using the visual editor. They are:

- **Linear and Sequential**: Execute nodes in a predefined order
- **Trigger-Based**: Started by specific events (webhooks, schedules, manual triggers)
- **Deterministic**: Follow a predictable path based on conditions
- **Batch Processing**: Handle multiple items in a single execution
- **Error Handling**: Built-in retry mechanisms and error nodes

**Example Use Cases:**

- Data synchronization between systems
- Automated email notifications
- File processing and transformation
- API integrations with multiple services

### Agents

**Agents** are AI-powered automation tools that can:

- **Make Decisions**: Use AI to determine the next action based on context
- **Learn and Adapt**: Improve performance over time with feedback
- **Handle Complex Logic**: Process natural language and unstructured data
- **Autonomous Operation**: Work independently with minimal human intervention
- **Dynamic Responses**: Generate different outputs based on input variations

**Example Use Cases:**

- Customer service automation
- Content generation and processing
- Intelligent data analysis
- Natural language processing tasks

### Key Differences

| Aspect           | Workflows          | Agents                  |
| ---------------- | ------------------ | ----------------------- |
| **Execution**    | Linear, sequential | Dynamic, decision-based |
| **Intelligence** | Rule-based logic   | AI-powered reasoning    |
| **Flexibility**  | Fixed paths        | Adaptive responses      |
| **Complexity**   | Structured data    | Unstructured content    |
| **Learning**     | Static behavior    | Improves over time      |
| **Use Case**     | Process automation | Intelligent automation  |

### When to Use Each

**Use Workflows when:**

- You have well-defined, repetitive tasks
- Data follows a predictable structure
- You need reliable, consistent results
- The process has clear decision points
- You want full control over the execution path

**Use Agents when:**

- You need to handle unstructured data
- The task requires natural language understanding
- You want the system to learn and improve
- Decisions need to be made based on context
- You're working with AI/ML applications

## Local Installation Guide

### Prerequisites

Before installing n8n, make sure you have the following installed on your system:

- **Node.js** (version 16 or higher)
- **npm** (comes with Node.js) or **yarn**
- **Git** (for cloning repositories)

### Installation Methods

#### Method 1: Using npm (Recommended)

```bash
# Install n8n globally
npm install n8n -g

# Start n8n
n8n
```

#### Method 2: Using Docker

```bash
# Pull the n8n Docker image
docker pull n8nio/n8n

# Run n8n container
docker run -it --rm \
  --name n8n \
  -p 5678:5678 \
  -v ~/.n8n:/home/node/.n8n \
  n8nio/n8n
```

#### Method 3: Using Docker Compose

Create a `docker-compose.yml` file:

```yaml
version: "3.8"

services:
  n8n:
    image: n8nio/n8n
    container_name: n8n
    ports:
      - "5678:5678"
    environment:
      - N8N_BASIC_AUTH_ACTIVE=true
      - N8N_BASIC_AUTH_USER=admin
      - N8N_BASIC_AUTH_PASSWORD=password
    volumes:
      - ~/.n8n:/home/node/.n8n
    restart: unless-stopped
```

Then run:

```bash
docker-compose up -d
```

### First Steps After Installation

1. **Access n8n**: Open your browser and go to `http://localhost:5678`

2. **Create Account**: Set up your first user account

3. **Explore the Interface**: Familiarize yourself with the dashboard

4. **Create Your First Workflow**: Start with a simple workflow to understand the basics

### Environment Variables

You can customize n8n behavior using environment variables:

```bash
# Database configuration
export N8N_DATABASE_TYPE=postgresdb
export N8N_DATABASE_POSTGRESDB_HOST=localhost
export N8N_DATABASE_POSTGRESDB_PORT=5432
export N8N_DATABASE_POSTGRESDB_DATABASE=n8n
export N8N_DATABASE_POSTGRESDB_USER=n8n
export N8N_DATABASE_POSTGRESDB_PASSWORD=password

# Security
export N8N_BASIC_AUTH_ACTIVE=true
export N8N_BASIC_AUTH_USER=admin
export N8N_BASIC_AUTH_PASSWORD=secure_password

# Webhook URL (for production)
export N8N_WEBHOOK_URL=https://your-domain.com

# Start n8n with environment variables
n8n
```

### Database Setup

By default, n8n uses SQLite. For production, consider using PostgreSQL:

```bash
# Install PostgreSQL (Ubuntu/Debian)
sudo apt update
sudo apt install postgresql postgresql-contrib

# Create database and user
sudo -u postgres psql
CREATE DATABASE n8n;
CREATE USER n8n WITH PASSWORD 'your_password';
GRANT ALL PRIVILEGES ON DATABASE n8n TO n8n;
\q
```

### Troubleshooting

#### Common Issues

1. **Port Already in Use**: Change the port using `--port` flag

   ```bash
   n8n --port 5679
   ```

2. **Permission Errors**: Run with appropriate permissions

   ```bash
   sudo npm install n8n -g
   ```

3. **Database Connection Issues**: Check your database configuration and credentials

4. **Memory Issues**: Increase Node.js memory limit
   ```bash
   NODE_OPTIONS="--max-old-space-size=4096" n8n
   ```

#### Getting Help

- **Documentation**: [docs.n8n.io](https://docs.n8n.io/)
- **Community Forum**: [community.n8n.io](https://community.n8n.io/)
- **GitHub Issues**: [github.com/n8n-io/n8n/issues](https://github.com/n8n-io/n8n/issues)
- **Discord**: [discord.gg/n8n](https://discord.gg/n8n)

## Next Steps

Now that you have n8n installed, you can:

1. **Follow Tutorials**: Check out the official tutorials in the n8n documentation
2. **Join the Community**: Connect with other n8n users
3. **Explore Templates**: Use pre-built workflow templates
4. **Build Your First Workflow**: Start automating your tasks

## Contributing

This repository is part of the n8n learning journey. Feel free to contribute by:

- Adding new workflow examples
- Improving documentation
- Sharing your automation stories
- Reporting issues or suggesting improvements

## License

This project is licensed under the Apache 2.0 License - see the [LICENSE](LICENSE) file for details.
