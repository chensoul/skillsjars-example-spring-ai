# SkillsJars Spring AI Example

This example shows how to use the Spring AI [Agent Utils](https://github.com/spring-ai-community/spring-ai-agent-utils)
library with [SkillsJars](https://www.skillsjars.com) to give an AI Agent access to dependency-defined Agent Skills.

The example uses the [Antropic internal-comms](https://github.com/anthropics/skills/tree/main/skills/internal-comms)
Agent Skill.

## Running the Example

1. Run the application
    ```bash
    export OPENAI_API_BASE_URL=<YOUR OPENAI API BASE URL>
    export OPENAI_API_KEY=<YOUR OPENAI API KEY>
    export OPENAI_API_MODEL=<YOUR MODEL>
    ./mvnw spring-boot:run
    ```
2. Ask a question like `use the pdf skill to create a pdf that contains the current directory listing`
