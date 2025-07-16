# GitHub Analysis Context Engineering Scaffold

A powerful framework for systematic GitHub repository analysis and data extraction, built on the Context Engineering methodology. This scaffold transforms the software-building PRP (Product Requirement Prompt) approach into an analysis-focused ARP (Analysis Requirement Prompt) system.

## 🎯 Overview

This scaffold provides a structured approach to:
- Analyze GitHub repositories systematically
- Extract meaningful insights and metrics
- Ensure reproducible and validated results
- Handle large-scale analysis efficiently

### Key Differences: ARP vs PRP

| PRP (Product Requirements) | ARP (Analysis Requirements) |
|---------------------------|---------------------------|
| Builds software | Extracts insights |
| Generates code | Collects data |
| Creates features | Identifies patterns |
| Implements functionality | Analyzes characteristics |

## 🚀 Quick Start

### 1. Setup

```bash
# Clone the scaffold
git clone <repository-url> github-analysis-scaffold
cd github-analysis-scaffold

# Configure API access (optional but recommended)
export GITHUB_TOKEN=your_github_token_here
```

### 2. Create Your Analysis Request

Create an `INITIAL.md` file describing what you want to analyze:

```markdown
# Analysis Request: My Repository Analysis

## OBJECTIVE
Analyze code quality and identify technical debt in my project.

## REPOSITORIES
**Target Repository**: myorg/myrepo
**Branch**: main

## EXPECTED OUTPUTS
- [x] Code metrics report
- [x] Technical debt assessment
- [x] Improvement recommendations
```

### 3. Generate Analysis Requirements

```bash
# Generate a comprehensive ARP from your request
/generate-arp INITIAL.md
```

This creates a detailed Analysis Requirement Prompt in `ARPs/`

### 4. Execute the Analysis

```bash
# Run the analysis based on the generated ARP
/execute-arp ARPs/generated-analysis.md
```

### 5. Validate Results

```bash
# Ensure data quality and completeness
/validate-analysis outputs/latest/
```

## 📋 Analysis Types

### Pre-built Templates

1. **Code Metrics Analysis** (`code_metrics_analysis.md`)
   - Lines of code, complexity metrics
   - Technical debt assessment
   - Code quality indicators

2. **Pattern Extraction** (`pattern_extraction.md`)
   - Design pattern detection
   - Anti-pattern identification
   - Architectural analysis

3. **Dependency Mapping** (`dependency_mapping.md`)
   - Dependency tree visualization
   - Security vulnerability scanning
   - Update recommendations

4. **Custom Analysis** (`arp_base.md`)
   - Build your own analysis type
   - Combine multiple approaches
   - Domain-specific metrics

## 🔧 Commands

### `/generate-arp`
Generates comprehensive Analysis Requirement Prompts from initial requests.

```bash
/generate-arp INITIAL.md [--output ARPs/custom-name.md]
```

**Features:**
- Explores target repositories automatically
- Plans optimal extraction strategies
- Considers API rate limits
- Includes validation criteria

### `/execute-arp`
Executes analysis workflows based on ARP specifications.

```bash
/execute-arp ARPs/analysis.md [--validate] [--cache-only] [--resume]
```

**Options:**
- `--validate`: Run pre-execution validation
- `--cache-only`: Use only cached data (no API calls)
- `--resume`: Continue from last checkpoint
- `--dry-run`: Preview execution plan

### `/validate-analysis`
Validates analysis outputs and ensures data quality.

```bash
/validate-analysis outputs/analysis-name/ [--report] [--strict]
```

**Validation Levels:**
1. Data Access - Repository accessibility
2. Extraction Quality - Completeness and accuracy
3. Processing Validity - Transformation correctness
4. Output Compliance - Format and schema validation

## 📁 Project Structure

```
github-analysis-scaffold/
├── .claude/                  # Claude Code configuration
│   ├── commands/            # Command definitions
│   └── settings.local.json  # Project settings
├── ARPs/                    # Analysis Requirement Prompts
│   ├── templates/          # Pre-built templates
│   └── examples/           # Example analyses
├── analysis/               # Analysis modules
│   ├── extractors/        # Data extraction logic
│   ├── processors/        # Data processing logic
│   └── validators/        # Validation logic
├── data/                  # Data storage
│   ├── cache/            # API response cache
│   └── schemas/          # Output schemas
├── outputs/              # Analysis results
└── INITIAL.md           # Your analysis request
```

