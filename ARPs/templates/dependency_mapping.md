# Analysis Requirement Prompt: Dependency Mapping

## Analysis Goal
Create a comprehensive map of internal and external dependencies, analyze dependency health, identify vulnerabilities, and provide insights for dependency management and architecture optimization.

## Target Repositories
- **Primary Repository**: [owner/repo-name@main]
- **Monorepo Packages**: [if applicable, list sub-packages]
- **Scope**: Include all dependency types (build, runtime, dev, optional)

## Context

### Repository Background
[Repository-specific context will be filled during ARP generation]

### Data Requirements
**Dependency Information**:
- Direct dependencies (first-level)
- Transitive dependencies (full tree)
- Version constraints and ranges
- License information
- Security vulnerabilities
- Update availability
- Dependency size/weight

**Relationship Mapping**:
- Internal module dependencies
- Cross-package dependencies (monorepos)
- Circular dependency detection
- Dependency depth analysis
- Critical path identification

**Quality Metrics**:
- Outdated dependency count
- Security risk assessment
- License compatibility
- Bundle size impact
- Maintenance status

### Known Constraints
- Private package access limitations
- Large dependency trees may need pruning
- Security scanning API rate limits

## Analysis Methodology

### Phase 1: Discovery
**Objective**: Identify all dependency sources and types

**Steps**:
1. Locate dependency manifests (package.json, requirements.txt, go.mod, etc.)
2. Identify build system files
3. Find lock files for exact versions
4. Detect vendored dependencies
5. Discover git submodules

**Validation**:
- All manifest files found
- Build systems identified
- Lock files matched to manifests

### Phase 2: Extraction
**Objective**: Build complete dependency graph

**Steps**:
1. **Manifest Parsing**
   - Extract direct dependencies
   - Parse version constraints
   - Identify dependency types
   - Extract metadata

2. **Transitive Resolution**
   - Build full dependency tree
   - Resolve version conflicts
   - Track dependency paths
   - Calculate tree depth

3. **Internal Analysis**
   - Map module imports
   - Build internal dependency graph
   - Track cross-module usage
   - Identify module boundaries

4. **Metadata Collection**
   - Fetch package metadata
   - Collect license information
   - Check security databases
   - Gather size metrics

**Data Sources**:
- Package registries (npm, PyPI, etc.)
- Security databases (NVD, Snyk, etc.)
- License databases
- GitHub repository data

### Phase 3: Processing
**Objective**: Analyze dependency health and risks

**Steps**:
1. **Vulnerability Analysis**
   - Cross-reference with CVE databases
   - Calculate risk scores
   - Identify affected paths
   - Suggest remediation

2. **Update Analysis**
   - Check latest versions
   - Analyze breaking changes
   - Calculate update complexity
   - Generate update plan

3. **Architecture Analysis**
   - Identify architectural layers
   - Find coupling hotspots
   - Detect abstraction violations
   - Measure modularity

4. **Impact Analysis**
   - Calculate bundle sizes
   - Measure load times
   - Analyze tree-shaking potential
   - Identify redundancies

**Analysis Algorithms**:
- Graph centrality measures
- Vulnerability scoring (CVSS)
- License compatibility matrix
- Update risk assessment

### Phase 4: Validation
**Objective**: Ensure accuracy and completeness

**Steps**:
1. Verify dependency resolution
2. Validate security findings
3. Confirm license analysis
4. Test update recommendations

## Validation Criteria

### Data Completeness
- [ ] All dependencies mapped
- [ ] Transitive tree complete
- [ ] Security scan finished
- [ ] Metadata collected

### Accuracy Checks
- [ ] Version resolution correct
- [ ] No phantom dependencies
- [ ] License detection accurate
- [ ] Vulnerability data current

### Performance Metrics
- [ ] Analysis time reasonable
- [ ] API rate limits respected
- [ ] Memory usage controlled
- [ ] Cache utilized effectively

## Output Specification

### Format
**Primary Output Format**: JSON with interactive visualizations

### Schema
```json
{
  "summary": {
    "total_dependencies": "number",
    "direct_dependencies": "number",
    "max_depth": "number",
    "total_size_mb": "number"
  },
  "dependencies": {
    "package_name": {
      "version": "string",
      "resolved": "string",
      "type": "dev|prod|peer|optional",
      "direct": "boolean",
      "dependencies": {},
      "metadata": {
        "license": "string",
        "size": "number",
        "homepage": "string",
        "repository": "string",
        "last_publish": "date"
      },
      "vulnerabilities": [{
        "id": "CVE-XXXX-XXXXX",
        "severity": "critical|high|medium|low",
        "description": "string",
        "fixed_in": "version"
      }],
      "update": {
        "latest": "version",
        "type": "patch|minor|major",
        "breaking": "boolean"
      }
    }
  },
  "internal_dependencies": {
    "module": {
      "imports": ["module"],
      "imported_by": ["module"],
      "coupling_score": "number"
    }
  },
  "issues": {
    "vulnerabilities": {
      "critical": "number",
      "high": "number",
      "medium": "number",
      "low": "number"
    },
    "outdated": {
      "major": "number",
      "minor": "number",
      "patch": "number"
    },
    "circular_dependencies": [],
    "license_conflicts": []
  }
}
```

### Delivery
**Reports**:
1. **Executive Summary**
   - Dependency health score
   - Critical vulnerabilities
   - Update recommendations
   - Architecture insights

2. **Security Report**
   - Vulnerability details
   - Remediation paths
   - Risk assessment
   - Compliance status

3. **Update Guide**
   - Prioritized update list
   - Breaking change analysis
   - Update effort estimates
   - Migration guides

**Visualizations**:
- Interactive dependency graph
- Vulnerability heat map
- Update impact diagram
- Architecture layers view
- Bundle size treemap

## Error Handling

### Registry Failures
- Use cached data when available
- Implement retry logic
- Provide offline analysis mode
- Log all failures

### Resolution Conflicts
- Document conflict details
- Suggest resolution strategies
- Provide override options
- Track unresolved issues

### Security API Limits
- Implement rate limiting
- Use API key rotation
- Cache security data
- Batch requests efficiently

## Additional Considerations

### Monorepo Support
- Cross-package dependency tracking
- Workspace protocol handling
- Local package resolution
- Build order determination

### Performance Optimization
- Incremental dependency analysis
- Parallel metadata fetching
- Efficient graph algorithms
- Smart caching strategies

### Continuous Monitoring
- Dependency change tracking
- Automated security alerts
- Update notification system
- Trend analysis support