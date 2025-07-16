# Extractors

This directory contains data extraction modules for different types of GitHub repository analysis.

## Overview

Extractors are responsible for collecting raw data from GitHub repositories using various methods:
- GitHub API calls
- Git operations
- File parsing
- AST analysis

## Creating Custom Extractors

To create a custom extractor, implement the base extractor interface:

```python
from analysis.extractors.base import BaseExtractor

class MyCustomExtractor(BaseExtractor):
    def __init__(self, config):
        super().__init__(config)
        
    def extract(self, repository):
        """
        Extract data from the repository.
        
        Args:
            repository: Repository metadata object
            
        Returns:
            dict: Extracted data
        """
        # Your extraction logic here
        return extracted_data
        
    def validate(self, data):
        """
        Validate extracted data for completeness.
        
        Args:
            data: Extracted data
            
        Returns:
            bool: True if valid
        """
        # Validation logic
        return True
```

## Available Extractors

### CodeMetricsExtractor
Extracts code complexity metrics, lines of code, and other quality indicators.

### PatternExtractor
Identifies design patterns, anti-patterns, and architectural patterns.

### DependencyExtractor
Maps internal and external dependencies, creating dependency graphs.

### GitHistoryExtractor
Analyzes commit history, code churn, and contributor patterns.

## Best Practices

1. **Rate Limiting**: Always respect GitHub API rate limits
2. **Caching**: Cache API responses to avoid redundant calls
3. **Error Handling**: Gracefully handle API failures and missing data
4. **Validation**: Validate extracted data before processing
5. **Performance**: Use efficient algorithms for large repositories