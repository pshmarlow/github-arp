# Generate ARP Command

Generate comprehensive Analysis Requirement Prompts (ARPs) from analysis request specifications.

## Usage

```
/generate-arp INITIAL.md [--output ARPs/my-analysis.md]
```

## Process

1. **Parse Analysis Request**
   - Read and understand the INITIAL.md file
   - Extract objectives, target repositories, and expected outputs
   - Identify any constraints or special requirements

2. **Repository Discovery**
   - Explore target repository structure
   - Analyze codebase size and complexity
   - Identify key files and patterns
   - Check API accessibility and rate limits

3. **Analysis Planning**
   - Determine optimal extraction strategies
   - Plan data collection phases
   - Consider caching and incremental processing
   - Design validation checkpoints

4. **ARP Generation**
   - Create comprehensive Analysis Requirement Prompt
   - Include all discovered context
   - Define clear success criteria
   - Specify output formats and schemas

## Template Selection

Based on the analysis type, automatically select appropriate templates:
- `code_metrics_analysis.md` - For code quality and complexity metrics
- `pattern_extraction.md` - For design pattern and anti-pattern detection
- `dependency_mapping.md` - For dependency tree and architecture analysis
- `arp_base.md` - For custom or mixed analysis types

## Key Features

- **Smart Context Gathering**: Automatically explores repositories to understand structure
- **Rate Limit Awareness**: Plans around GitHub API limits
- **Validation Planning**: Includes data quality checks at each phase
- **Incremental Design**: Supports resumable and partial analyses

## Example Workflow

```bash
# Generate ARP from initial request
/generate-arp INITIAL.md

# Review generated ARP
cat ARPs/generated_analysis.md

# Execute the analysis
/execute-arp ARPs/generated_analysis.md
```

## Best Practices

1. **Be Specific in INITIAL.md**: Clear objectives lead to better ARPs
2. **Review Generated ARPs**: Validate the analysis plan before execution
3. **Consider Constraints**: Include rate limits and time constraints
4. **Plan for Scale**: Design for both small and large repositories

## Output

Generated ARPs include:
- Complete analysis methodology
- Detailed extraction phases
- Validation criteria
- Output specifications
- Error handling strategies
- Performance considerations