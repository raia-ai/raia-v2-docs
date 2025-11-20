# raia Command User Guide

## Build and Train Your Digital Workforce Without Code&#x20;

***

### Overview

raia Command serves as the central command center for building, training, and deploying AI agents across your organization. Designed with simplicity and enterprise security in mind, Command empowers businesses to create intelligent, autonomous agents without writing a single line of code. Through an intuitive, step-by-step interface, teams can define an agent's purpose, connect data sources, assign capabilities, and launch into production—all within minutes.\


Built on SOC2-compliant infrastructure, raia Command enables organizations to scale from a single use case to hundreds of specialized agents, each trained on company knowledge and processes. Whether automating customer support, sales outreach, or internal workflows, Command provides the foundation for building a true digital workforce that operates 24/7 across every channel.

***

### How raia Command Works

#### The Agent Creation Workflow

raia Command transforms complex AI agent development into a guided, accessible process through its step-by-step Wizard interface. The Wizard walks users through each stage of agent creation using clear, simple prompts that require no technical expertise. Users begin by selecting or defining an agent role—such as customer support specialist, sales representative, or internal assistant—which establishes the foundational purpose and behavior patterns.



The platform leverages a sophisticated four-layer training architecture that combines base language models with your organization's specific knowledge and requirements. The first layer consists of powerful foundation models from OpenAI that provide general language understanding and reasoning capabilities. The second layer connects to your vector store, where all company-specific knowledge resides in AI-ready format. The third layer applies instructional prompts that define the agent's behavior, tone, and response patterns. The fourth layer adds contextual prompts that adapt responses based on real-time conversation context and user information.

#### Skills: Empowering Agents with Capabilities

One of Command's most powerful features is its comprehensive Skills system, which gives agents the capabilities they need to perform real-world tasks. Skills are pre-built integrations and functionalities that can be enabled with simple configuration, eliminating the need for custom development. Communication Skills enable multi-channel engagement through Live Chat, SMS, Email, and Voice, allowing agents to interact with customers wherever they are. Integration Skills connect agents to external systems through APIs, Webhooks, and custom Functions, enabling actions like updating CRM records, booking appointments, or triggering workflows in other applications.



Intelligence Skills enhance agent capabilities with features like Web Search for accessing current information, Scraping for extracting data from websites, Scoring for evaluating conversation quality, and Memory for maintaining context across interactions. Operational Skills support business processes through Calendar integration for scheduling, Notifications for alerts and updates, Reporting for analytics, Feedback for human-in-the-loop improvement, and Escalation for seamless handoff to human agents when needed.

#### Agent States and Lifecycle Management

raia Command implements a clear agent lifecycle with three distinct states that ensure safe development and deployment. Draft state represents the configuration and testing phase where agents are built, trained, and refined without handling real conversations. This protected environment allows teams to experiment, test different configurations, and iterate on training materials without risk to production operations.\


Active state indicates that an agent is live and operational, handling real conversations across configured channels. Active agents respond to customer inquiries, execute workflows, and perform their assigned tasks with full access to skills and knowledge. Inactive state represents a paused agent that retains all settings, training, and configuration but does not handle conversations. This state is useful for seasonal agents, temporary deactivation during updates, or agents that need to be preserved for future reactivation.

#### Integration and Connectivity

Command provides robust integration capabilities that connect agents to your existing technology ecosystem. The platform supports direct API integration with authentication options including API keys and OAuth, enabling secure connections to CRM systems, helpdesk platforms, databases, and custom applications. Webhook functionality allows agents to send real-time data to external systems based on conversation events, enabling automated workflows and data synchronization.



For communication channels, Command integrates seamlessly with Twilio for SMS messaging and Mailgun for email, providing enterprise-grade reliability and deliverability. The Live Chat SDK enables embedding agents directly into websites with customizable appearance and behavior, while Zendesk integration allows agents to operate within existing support workflows. These integrations are configured through simple forms in the Command interface, with test capabilities to verify connections before activation.



***

### Key Benefits

#### Speed and Accessibility for All Users

raia Command dramatically reduces the time and expertise required to deploy AI agents. Traditional AI development requires months of engineering work, specialized machine learning knowledge, and significant technical resources. Command compresses this timeline to minutes through its no-code interface and pre-built components. Business users, customer service managers, sales leaders, and operations teams can create sophisticated AI agents without involving engineering teams, democratizing AI capabilities across the organization.



The platform's use of pre-built training packs and pre-configured skills accelerates deployment even further. Instead of starting from scratch, users can leverage ready-to-go knowledge bases and capabilities, then customize them to specific business needs. This approach enables rapid experimentation and iteration, allowing organizations to test multiple use cases quickly and scale what works. The speed advantage extends beyond initial deployment—updates, refinements, and new agent creation all follow the same streamlined process, enabling continuous improvement and expansion of AI capabilities.

#### Enterprise Security and Governance

