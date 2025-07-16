# Analysis Requirement Prompt: Code Metrics Analysis

## Analysis Goal
Extract comprehensive code quality metrics, complexity measurements, and maintainability indicators from target repositories to assess code health and identify areas for improvement.

## Target Repositories
- **Primary Repository**: [owner/repo-name@main]
- **Comparison Baseline**: [optional: previous version or benchmark repo]
- **File Patterns**: All source code files (exclude tests, docs, vendor)

## Context

### Repository Background
[Repository-specific context will be filled during ARP generation]

### Data Requirements
**Core Metrics**:
- Lines of Code (LOC, SLOC, Comments)
- Cyclomatic Complexity per function/method
- Cognitive Complexity scores
- Code duplication percentage
- Test coverage metrics
- Dependency coupling metrics
- Technical debt indicators

**Quality Indicators**:
- Function/method length distribution
- Class/module size metrics
- Nesting depth analysis
- Parameter count distribution
- Dead code detection
- Code smell identification

### Known Constraints
- Large repositories may require sampling
- Language-specific parsers needed
- Test coverage requires build environment

## Analysis Methodology

### Phase 1: Discovery
**Objective**: Map codebase structure and identify analysis targets

**Steps**:
1. Identify programming languages used
2. Locate source code directories
3. Find test directories and files
4. Identify build and configuration files
5. Estimate total codebase size

**Validation**:
- Language detection accuracy
- Source/test separation confirmed
- Build system identified

### Phase 2: Extraction
**Objective**: Collect raw metrics from source files

**Steps**:
1. **Basic Metrics Collection**
   - Count lines (code, comments, blank)
   - Measure file sizes
   - Track file modification history

2. **Complexity Analysis**
   - Parse AST for each file
   - Calculate cyclomatic complexity
   - Measure cognitive complexity
   - Analyze nesting depths

3. **Dependency Mapping**
   - Extract import statements
   - Build dependency graph
   - Identify circular dependencies
   - Calculate coupling metrics

4. **Quality Indicators**
   - Detect code duplication
   - Identify long methods/functions
   - Find deeply nested code
   - Locate dead code

**Data Collection Tools**:
- Language-specific AST parsers
- Complexity calculation libraries
- Duplication detection algorithms
- Static analysis tools

### Phase 3: Processing
**Objective**: Aggregate and analyze collected metrics

**Steps**:
1. **Statistical Analysis**
   - Calculate percentiles for all metrics
   - Generate distribution charts
   - Identify outliers and anomalies

2. **Trend Analysis**
   - Compare with historical data
   - Calculate metric trends
   - Project future trajectories

3. **Risk Assessment**
   - Identify high-risk components
   - Calculate maintainability index
   - Generate technical debt estimates

**Algorithms**:
- Halstead complexity measures
- Maintainability Index calculation
- SOLID principles violation detection
- Code smell pattern matching

### Phase 4: Validation
**Objective**: Ensure metric accuracy and completeness

**Steps**:
1. Cross-validate metrics with multiple tools
2. Spot-check complex calculations
3. Verify against known benchmarks
4. Validate statistical significance

## Validation Criteria

### Data Completeness
- [ ] 95%+ of source files analyzed
- [ ] All supported languages processed
- [ ] No parser failures on valid code
- [ ] Dependency graph fully connected

### Accuracy Checks
- [ ] Complexity calculations verified
- [ ] Line counts match file stats
- [ ] Duplication detection validated
- [ ] Sample manual verification passed

### Performance Metrics
- [ ] Analysis under 1 minute per 10K LOC
- [ ] Memory usage below 2GB
- [ ] Incremental analysis supported
- [ ] Parallel processing utilized

## Output Specification

### Format
**Primary Output Format**: JSON with Markdown report

### Schema
```json
{
  "summary": {
    "total_files": "number",
    "total_lines": "number",
    "languages": {
      "language": {
        "files": "number",
        "lines": "number",
        "percentage": "number"
      }
    }
  },
  "metrics": {
    "complexity": {
      "cyclomatic": {
        "average": "number",
        "median": "number",
        "p95": "number",
        "max": "number",
        "high_complexity_functions": []
      },
      "cognitive": { /* similar structure */ }
    },
    "duplication": {
      "percentage": "number",
      "duplicate_blocks": []
    },
    "maintainability": {
      "index": "number",
      "technical_debt_hours": "number",
      "risk_components": []
    }
  },
  "trends": {
    "complexity_trend": [],
    "size_growth": [],
    "quality_trajectory": []
  }
}
```

### Delivery
**Reports**:
1. **Executive Summary** (1-2 pages)
   - Key metrics dashboard
   - Risk assessment
   - Improvement recommendations

2. **Detailed Analysis** (10-20 pages)
   - Metric breakdowns by component
   - Trend analysis charts
   - Specific improvement suggestions

3. **Technical Appendix**
   - Raw metric data
   - Methodology details
   - Tool configurations

**Visualizations**:
- Complexity heatmaps
- Dependency graphs
- Trend charts
- Distribution histograms

## Error Handling

### Parser Failures
- Log unparseable files
- Continue with partial analysis
- Report parsing success rate
- Provide fallback metrics

### Resource Constraints
- Implement file sampling for large repos
- Use streaming for memory efficiency
- Support incremental analysis
- Provide resource usage warnings