## 🔄 Workflow Example

### Analyzing React's Codebase

1. **Create Initial Request**
```markdown
# INITIAL.md
## OBJECTIVE
Analyze React's code complexity and identify refactoring opportunities.

## REPOSITORIES
Target: facebook/react@main
```

2. **Generate ARP**
```bash
/generate-arp INITIAL.md
# Creates: ARPs/react-complexity-analysis.md
```

3. **Execute Analysis**
```bash
/execute-arp ARPs/react-complexity-analysis.md
# Generates: outputs/react-analysis-20240115/
```

4. **Review Results**
```bash
/validate-analysis outputs/react-analysis-20240115/
# View report at: outputs/react-analysis-20240115/reports/summary.md
```

## 🛡️ Best Practices

### API Rate Limiting
- The scaffold automatically manages GitHub API rate limits
- Use authentication for higher limits (5000 vs 60 requests/hour)
- Enable caching to minimize API calls
- Use `--cache-only` for offline analysis

### Performance Optimization
- **Large Repositories**: Use incremental analysis
- **Multiple Repos**: Enable parallel processing
- **Historical Analysis**: Cache historical data
- **Resource Limits**: Monitor memory usage

### Data Quality
- Always validate results before use
- Check completeness metrics
- Review error logs
- Verify against known values

## 🔌 Extending the Framework

### Custom Templates
1. Copy an existing template from `ARPs/templates/`
2. Modify phases for your analysis needs
3. Add custom validation rules
4. Test with small repositories first

### Custom Extractors
```python
# analysis/extractors/my_extractor.py
class MyExtractor:
    def extract(self, repo_data):
        # Custom extraction logic
        return extracted_data
```

### Integration Examples

**GitHub Actions:**
```yaml
- name: Weekly Code Analysis
  run: |
    /generate-arp .github/WEEKLY_ANALYSIS.md
    /execute-arp ARPs/weekly-analysis.md
    /validate-analysis outputs/latest/ --strict
```

**Git Hooks:**
```bash
#!/bin/bash
# .git/hooks/pre-push
/execute-arp ARPs/pre-push-analysis.md --quick
```

## 🐛 Troubleshooting

### Common Issues

**"Repository not accessible"**
- Check repository visibility
- Verify authentication token
- Ensure correct repository path

**"Rate limit exceeded"**
```bash
# Check rate limit status
curl -H "Authorization: token $GITHUB_TOKEN" \
  https://api.github.com/rate_limit

# Use cached data
/execute-arp ARPs/analysis.md --cache-only
```

**"Analysis timeout"**
- Reduce analysis scope
- Enable incremental mode
- Increase timeout limits

### Debug Mode
```bash
# Enable detailed logging
export ANALYSIS_DEBUG=true
export ANALYSIS_LOG_LEVEL=debug

# Run with verbose output
/execute-arp ARPs/analysis.md --verbose
```

## 📊 Output Formats

### JSON Data
```json
{
  "analysis_metadata": {
    "timestamp": "2024-01-15T10:30:00Z",
    "repository": "owner/repo",
    "duration_seconds": 245
  },
  "results": {
    // Analysis-specific results
  }
}
```

### Markdown Reports
- Executive summaries
- Detailed findings
- Visualizations
- Recommendations

### Visualizations
- Dependency graphs (D3.js)
- Complexity heatmaps
- Trend charts
- Architecture diagrams

## 🤝 Contributing

### Adding New Analysis Types
1. Create template in `ARPs/templates/`
2. Implement extractors/processors
3. Add validation rules
4. Document usage

### Improving Existing Analyses
- Enhance accuracy
- Optimize performance
- Add visualizations
- Improve error handling

## 📚 Resources

### Documentation
- [Context Engineering Introduction](https://github.com/coleam00/context-engineering-intro)
- [Original PRP Concept](https://github.com/Wirasm/dylan/tree/main/concept_library/cc_PRP_flow)
- GitHub API Documentation

### Examples
- See `ARPs/examples/` for complete analysis examples
- Check `outputs/examples/` for sample results
- Review templates for patterns

## 📄 License

[Your License Here]

## 🙏 Acknowledgments

Built on the Context Engineering methodology, adapting software building patterns for powerful repository analysis capabilities.