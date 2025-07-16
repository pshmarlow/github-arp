# Analysis Requirement Prompt: Pattern Extraction

## Analysis Goal
Identify and catalog design patterns, anti-patterns, architectural patterns, and coding conventions used throughout the codebase to understand design decisions and identify improvement opportunities.

## Target Repositories
- **Primary Repository**: [owner/repo-name@main]
- **Pattern Library Reference**: [optional: reference implementation]
- **File Patterns**: Source code files, focusing on architectural boundaries

## Context

### Repository Background
[Repository-specific context will be filled during ARP generation]

### Data Requirements
**Design Patterns**:
- Gang of Four patterns (Singleton, Factory, Observer, etc.)
- Architectural patterns (MVC, MVP, MVVM, etc.)
- Domain patterns (Repository, Service, DTO, etc.)
- Concurrency patterns (Producer-Consumer, Thread Pool, etc.)

**Anti-Patterns**:
- God Class/God Object
- Spaghetti Code
- Copy-Paste Programming
- Magic Numbers/Strings
- Circular Dependencies
- Feature Envy
- Data Clumps

**Code Conventions**:
- Naming patterns and conventions
- File organization patterns
- Comment patterns
- Error handling patterns
- Testing patterns

### Known Constraints
- Pattern detection accuracy varies by language
- Some patterns require semantic analysis
- Performance overhead for large codebases

## Analysis Methodology

### Phase 1: Discovery
**Objective**: Understand codebase structure and pattern contexts

**Steps**:
1. Map architectural layers and boundaries
2. Identify core domain models
3. Locate pattern-heavy directories
4. Find framework-specific patterns
5. Discover custom pattern implementations

**Validation**:
- Architecture mapping complete
- Key components identified
- Pattern hotspots located

### Phase 2: Extraction
**Objective**: Detect and catalog patterns in the codebase

**Steps**:
1. **Structural Pattern Detection**
   - AST analysis for class relationships
   - Interface implementation mapping
   - Inheritance hierarchy analysis
   - Composition pattern detection

2. **Behavioral Pattern Detection**
   - Method call graph analysis
   - Event/listener registration patterns
   - Command pattern identification
   - State machine detection

3. **Anti-Pattern Detection**
   - Complexity hotspot analysis
   - Coupling measurement
   - Cohesion analysis
   - Code smell detection

4. **Convention Analysis**
   - Naming pattern extraction
   - Code style consistency check
   - Comment pattern analysis
   - Project structure patterns

**Detection Techniques**:
- AST pattern matching
- Graph analysis algorithms
- Machine learning classifiers
- Rule-based detection
- Heuristic analysis

### Phase 3: Processing
**Objective**: Analyze and contextualize detected patterns

**Steps**:
1. **Pattern Validation**
   - Confirm pattern implementations
   - Rate implementation quality
   - Identify incomplete patterns
   - Find pattern variations

2. **Context Analysis**
   - Map patterns to components
   - Analyze pattern density
   - Identify pattern clusters
   - Track pattern evolution

3. **Impact Assessment**
   - Calculate pattern coverage
   - Measure pattern effectiveness
   - Identify refactoring opportunities
   - Estimate improvement potential

**Analysis Methods**:
- Pattern similarity scoring
- Implementation quality metrics
- Pattern co-occurrence analysis
- Temporal pattern analysis

### Phase 4: Validation
**Objective**: Ensure pattern detection accuracy

**Steps**:
1. Manual verification of sample patterns
2. Cross-reference with documentation
3. Validate against known patterns
4. Check for false positives

## Validation Criteria

### Data Completeness
- [ ] All source files scanned
- [ ] Pattern coverage >80%
- [ ] Anti-pattern detection complete
- [ ] Convention analysis finished

### Accuracy Checks
- [ ] 90%+ precision on known patterns
- [ ] Low false positive rate (<5%)
- [ ] Manual spot checks passed
- [ ] Expert review validated

### Performance Metrics
- [ ] Analysis completed within limits
- [ ] Memory usage acceptable
- [ ] Incremental detection working
- [ ] Results reproducible

## Output Specification

### Format
**Primary Output Format**: JSON with visual pattern maps

### Schema
```json
{
  "patterns": {
    "design_patterns": [{
      "type": "string",
      "category": "creational|structural|behavioral",
      "instances": [{
        "location": "file:line",
        "confidence": "number",
        "implementation_quality": "high|medium|low",
        "participants": {
          "role": "class_name"
        }
      }]
    }],
    "anti_patterns": [{
      "type": "string",
      "severity": "critical|high|medium|low",
      "instances": [{
        "location": "file:line",
        "description": "string",
        "refactoring_suggestion": "string",
        "effort_estimate": "hours"
      }]
    }],
    "architectural_patterns": [{
      "pattern": "string",
      "components": ["string"],
      "coverage": "percentage",
      "consistency": "percentage"
    }]
  },
  "conventions": {
    "naming": {
      "patterns": {},
      "violations": []
    },
    "structure": {
      "patterns": {},
      "inconsistencies": []
    }
  },
  "statistics": {
    "pattern_density": "number",
    "anti_pattern_ratio": "number",
    "consistency_score": "number"
  }
}
```

### Delivery
**Reports**:
1. **Pattern Catalog**
   - All detected patterns with examples
   - Implementation quality ratings
   - Usage statistics

2. **Anti-Pattern Report**
   - Priority-ranked issues
   - Refactoring recommendations
   - Effort estimates

3. **Architecture Overview**
   - Visual pattern maps
   - Component relationships
   - Pattern distribution

**Visualizations**:
- Pattern relationship graphs
- Anti-pattern heat maps
- Architecture diagrams
- Pattern evolution timeline

## Error Handling

### Detection Failures
- Log unanalyzable code sections
- Provide partial results
- Flag uncertain detections
- Suggest manual review

### Pattern Ambiguity
- Report confidence scores
- List alternative interpretations
- Provide context for decisions
- Enable manual override

### Performance Issues
- Implement sampling strategies
- Use caching for expensive operations
- Support distributed analysis
- Provide progress indicators

## Additional Considerations

### Language-Specific Patterns
- Framework-specific patterns
- Idiom detection
- Language best practices
- Platform conventions

### Evolution Tracking
- Pattern introduction dates
- Pattern modification history
- Deprecation patterns
- Migration patterns

### Quality Metrics
- Pattern implementation scores
- Consistency measurements
- Maintainability impact
- Technical debt correlation