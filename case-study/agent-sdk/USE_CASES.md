# agent-sdk - Use Cases
## Case Study: TypeScript AI Agent Framework

---

## UC-001: Create Agent

| Field | Value |
|-------|-------|
| **Use Case ID** | UC-001 |
| **Use Case Name** | Create AI Agent |
| **Actor** | Developer |
| **Secondary Actors** | LLM Provider (OpenAI/Anthropic) |
| **Trigger** | Developer creates new agent instance |
| **Pre-condition** | Valid API keys configured |
| **Post-condition (Success)** | Agent instance created with configured behavior |
| **Post-condition (Failure)** | Error returned with validation details |
| **Priority** | P0 (Critical) |

### Main Flow

| Step | Actor Action | System Response |
|------|-------------|------------------|
| 1 | Developer defines agent name | System validates name format |
| 2 | Developer provides instructions | System validates instructions not empty |
| 3 | Developer selects model (gpt-4, claude-3, etc.) | System validates model availability |
| 4 | Developer configures temperature | System validates range (0-2) |
| 5 | Developer registers tools (optional) | System validates tool interfaces |
| 6 | Developer calls AgentRunner.run() | System creates agent instance |
| 7 | | System returns configured agent |

### Alternative Flows

#### Alt-1: Create Agent with Tools
| Step | Description |
|------|-------------|
| 1 | Developer provides tools array |
| 2 | System validates each tool has name, description, execute |
| 3 | Tools registered with agent |
| 4 | Agent can call tools during execution |

#### Alt-2: Create Agent with Guardrails
| Step | Description |
|------|-------------|
| 1 | Developer provides input/output guardrails |
| 2 | System validates guardrail configurations |
| 3 | Guardrails active during agent execution |

### Exception Flows

#### Ex-1: Invalid Model
| Step | Description |
|------|-------------|
| 1 | Developer specifies unsupported model |
| 2 | System returns ValidationError |
| 3 | Use case ends |

#### Ex-2: Empty Instructions
| Step | Description |
|------|-------------|
| 1 | Developer provides empty instructions |
| 2 | System returns ValidationError "Instructions required" |
| 3 | Use case ends |

### Business Rules
- BR-001: Agent name must be unique within a system
- BR-002: Instructions maximum 32,000 characters
- BR-003: Temperature must be between 0.0 and 2.0
- BR-004: Maximum 100 tools per agent

---

## UC-002: Run Agent with Conversation

| Field | Value |
|-------|-------|
| **Use Case ID** | UC-002 |
| **Use Case Name** | Execute Agent Conversation |
| **Actor** | Developer/Application |
| **Secondary Actors** | LLM Provider, Tools |
| **Trigger** | Developer calls agent.run(prompt) |
| **Pre-condition** | Agent created with valid configuration |
| **Post-condition (Success)** | Agent response returned, conversation stored |
| **Post-condition (Failure)** | Error returned, conversation unchanged |
| **Priority** | P0 (Critical) |

### Main Flow

| Step | Actor Action | System Response |
|------|-------------|------------------|
| 1 | Developer sends user message | System adds to conversation memory |
| 2 | Developer calls run() | System begins agent loop |
| 3 | | System constructs prompt with memory |
| 4 | | System calls LLM provider |
| 5 | | System receives LLM response |
| 6 | | System checks for tool calls |
| 7 | | If tool call: executes tool, continues loop |
| 8 | | If final output: returns to developer |
| 9 | | System updates conversation memory |

### Alternative Flows

#### Alt-1: Agent Uses Tool
| Step | Description |
|------|-------------|
| 1 | LLM returns tool call |
| 2 | System extracts tool name and arguments |
| 3 | System executes tool via ToolCollection |
| 4 | Tool result added to conversation |
| 5 | Return to step 4 with tool result |

#### Alt-2: Max Turns Reached
| Step | Description |
|------|-------------|
| 1 | Conversation exceeds maxTurns |
| 2 | System returns partial response |
| 3 | Warning includes turn count |

### Exception Flows

#### Ex-1: LLM Provider Error
| Step | Description |
|------|-------------|
| 1 | API key invalid or expired |
| 2 | System returns AgentError "Authentication failed" |
| 3 | Use case ends |

#### Ex-2: Rate Limit Exceeded
| Step | Description |
|------|-------------|
| 1 | Too many requests to LLM |
| 2 | System returns AgentError "Rate limit exceeded" |
| 3 | Retry-After header respected |

### Business Rules
- BR-010: Maximum 10 tool calls per conversation turn
- BR-011: Conversation memory stores last 50 messages by default
- BR-012: Tool execution timeout: 30 seconds

---

## UC-003: Multi-Agent Handoff

| Field | Value |
|-------|-------|
| **Use Case ID** | UC-003 |
| **Use Case Name** | Transfer Conversation Between Agents |
| **Actor** | Agent (autonomous) |
| **Secondary Actors** | Target Agent |
| **Trigger** | Current agent determines handoff needed |
| **Pre-condition** | Multi-agent system configured with handoffs |
| **Post-condition (Success)** | Conversation transferred to target agent |
| **Post-condition (Failure)** | Error logged, conversation continues with current agent |
| **Priority** | P1 (Important) |

