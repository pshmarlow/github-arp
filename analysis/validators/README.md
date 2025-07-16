# Validators

This directory contains validation modules that ensure data quality and analysis accuracy.

## Overview

Validators perform multi-level validation throughout the analysis pipeline:
- Pre-extraction validation (access, permissions)
- Data quality validation (completeness, accuracy)
- Result validation (consistency, correctness)
- Output validation (format, schema compliance)

## Creating Custom Validators

To create a custom validator, implement the base validator interface:

```python
from analysis.validators.base import BaseValidator

class MyCustomValidator(BaseValidator):
    def __init__(self, config):
        super().__init__(config)
        
    def validate_access(self, repository):
        """
        Validate repository accessibility.
        
        Args:
            repository: Repository metadata
            
        Returns:
            ValidationResult: Access validation result
        """
        # Access validation logic
        return ValidationResult(passed=True)
        
    def validate_data(self, data):
        """
        Validate data quality.
        
        Args:
            data: Data to validate
            
        Returns:
            ValidationResult: Data validation result
        """
        # Data validation logic
        return ValidationResult(passed=True, metrics={})
        
    def validate_output(self, output, schema):
        """
        Validate output against schema.
        
        Args:
            output: Analysis output
            schema: Expected schema
            
        Returns:
            ValidationResult: Schema validation result
        """
        # Schema validation logic
        return ValidationResult(passed=True)
```

## Validation Levels

### Level 1: Data Access
- Repository exists and is accessible
- Required permissions available
- API authentication valid
- Network connectivity stable

### Level 2: Extraction Quality
- Data completeness (no missing required fields)
- Data accuracy (spot checks pass)
- Extraction coverage meets threshold
- No critical extraction errors

### Level 3: Processing Validity
- Calculations mathematically correct
- Transformations preserve data integrity
- Aggregations statistically valid
- No data corruption during processing

### Level 4: Output Compliance
- Output matches specified schema
- All required fields present
- Data types correct
- File formats valid

## Available Validators

### SchemaValidator
Validates JSON outputs against JSON Schema specifications.

### MetricsValidator
Validates calculated metrics for statistical correctness.

### DependencyValidator
Validates dependency graphs for consistency.

### SecurityValidator
Checks for exposed secrets or sensitive data.

## Validation Strategies

1. **Fail-Fast**: Stop on first critical error
2. **Collect-All**: Gather all issues before failing
3. **Warning-Only**: Report issues but don't fail
4. **Progressive**: Validate incrementally during execution

## Best Practices

1. **Clear Error Messages**: Provide actionable error descriptions
2. **Validation Reports**: Generate detailed validation reports
3. **Performance**: Don't let validation slow down analysis
4. **Configurability**: Allow validation levels to be configured
5. **Recovery**: Suggest fixes for common validation failures