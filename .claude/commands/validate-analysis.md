# Validate Analysis Command

Comprehensive validation of analysis outputs and data quality.

## Usage

```
/validate-analysis outputs/analysis-name/ [--schema data/schemas/output_schema.json] [--report]
```

## Validation Levels

### Level 1: Data Access Validation
- Verify all specified repositories were accessible
- Check API authentication status
- Confirm required permissions
- Validate network connectivity logs

### Level 2: Extraction Quality
- **Completeness Check**
  - All specified files processed
  - All requested metrics calculated
  - No missing data fields
  - Coverage percentage calculation

- **Accuracy Verification**
  - Sample data spot checks
  - Cross-reference with source
  - Checksum validation
  - Timestamp consistency

### Level 3: Processing Validity
- **Transformation Accuracy**
  - Algorithm output verification
  - Edge case handling
  - Data type consistency
  - Calculation correctness

- **Business Logic Validation**
  - Rules compliance
  - Threshold adherence
  - Pattern matching accuracy
  - Aggregation validity

### Level 4: Output Compliance
- **Schema Validation**
  - JSON schema compliance
  - Required fields present
  - Data type matching
  - Format specifications

- **Content Validation**
  - Output file integrity
  - Encoding verification
  - Size constraints
  - Naming conventions

## Validation Checks

### Structural Validation
```python
# Example checks performed
- File structure matches specification
- All required outputs generated
- Proper directory organization
- Metadata files present
```

### Data Quality Metrics
```python
# Quality measurements
- Null value percentage
- Duplicate detection
- Outlier identification
- Statistical consistency
```

### Performance Validation
```python
# Efficiency checks
- Execution time vs. estimates
- API call efficiency
- Cache hit rates
- Resource usage analysis
```

## Command Options

- `--schema`: Custom schema file for validation
- `--report`: Generate detailed validation report
- `--fix`: Attempt automatic fixes for common issues
- `--strict`: Fail on any validation warning
- `--metrics-only`: Only validate metrics, skip file checks

## Validation Report Format

```markdown
# Analysis Validation Report

## Summary
- Analysis Name: [Name]
- Validation Date: [Date]
- Overall Status: [PASS/FAIL/WARNING]

## Level 1: Data Access ✓
- Repositories Accessed: 5/5
- API Calls Success Rate: 98%
- Cache Utilization: 45%

## Level 2: Extraction Quality ⚠️
- Data Completeness: 95%
- Missing Files: 3
- Accuracy Score: 99.2%

## Level 3: Processing Validity ✓
- All transformations valid
- No calculation errors
- Pattern matching: 100%

## Level 4: Output Compliance ✓
- Schema validation passed
- All formats correct
- File integrity verified

## Recommendations
1. Re-run extraction for missing files
2. Update cache for better performance
3. Consider rate limit optimization
```

## Error Handling

### Common Issues and Fixes

1. **Missing Data**
   - Identify specific gaps
   - Suggest targeted re-extraction
   - Provide completion commands

2. **Schema Violations**
   - Highlight specific fields
   - Show expected vs. actual
   - Offer transformation scripts

3. **Performance Issues**
   - Identify bottlenecks
   - Suggest optimizations
   - Recommend caching strategies

## Integration with CI/CD

```yaml
# Example GitHub Actions integration
- name: Validate Analysis
  run: |
    claude-code /validate-analysis outputs/latest/ --strict
    claude-code /validate-analysis outputs/latest/ --report > validation.md
```

## Custom Validators

Support for plugin validators:
```python
# Custom validator example
class SecurityValidator:
    def validate(self, data):
        # Check for exposed secrets
        # Validate security patterns
        # Return validation results
```

## Best Practices

1. **Run After Every Analysis**: Catch issues early
2. **Use Strict Mode in CI**: Ensure quality standards
3. **Archive Validation Reports**: Track quality over time
4. **Custom Schemas**: Define project-specific requirements
5. **Incremental Validation**: Validate during long-running analyses