### Main Flow

| Step | Actor Action | System Response |
|------|-------------|------------------|
| 1 | Agent evaluates conversation | System provides context to agent |
| 2 | Agent determines handoff required | Agent returns handoff action |
| 3 | System validates target agent exists | |
| 4 | | System transfers conversation to target agent |
| 5 | | Target agent continues conversation |
| 6 | | Handoff metadata logged |

### Alternative Flows

#### Alt-1: Handoff with Context
| Step | Description |
|------|-------------|
| 1 | Agent includes context data with handoff |
| 2 | System transfers context to target agent |
| 3 | Target agent initialized with context |

### Exception Flows

#### Ex-1: Target Agent Not Found
| Step | Description |
|------|-------------|
| 1 | Handoff specifies non-existent agent |
| 2 | System logs warning |
| 3 | Conversation continues with current agent |

### Business Rules
- BR-020: Handoff must specify valid target agent name
- BR-021: Context data serialized as JSON
- BR-022: Handoffs are logged for audit

---

## UC-004: Execute Tool

| Field | Value |
|-------|-------|
| **Use Case ID** | UC-004 |
| **Use Case Name** | Agent Executes Tool |
| **Actor** | Agent (via ToolCollection) |
| **Trigger** | LLM returns tool call in response |
| **Pre-condition** | Tool registered with agent |
| **Post-condition (Success)** | Tool result returned to agent |
| **Post-condition (Failure)** | Error result returned |
| **Priority** | P0 (Critical) |

### Main Flow

| Step | Actor Action | System Response |
|------|-------------|------------------|
| 1 | System extracts tool name | |
| 2 | System locates tool in ToolCollection | |
| 3 | System validates tool parameters | |
| 4 | | System executes tool |
| 5 | | System returns result to agent |

### Alternative Flows

#### Alt-1: Built-in Calculator Tool
| Step | Description |
|------|-------------|
| 1 | Tool name is "calculator" |
| 2 | System evaluates mathematical expression |
| 3 | Result returned as string |

#### Alt-2: Custom Tool
| Step | Description |
|------|-------------|
| 1 | Tool is user-defined function |
| 2 | System calls custom execute function |
| 3 | Result returned |

### Exception Flows

#### Ex-1: Tool Not Found
| Step | Description |
|------|-------------|
| 1 | Tool name not in collection |
| 2 | System returns error "Tool not found: {name}" |
| 3 | Agent notified of error |

#### Ex-2: Tool Execution Error
| Step | Description |
|------|-------------|
| 1 | Tool throws exception during execution |
| 2 | System catches exception |
| 3 | Error returned to agent as tool result |

### Business Rules
- BR-030: Tool names must be unique
- BR-031: Parameters must match tool schema
- BR-032: Tool execution is synchronous by default

---

## UC-005: Validate with Guardrails

| Field | Value |
|-------|-------|
| **Use Case ID** | UC-005 |
| **Use Case Name** | Apply Content Guardrails |
| **Actor** | Guardrail System |
| **Trigger** | Before/after LLM call |
| **Pre-condition** | Guardrails configured on agent |
| **Post-condition (Success)** | Content validated, passed through |
| **Post-condition (Failure)** | Content blocked, error returned |
| **Priority** | P1 (Important) |

### Main Flow

| Step | Actor Action | System Response |
|------|-------------|------------------|
| 1 | User input received | |
| 2 | | GuardrailConfig validates input |
| 3 | | If valid: pass to agent |
| 4 | | If invalid: return error |
| 5 | Agent generates response | |
| 6 | | GuardrailConfig validates output |
| 7 | | If valid: return to user |
| 8 | | If invalid: return error |

### Alternative Flows

#### Alt-1: Max Length Guardrail
| Step | Description |
|------|-------------|
| 1 | Input/Output exceeds max characters |
| 2 | Guardrail returns failed validation |
| 3 | User receives error |

#### Alt-2: Content Filter Guardrail
| Step | Description |
|------|-------------|
| 1 | Input/Output contains prohibited terms |
| 2 | Guardrail returns failed validation |
| 3 | Content blocked |

### Business Rules
- BR-040: Input guardrails run before LLM call
- BR-041: Output guardrails run after LLM call
- BR-042: Failed guardrail does not consume LLM tokens

---

## Traceability Matrix

| Use Case | Functional Requirements | Test Cases |
|----------|------------------------|------------|
| UC-001 | FR-001 | TC-001, TC-002, TC-003 |
| UC-002 | FR-002 | TC-004, TC-005, TC-006 |
| UC-003 | FR-003 | TC-007, TC-008 |
| UC-004 | FR-004 | TC-009, TC-010, TC-011 |
| UC-005 | FR-005 | TC-012, TC-013 |

---

*Document Control:*
- *Version:* 1.0
- *Author:* Hafeez
- *Date:* 2026-04-20