Security and compliance are foundational to raia Command's architecture, not afterthoughts. The platform is built on SOC2-compliant infrastructure with comprehensive security controls that meet enterprise and regulatory requirements. Role-based access control ensures that only authorized personnel can create, modify, or deploy agents, with granular permissions that can be tailored to organizational structure. Audit logging tracks all actions and changes, providing complete visibility for compliance reporting and security monitoring.



Data isolation ensures that each agent's knowledge and conversations remain separate and secure, preventing unauthorized access or cross-contamination. Agents can be configured as Public (accessible via link without authentication) or Private (requiring user authentication), giving organizations control over access based on use case sensitivity. API key management includes rotation capabilities and secure storage, following security best practices. These enterprise-grade security features enable organizations in regulated industries—including healthcare, finance, and legal services—to deploy AI agents with confidence.

#### Scalability and Centralized Management

raia Command is architected for scale, supporting organizations as they grow from a single agent to hundreds of specialized agents across departments and use cases. The centralized management interface provides a single pane of glass for monitoring, configuring, and optimizing all agents, eliminating the complexity of managing disparate AI implementations. This centralization ensures consistent governance, standardized security policies, and unified reporting across the entire agent fleet.



The platform's architecture supports both vertical scaling (increasing capacity for individual agents) and horizontal scaling (adding more agents) without performance degradation. Organizations can deploy specialized agents for different products, regions, languages, or customer segments, each with tailored knowledge and capabilities. Version control and agent cloning (where permitted by security policies) enable rapid deployment of proven configurations to new use cases. As the agent fleet grows, Command's monitoring and analytics capabilities provide visibility into performance, resource utilization, and business impact across all agents.

#### Continuous Improvement and Optimization

raia Command facilitates continuous improvement through comprehensive monitoring, feedback collection, and iterative refinement. The Reports Tab provides detailed analytics on conversation volume, skill utilization, response times, and user satisfaction, enabling data-driven optimization. Conversation logs capture complete interaction history, allowing teams to identify patterns, common issues, and opportunities for enhancement.



Integration with raia Copilot enables human-in-the-loop feedback where team members can review agent responses, provide ratings, and suggest improvements. This feedback flows back into agent training, creating a virtuous cycle of continuous learning. The platform supports A/B testing of different configurations, allowing organizations to experiment with variations in instructions, knowledge, or skills and measure impact on key metrics. Version control enables rollback to previous configurations if updates don't perform as expected, reducing risk and encouraging experimentation.



***

### Key Features

#### No-Code Agent Builder with Guided Wizard

The Agent Builder Wizard represents Command's commitment to accessibility without sacrificing sophistication. The step-by-step interface guides users through agent creation with contextual help, examples, and best practice recommendations at each stage. Users define the agent's role and purpose through natural language descriptions, eliminating the need to understand technical AI concepts. The Wizard intelligently suggests relevant skills based on the selected role, streamlining configuration while allowing full customization.\


Pre-built templates for common use cases—such as customer support, lead qualification, appointment scheduling, and FAQ answering—provide starting points that can be customized to specific needs. The Wizard includes validation checks that identify potential issues before deployment, such as missing required configurations or conflicting settings. Preview functionality allows users to test agent behavior during the creation process, ensuring the configuration meets expectations before activation.

#### Comprehensive Skills Ecosystem

Command's Skills ecosystem provides agents with a rich set of capabilities that can be enabled and configured through simple interfaces. Each skill includes detailed configuration options that control behavior, authentication, error handling, and integration specifics. The Live Chat Skill, for example, offers extensive customization of widget appearance, welcome messages, routing rules, and escalation triggers, all configured through visual editors without code.\


The API Skill enables sophisticated integrations with external systems through a configuration interface that handles endpoint specification, authentication methods, request/response mapping, and error handling. Users can test API connections directly from Command, validating functionality before agent activation. The Functions Skill allows execution of custom backend logic, with configuration for function selection, parameter passing, and result handling. Each skill includes comprehensive documentation, examples, and troubleshooting guidance accessible directly from the configuration interface.

#### Multi-Channel Communication

Command enables agents to engage across multiple communication channels from a single configuration, ensuring consistent behavior and knowledge regardless of how customers choose to interact. The Live Chat channel deploys embeddable web widgets that can be customized to match brand identity, with control over colors, positioning, welcome messages, and behavior. SMS integration through Twilio enables two-way text messaging with configuration for phone numbers, message templates, and conversation flow.



Email capability through Mailgun allows agents to send and receive emails with customizable sender identity, templates, and automated responses. Voice integration enables telephone conversations with configuration for phone numbers, greeting messages, and call routing. All channels share the same underlying agent intelligence, knowledge base, and skills, ensuring customers receive consistent, accurate responses regardless of channel. Conversation history is unified across channels, allowing agents to maintain context even when customers switch between chat, SMS, email, and voice.

#### Security and Access Control

