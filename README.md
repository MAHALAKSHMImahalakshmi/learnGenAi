graph TD
    subgraph Core Language Learning Platform
        User["Student / Teacher"] --> FrontEnd["Language Learning Portal (Web/App)"]
        FrontEnd -- "Interacts via API" --> BackEnd["Backend API (Flask App)"]
        BackEnd -- "Stores & Retrieves" --> Database["Relational Database (e.g., SQLite)"]
        FrontEnd -- "Launches / Presents" --> StudyActivities["Study Activities / Learning Games"]
        StudyActivities -- "Interacts via API" --> BackEnd
    end

    subgraph GenAI Augmentation: Vocab Importer Example
        InternalUser["Internal User / Teacher"] --> VocabImporter["Vocab Importer Tool (e.g., Gradio/Streamlit)"]
        VocabImporter -- "Requests Vocabulary Generation" --> GenAISystem["GenAI System"]

        subgraph GenAI System
            GenAISystem --> ContextManagement["Context Management / Prompt Engineering"]
            ContextManagement -- "Prepares input for" --> LLM["AI Model (Large Language Model)"]
            LLM -- "Generates Vocab" --> GenAISystem

            subgraph Optional GenAI Components
                GuardRails["Guardrails (Input/Output Filtering)"]
                PipelineOrchestrator["Pipeline Orchestrator"]
                KnowledgeBase["Knowledge Base (RAG)"]
                Agents["Agents / External Actions"]
                Caching["Caching"]

                ContextManagement -- "Subject to" --> GuardRails
                GuardRails -- "Filters" --> LLM
                LLM -- "Managed by" --> PipelineOrchestrator
                PipelineOrchestrator -- "Integrates" --> KnowledgeBase
                PipelineOrchestrator -- "Triggers" --> Agents
                LLM -- "Results may be" --> Caching
                Caching -- "Serves" --> GenAISystem
            end
        end

        GenAISystem -- "Returns Formatted Vocab (JSON)" --> VocabImporter
        VocabImporter -- "Imports into" --> BackEnd
    end

   %% Style definitions with bold white text and high contrast background
style User fill:#1F77B4,stroke:#333,stroke-width:2px,color:#fff,font-weight:bold
style InternalUser fill:#1F77B4,stroke:#333,stroke-width:2px,color:#fff,font-weight:bold
style FrontEnd fill:#FF7F0E,stroke:#333,stroke-width:2px,color:#fff,font-weight:bold
style BackEnd fill:#D62728,stroke:#333,stroke-width:2px,color:#fff,font-weight:bold
style Database fill:#2CA02C,stroke:#333,stroke-width:2px,color:#fff,font-weight:bold
style StudyActivities fill:#FF7F0E,stroke:#333,stroke-width:2px,color:#fff,font-weight:bold
style VocabImporter fill:#9467BD,stroke:#333,stroke-width:2px,color:#fff,font-weight:bold
style GenAISystem fill:#8C564B,stroke:#333,stroke-width:2px,color:#fff,font-weight:bold
style LLM fill:#8C564B,stroke:#333,stroke-width:2px,color:#fff,font-weight:bold
style ContextManagement fill:#17BECF,stroke:#333,stroke-width:2px,color:#fff,font-weight:bold
style GuardRails fill:#BCBD22,stroke:#333,stroke-width:2px,color:#fff,font-weight:bold
style PipelineOrchestrator fill:#E377C2,stroke:#333,stroke-width:2px,color:#fff,font-weight:bold
style KnowledgeBase fill:#7F7F7F,stroke:#333,stroke-width:2px,color:#fff,font-weight:bold
style Agents fill:#FFBB78,stroke:#333,stroke-width:2px,color:#fff,font-weight:bold
style Caching fill:#AEC7E8,stroke:#333,stroke-width:2px,color:#fff,font-weight:bold

