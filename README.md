# Podcast Processor CLI Tool

A Claude Code sub-agent that automatically transcribes Spotify podcast episodes using OpenAI Whisper API and formats them into structured markdown files.

## Overview

This tool creates a seamless workflow for converting Spotify podcast content into searchable, formatted transcripts with timestamps, metadata, and structured navigation.

### Core Workflow
1. **Input**: Spotify podcast URL
2. **Download**: Extract audio from Spotify podcast
3. **Transcribe**: Process audio through OpenAI Whisper API
4. **Format**: Generate structured markdown with metadata
5. **Save**: Output formatted transcript file

## Key Features

- **Spotify Integration**: Direct URL input for podcast episodes
- **High-Quality Transcription**: OpenAI Whisper API for excellent accuracy
- **Structured Output**: YAML frontmatter + timestamped sections
- **Speaker Identification**: Host/Guest labeling with visual icons
- **Navigation**: Clickable timestamps for easy reference
- **Claude Code Integration**: Seamless CLI command integration

## Output Format

### Markdown Structure
```markdown
---
title: "Episode Title"
podcast_name: "Podcast Series Name"
episode_number: "Episode #123"
spotify_url: "https://open.spotify.com/episode/..."
transcription_date: "2025-09-17"
duration: "45:32"
file_size: "42.3 MB"
language: "en"
quality: "high"
---

## Episode Summary
[Auto-generated key topics and overview]

## Transcript
### [00:00:00] Introduction
**Host:** Welcome to the show...

### [00:05:30] Main Topic Discussion
**Guest:** Thanks for having me...
```

### File Naming Convention
```
[podcast-name]-ep[###]-[episode-title-slug]-transcript-YYYY-MM-DD.md
```

## Technical Architecture

### Technology Stack
- **Framework**: Pydantic AI (production-ready Python agent framework)
- **APIs**: Spotify API + OpenAI Whisper API
- **Language**: Python with full type safety
- **CLI Integration**: Claude Code sub-agent pattern
- **Output**: Structured markdown with YAML frontmatter

### Core Components
- **URL Validation**: Type-safe Spotify URL processing
- **Audio Processing**: Download and format conversion pipeline
- **API Integration**: Robust Whisper API calls with error handling
- **Markdown Generation**: Template engine for consistent formatting
- **CLI Interface**: Claude Code command integration

### Pydantic AI Integration

#### Input Validation Models
```python
class PodcastRequest(BaseModel):
    spotify_url: HttpUrl
    output_format: Literal["markdown", "json"] = "markdown"
    include_timestamps: bool = True
    language: str = "en"
```

#### Agent-Based Processing
```python
@agent.tool
def download_audio(spotify_url: str) -> AudioFile:
    # Spotify API integration

@agent.tool
def transcribe_audio(audio_file: AudioFile) -> TranscriptionResult:
    # Whisper API with retry logic

@agent.tool
def format_transcript(result: TranscriptionResult) -> MarkdownDocument:
    # Structured markdown generation
```

## Development Status

**Current Phase**: Planning - Ready for BMAD Implementation

### Completed
- ✅ Project concept and requirements definition
- ✅ Technical architecture outline
- ✅ Output format design and markdown structure
- ✅ Pydantic AI framework integration analysis
- ✅ BMAD framework installation

### Next Steps
1. **BMAD Planning Phase**: Use analyst/PM/architect agents for detailed requirements
2. **Pydantic AI Setup**: Install framework and define data models
3. **API Integration**: Implement Spotify and Whisper API connections
4. **CLI Development**: Create Claude Code sub-agent interface
5. **Testing & Validation**: Quality assurance and error handling

## BMAD Method Integration

This project uses the **BMAD (Breakthrough Method for AI-driven Agile Development)** methodology:

### Planning Phase Agents
1. **Analyst** → Research Spotify API + Whisper integration patterns
2. **Product Manager** → Define CLI interface and error handling
3. **Architect** → Design audio processing pipeline architecture
4. **Product Owner** → Validate document consistency

### Development Phase
5. **Scrum Master** → Break into implementable stories
6. **Developer** → Code implementation with Pydantic AI
7. **QA/Test Architect** → Quality assurance and testing

## Use Cases

### Primary Use Case
- **Target User**: Content creators, researchers, students
- **Problem Solved**: Manual transcription of podcast content is time-consuming and inaccurate
- **Value Delivered**: Automated, high-quality transcripts with searchable content

### Business Applications
- Content repurposing for blogs and social media
- Research and analysis of podcast discussions
- Accessibility improvements for hearing-impaired audiences
- SEO optimization through text content generation

## Project Structure

```
podcast-processor-cli-tool/
├── .bmad-core/              # BMAD framework installation
├── .claude/                 # Claude Code integration
├── drews-artifacts/         # Project checkpoints and planning docs
├── src/                     # Source code (TBD)
├── tests/                   # Test suites (TBD)
└── README.md               # This file
```

## Installation & Usage

*Coming soon - CLI interface under development*

```bash
# Future usage pattern
claude-podcast-transcribe https://open.spotify.com/episode/xyz123
```

## Quality & Error Handling

### Multi-Layer Validation
- **URL Validation**: Verify Spotify podcast URLs
- **API Error Handling**: Robust retry logic for network failures
- **Audio Format Validation**: Ensure compatible audio processing
- **Quality Metrics**: Confidence scores and transcription accuracy

### Observability
- **Pydantic Logfire**: Built-in monitoring and debugging
- **Performance Metrics**: Processing time and API usage tracking
- **Quality Assessment**: Transcription confidence and error rates

## Contributing

This is a learning project focused on:
- Pydantic AI framework patterns
- Claude Code sub-agent development
- Production-ready Python practices
- AI-assisted development workflows

## License

Private project - All rights reserved.

---

**Built with**: Pydantic AI | BMAD Methodology | OpenAI Whisper | Claude Code Integration
**Purpose**: Automated podcast transcription with production-ready AI agent patterns