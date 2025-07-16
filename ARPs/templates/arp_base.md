# Analysis Requirement Prompt: [Analysis Name]

## Analysis Goal
[Clearly state what insights or data need to be extracted from the target repositories. Be specific about the questions this analysis should answer.]

## Target Repositories
- **Primary Repository**: [owner/repo-name@branch]
- **Additional Repositories**: 
  - [owner/repo2-name@branch]
  - [owner/repo3-name@branch]
- **Commit Range**: [optional: specific commit range or date range]
- **File Patterns**: [optional: specific file patterns to focus on]

## Context

### Repository Background
[Provide relevant context about the repositories being analyzed:
- Technology stack
- Project type and purpose
- Known architectural patterns
- Team size and development practices
- Any special considerations]

### Data Requirements
[Specify exactly what data needs to be collected:
- Metrics and measurements
- Patterns to identify
- Relationships to map
- Historical trends to track
- Specific code constructs to analyze]

### Known Constraints
[List any limitations or special considerations:
- API rate limits
- Access restrictions
- Time constraints
- Processing limitations
- Output size limits]

## Analysis Methodology

### Phase 1: Discovery
**Objective**: Understand repository structure and validate accessibility

**Steps**:
1. Verify repository access and authentication
2. Map repository structure and key directories
3. Identify file types and counts
4. Assess codebase size and complexity
5. Check for build files and documentation

**Validation**:
- All repositories accessible
- Required permissions confirmed
- Initial size estimates calculated

### Phase 2: Extraction
**Objective**: Collect raw data from repositories

**Steps**:
1. [Specific extraction step 1]
2. [Specific extraction step 2]
3. [Specific extraction step 3]

**Data Collection**:
- Use GitHub API for metadata
- Clone repositories for deep analysis
- Cache responses for efficiency
- Handle rate limits gracefully

**Validation**:
- Data completeness checks
- Extraction error logging
- Progress tracking

### Phase 3: Processing
**Objective**: Transform and analyze collected data

**Steps**:
1. [Processing step 1]
2. [Processing step 2]
3. [Processing step 3]

**Algorithms**:
- [List specific algorithms or analysis methods]
- [Include any statistical methods]
- [Specify pattern matching approaches]

**Validation**:
- Processing accuracy checks
- Intermediate result validation
- Performance monitoring

### Phase 4: Validation
**Objective**: Ensure data quality and completeness

**Steps**:
1. Run automated validation checks
2. Perform statistical consistency tests
3. Validate against known benchmarks
4. Check output format compliance

**Quality Metrics**:
- Coverage percentage
- Accuracy score
- Completeness rating
- Performance metrics

## Validation Criteria

### Data Completeness
- [ ] All specified repositories analyzed
- [ ] Required metrics calculated
- [ ] No significant data gaps
- [ ] Minimum coverage threshold met (specify %)

### Accuracy Checks
- [ ] Sample validation passed
- [ ] Cross-reference checks completed
- [ ] Known values match expected
- [ ] Error rate below threshold (specify %)

### Performance Metrics
- [ ] Analysis completed within time limit
- [ ] API rate limits respected
- [ ] Memory usage within bounds
- [ ] Cache hit rate acceptable

## Output Specification

### Format
**Primary Output Format**: [JSON/CSV/Markdown/Custom]

**File Structure**:
```
outputs/
├── data/
│   ├── raw/           # Raw extracted data
│   ├── processed/     # Processed results
│   └── aggregated/    # Summary data
├── reports/
│   ├── summary.md     # Executive summary
│   └── detailed.md    # Detailed findings
├── visualizations/    # Charts and graphs
└── logs/             # Execution logs
```

### Schema
```json
{
  "analysis_metadata": {
    "name": "string",
    "version": "string",
    "timestamp": "ISO8601",
    "repositories": ["string"]
  },
  "results": {
    // Define specific schema for results
  },
  "validation": {
    "completeness": "number",
    "accuracy": "number",
    "warnings": ["string"]
  }
}
```

### Delivery
- **Output Location**: `outputs/[analysis-name]/`
- **Report Format**: Markdown with embedded visualizations
- **Data Export**: JSON with optional CSV conversion
- **Archive**: Compressed archive of all outputs

## Error Handling

### API Errors
- Implement exponential backoff
- Cache partial results
- Provide clear error messages
- Suggest recovery actions

### Data Quality Issues
- Log all quality issues
- Provide data quality report
- Mark questionable data
- Offer remediation steps

### Processing Failures
- Save checkpoints regularly
- Enable resume capability
- Log detailed error context
- Provide debugging information

## Additional Considerations

### Security
- Never expose API tokens
- Sanitize sensitive data
- Follow security best practices
- Audit access logs

### Performance Optimization
- Use parallel processing where possible
- Implement efficient caching
- Stream large datasets
- Monitor resource usage

### Future Extensibility
- Design for incremental updates
- Support custom extractors
- Enable plugin architecture
- Document extension points