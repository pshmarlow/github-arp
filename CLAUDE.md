# Claude Code Project Instructions: GitHub Analysis Scaffold

## Project Overview
This is a GitHub Analysis Context Engineering Scaffold - a specialized framework for systematic repository analysis and data extraction. It adapts the PRP (Product Requirement Prompt) methodology into ARP (Analysis Requirement Prompt) for analysis workflows.

## Core Principles

### 1. Analysis-First Approach
- **Never modify target repositories** - only analyze and extract
- **Prioritize data quality** over speed
- **Validate continuously** throughout the analysis pipeline
- **Cache intelligently** to respect API limits and improve performance

### 2. Systematic Methodology
- **Always use ARPs** for analysis tasks - never ad-hoc analysis
- **Follow the four-phase approach**: Discovery → Extraction → Processing → Validation
- **Document all assumptions** and analysis decisions
- **Generate reproducible results** with clear audit trails

### 3. GitHub API Best Practices
- **Respect rate limits** - implement exponential backoff
- **Use authenticated requests** when available for higher limits
- **Cache API responses** with appropriate TTLs
- **Batch requests** efficiently to minimize API calls

## Command Usage

### `/generate-arp INITIAL.md`
Before running this command:
1. Ensure INITIAL.md contains clear analysis objectives
2. Verify target repository accessibility
3. Check API token configuration if needed

The command will:
- Parse your analysis request
- Explore target repositories
- Generate a comprehensive ARP with all context
- Select appropriate templates based on analysis type

### `/execute-arp ARPs/analysis-name.md`
Before execution:
1. Review the generated ARP for accuracy
2. Ensure output directories exist
3. Check available disk space for large analyses
4. Verify API rate limit status

The command will:
- Load the ARP specification
- Execute the analysis in phases
- Continuously validate data quality
- Generate specified outputs and reports

### `/validate-analysis outputs/analysis-name/`
After analysis completion:
1. Always run validation before using results
2. Check the validation report for warnings
3. Address any data quality issues
4. Archive validated results

## File Organization

### ARPs Directory
- `ARPs/` - Store all generated and custom ARPs
- `ARPs/templates/` - Template library (do not modify)
- `ARPs/examples/` - Reference implementations
- Name ARPs descriptively: `{repo-name}-{analysis-type}-{date}.md`

### Data Directory
- `data/cache/` - API response cache (auto-managed)
- `data/schemas/` - Output validation schemas
- `data/raw/` - Temporary raw data storage
- Never commit large data files

### Outputs Directory
- `outputs/{analysis-name}/data/` - Analysis results
- `outputs/{analysis-name}/reports/` - Generated reports
- `outputs/{analysis-name}/logs/` - Execution logs
- Each analysis gets its own timestamped directory

## Analysis Patterns

### Code Metrics Analysis
```bash
# For code quality assessment
/generate-arp INITIAL_code_metrics.md
/execute-arp ARPs/generated_metrics_analysis.md
/validate-analysis outputs/metrics_20240115/
```

### Dependency Mapping
```bash
# For dependency analysis
/generate-arp INITIAL_dependencies.md
/execute-arp ARPs/dependency_analysis.md --cache-only  # Use cached data
```

### Pattern Extraction
```bash
# For design pattern detection
/generate-arp INITIAL_patterns.md
/execute-arp ARPs/pattern_extraction.md --resume  # Resume if interrupted
```

## Error Handling

### API Rate Limits
- The scaffold automatically handles rate limiting
- Check `outputs/logs/api_calls.log` for rate limit status
- Use `--cache-only` flag to work with cached data
- Implement analysis scheduling for large repositories

### Failed Analyses
- Always check exit codes
- Review logs in `outputs/{analysis}/logs/`
- Use `--resume` flag to continue interrupted analyses
- Partial results are saved automatically

### Validation Failures
- Address data quality issues before using results
- Re-run specific extraction phases if needed
- Check validation reports for specific issues
- Use `--fix` flag for automatic corrections where possible

## Best Practices

### 1. INITIAL.md Files
- Be specific about analysis goals
- Include example outputs if possible
- List all constraints upfront
- Reference similar analyses in examples

### 2. ARP Customization
- Start with templates, customize as needed
- Document any custom validation rules
- Include error handling strategies
- Specify output formats precisely

### 3. Performance Optimization
- Use incremental analysis for large repos
- Enable parallel processing where possible
- Monitor resource usage during execution
- Clean up cache periodically

### 4. Security Considerations
- Never commit API tokens
- Sanitize sensitive data in outputs
- Use read-only access tokens
- Audit access logs regularly

## Extending the Framework

### Custom Templates
1. Copy a base template to start
2. Modify phases for your specific needs
3. Add custom validation criteria
4. Test with small repositories first

### Custom Validators
1. Add validators to `analysis/validators/`
2. Follow the validator interface
3. Register in validation pipeline
4. Document validation rules

### Integration with CI/CD
```yaml
# Example GitHub Action
- name: Analyze Repository
  run: |
    claude-code /generate-arp .github/ANALYSIS_REQUEST.md
    claude-code /execute-arp ARPs/ci_analysis.md
    claude-code /validate-analysis outputs/latest/ --strict
```

## Troubleshooting

### Common Issues
1. **"Repository not accessible"** - Check authentication and permissions
2. **"Rate limit exceeded"** - Wait or use cached data
3. **"Validation failed"** - Review validation report details
4. **"Out of memory"** - Enable streaming mode or reduce scope

### Debug Mode
```bash
# Enable verbose logging
export ANALYSIS_DEBUG=true
/execute-arp ARPs/analysis.md --verbose
```

### Support Resources
- Check `analysis/examples/` for reference implementations
- Review logs for detailed error messages
- Consult API documentation for specific limits
- Use `--dry-run` to preview execution plans

## Maintenance

### Cache Management
```bash
# Clear cache older than 7 days
find data/cache -mtime +7 -delete

# View cache statistics
du -sh data/cache/*
```

### Log Rotation
- Logs are automatically rotated after 100MB
- Archive old logs to `outputs/archives/`
- Keep execution logs for audit purposes

### Update Checking
- Check for scaffold updates regularly
- Review template changes in updates
- Test updates with example analyses first
- Backup custom templates before updating