# Analysis Requirement Prompt: React Repository Code Quality Analysis

## Analysis Goal
Perform a comprehensive code quality analysis of the React repository to understand code complexity, identify maintainability issues, and provide actionable insights for the React core team.

## Target Repositories
- **Primary Repository**: facebook/react@main
- **Comparison Baseline**: facebook/react@v18.0.0 (for trend analysis)
- **File Patterns**: 
  - Include: `packages/*/src/**/*.js`, `packages/*/src/**/*.ts`
  - Exclude: `**/__tests__/**`, `**/node_modules/**`, `**/*.test.js`

## Context

### Repository Background
React is a JavaScript library for building user interfaces, maintained by Meta. The codebase:
- Uses a monorepo structure with multiple packages
- Implements complex reconciliation algorithms
- Has extensive backwards compatibility requirements
- Follows specific coding conventions and patterns
- Contains both legacy and modern code sections

### Data Requirements
**Core Metrics**:
- Lines of Code per package and total
- Cyclomatic and Cognitive Complexity distributions
- Function length statistics
- Module coupling metrics
- Test coverage per package
- Code duplication analysis
- Technical debt hotspots

**Quality Indicators**:
- Long function identification (>50 lines)
- High complexity functions (>10 cyclomatic)
- Deeply nested code blocks (>4 levels)
- Large files (>500 lines)
- Circular dependency detection

### Known Constraints
- Large codebase requires efficient processing
- Some packages have different coding standards
- Build-time generated files should be excluded
- Flow type annotations need special handling

## Analysis Methodology

### Phase 1: Discovery
**Objective**: Map React repository structure and identify analysis scope

**Steps**:
1. Map all packages in the monorepo
2. Identify source vs generated code
3. Locate test files and fixtures
4. Find build configuration files
5. Estimate total analysis scope (~200K LOC)

**Validation**:
- All packages discovered
- Source/test separation confirmed
- Build artifacts excluded

### Phase 2: Extraction
**Objective**: Collect comprehensive metrics from React source

**Steps**:
1. **Package-Level Analysis**
   - Process each package independently
   - Extract package-specific metrics
   - Map inter-package dependencies

2. **Core Metrics Collection**
   - Parse JavaScript/TypeScript ASTs
   - Calculate complexity metrics
   - Measure code duplication
   - Extract function/class sizes

3. **React-Specific Analysis**
   - Identify React component patterns
   - Analyze hook implementations
   - Track prop drilling depth
   - Measure component complexity

4. **Historical Comparison**
   - Compare with v18.0.0 baseline
   - Track metric evolution
   - Identify improvement areas

**Data Collection**:
- Use @babel/parser for AST generation
- Apply React-aware analysis rules
- Cache parsed ASTs for efficiency

### Phase 3: Processing
**Objective**: Generate insights from collected metrics

**Steps**:
1. **Statistical Analysis**
   - Calculate percentiles for all metrics
   - Identify statistical outliers
   - Generate distribution charts

2. **Package Comparison**
   - Compare metrics across packages
   - Identify best/worst performers
   - Find common patterns

3. **Trend Analysis**
   - Calculate metric changes since v18
   - Project future trends
   - Identify improvement velocity

**Algorithms**:
- Custom React component complexity scoring
- Hook dependency analysis
- Render path complexity calculation

### Phase 4: Validation
**Objective**: Ensure analysis accuracy for React codebase

**Steps**:
1. Validate against known complex components
2. Cross-check with React team's assessments
3. Verify Flow type handling
4. Confirm monorepo boundaries

## Validation Criteria

### Data Completeness
- [ ] All packages analyzed (30+)
- [ ] 95%+ source coverage
- [ ] No parser failures on valid code
- [ ] Historical comparison complete

### Accuracy Checks
- [ ] Complexity calculations verified
- [ ] React patterns correctly identified
- [ ] Known hotspots detected
- [ ] Manual spot checks passed

### Performance Metrics
- [ ] Full analysis under 10 minutes
- [ ] Memory usage below 4GB
- [ ] Incremental mode functional
- [ ] Results reproducible

## Output Specification

### Format
**Primary Output Format**: JSON data with Markdown report and interactive dashboard

### Schema
```json
{
  "repository": "facebook/react",
  "analysis_date": "2024-01-15",
  "summary": {
    "total_packages": 35,
    "total_files": 1247,
    "total_sloc": 198453,
    "average_complexity": 4.3
  },
  "packages": {
    "react": {
      "metrics": {
        "sloc": 15234,
        "complexity": {
          "average": 3.8,
          "p95": 12,
          "max": 47,
          "high_complexity_functions": [
            {
              "name": "beginWork",
              "file": "packages/react-reconciler/src/ReactFiberBeginWork.js",
              "line": 2847,
              "complexity": 47
            }
          ]
        }
      }
    }
  },
  "trends": {
    "complexity_change": -5.2,
    "sloc_growth": 8.3,
    "duplication_change": -2.1
  },
  "recommendations": [
    {
      "type": "refactor",
      "priority": "high",
      "component": "ReactFiberBeginWork",
      "description": "Split beginWork function to reduce complexity"
    }
  ]
}
```

### Delivery
**Reports**:
1. **Executive Summary** (2 pages)
   - Overall health score: B+
   - Key improvements since v18
   - Top 5 refactoring priorities
   - Package health rankings

2. **Package Deep Dives** (30 pages)
   - Detailed metrics per package
   - Complexity hotspot maps
   - Specific recommendations
   - Code examples

3. **Interactive Dashboard**
   - Filterable metrics explorer
   - Trend visualizations
   - Drill-down capabilities
   - Export functionality

## Error Handling

### React-Specific Issues
- Handle Flow type annotations
- Process experimental syntax
- Skip generated reconciler code
- Handle version-specific features

### Monorepo Challenges
- Resolve cross-package imports
- Handle workspace protocols
- Process shared utilities
- Manage circular dependencies

## Additional Considerations

### React-Specific Patterns
- Component complexity scoring
- Hook dependency analysis
- Render optimization opportunities
- Concurrent mode considerations

### Performance Impact
- Bundle size correlation
- Runtime performance indicators
- Tree-shaking effectiveness
- Dead code identification

### Team Integration
- Generate PR-ready reports
- Provide actionable tickets
- Include code modification examples
- Align with React team standards