Command implements comprehensive security controls that protect sensitive data and ensure appropriate access. Role-based access control (RBAC) allows administrators to define roles with specific permissions, such as Agent Creator, Agent Manager, Viewer, or Administrator. Permissions can be granted at granular levels, controlling who can create agents, modify configurations, access conversation logs, manage integrations, or deploy to production.



Agent-level security settings distinguish between Public agents (accessible without authentication) and Private agents (requiring user login), with additional controls for IP whitelisting, rate limiting, and access restrictions. API key management includes secure generation, storage, rotation, and revocation capabilities, with audit logging of all API access. Data encryption protects information at rest and in transit, meeting compliance requirements for regulated industries. Session management controls timeout periods, concurrent session limits, and forced logout capabilities for enhanced security.

#### Monitoring, Reporting, and Analytics

The Reports Tab in Command provides comprehensive visibility into agent performance, resource utilization, and business impact. Conversation analytics track volume, duration, resolution rates, and user satisfaction across all channels and agents. Skill utilization reports show which capabilities are being used most frequently, informing optimization decisions and identifying opportunities for additional automation.



Performance metrics monitor response times, error rates, API call volumes, and system health, with alerting capabilities for anomalies or issues. User interaction reports provide insights into common questions, conversation patterns, and drop-off points, enabling continuous improvement of agent knowledge and behavior. Export functionality allows data to be extracted for further analysis in business intelligence tools or custom dashboards. Scheduled reports can be configured to deliver key metrics via email or SMS, keeping stakeholders informed without requiring manual monitoring.

#### Integration with raia Ecosystem

Command seamlessly integrates with the other applications in the raia cX platform, creating a unified workflow for agent development, training, deployment, and optimization. Integration with raia Connect enables direct access to knowledge management capabilities, allowing users to upload training materials, convert documents to AI-ready format, and push content to agent vector stores without leaving the Command interface.



Connection to raia Copilot provides testing and feedback capabilities, with the ability to simulate conversations, enable Admin Mode for debugging, and collect human feedback on agent responses. Integration with raia Chat ensures that agents deployed through Command are immediately available through web chat widgets with consistent branding and behavior. Connection to raia Control enables agents to be used in proactive outbound campaigns, extending their capabilities from reactive support to active engagement. This ecosystem integration eliminates silos, reduces context switching, and creates a seamless experience for agent development and management.

#### Version Control and Rollback

Command maintains complete version history for all agent configurations, enabling safe experimentation and rapid recovery from issues. Every change to agent settings, instructions, skills, or knowledge is tracked with timestamps, user attribution, and change descriptions. Users can compare versions to understand what changed between iterations, facilitating troubleshooting and learning.\


Rollback functionality allows instant reversion to any previous configuration, minimizing downtime and risk when updates don't perform as expected. Version tagging enables marking stable configurations for easy reference and reuse. The version control system supports branching workflows where teams can experiment with variations without affecting production agents, then merge successful changes back to the main configuration. This capability encourages innovation and continuous improvement by reducing the risk associated with making changes.



***

### Getting Started with raia Command

Organizations beginning their journey with raia Command typically start with a single, well-defined use case that addresses a clear business need. Common starting points include customer FAQ automation, lead qualification, appointment scheduling, or internal help desk support. The focused approach allows teams to learn the platform, establish best practices, and demonstrate value before expanding to additional use cases.\


The typical implementation timeline spans one to two weeks from initial setup to production deployment. The first phase involves defining the agent's role, gathering relevant knowledge materials, and configuring basic settings through the Wizard. The second phase focuses on training, where documents are uploaded through raia Connect and converted to AI-ready format. The third phase emphasizes testing through raia Copilot, where team members simulate conversations, provide feedback, and refine agent behavior. The final phase includes production deployment with monitoring and continuous optimization.



Success with raia Command comes from treating agents as evolving assets rather than one-time implementations. Organizations that achieve the greatest value establish regular review cycles, continuously expand agent knowledge based on new questions and scenarios, and systematically add skills and capabilities as needs evolve. The platform's accessibility enables this iterative approach, allowing business users to make improvements without waiting for technical resources or lengthy development cycles.



***

### Conclusion

raia Command represents a fundamental shift in how organizations approach AI agent development and deployment. By eliminating technical barriers while maintaining enterprise-grade security and scalability, Command democratizes AI capabilities and enables rapid innovation. The platform's no-code interface, comprehensive skills ecosystem, and seamless integration with the raia cX platform create a complete solution for building, training, and managing intelligent agents at scale.\


Organizations using raia Command report dramatic reductions in time-to-deployment, increased accessibility of AI capabilities across teams, and improved ability to scale automation initiatives. The platform's combination of simplicity and sophistication enables both rapid experimentation with new use cases and robust production deployments that handle millions of interactions. As businesses continue to recognize AI agents as essential components of modern operations, raia Command provides the foundation for building a true digital workforce that augments human capabilities and drives measurable business outcomes.

\
