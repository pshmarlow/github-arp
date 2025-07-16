# Analysis Request: Next.js Performance and Bundle Size Analysis

## OBJECTIVE
Analyze the Next.js repository to understand bundle size trends, identify performance bottlenecks in the build system, and provide recommendations for reducing client-side JavaScript payload.

## REPOSITORIES
**Target Repository**: vercel/next.js
**Branch/Tag**: canary
**Comparison Branch**: v13.5.0 (last major release)

## EXPECTED OUTPUTS
- [x] Bundle size metrics report (JSON)
- [x] Performance bottleneck analysis (Markdown)
- [x] Visual charts showing size trends
- [x] Optimization recommendations document
- [x] Raw webpack stats data
- [x] Executive summary (2 pages)

## SPECIFIC QUESTIONS TO ANSWER
1. What is the current size of core Next.js bundles, and how has it changed since v13.5.0?
2. Which packages contribute most to the client-side bundle size?
3. Are there any duplicate dependencies that could be deduplicated?
4. What are the top 5 largest dependencies and are there smaller alternatives?
5. How much of the bundle is actually used in a typical Next.js application?
6. What's the impact of enabling/disabling specific Next.js features on bundle size?
7. Are there any performance regressions in the build pipeline since the last major version?

## CONSTRAINTS
- **Time Limit**: Complete analysis within 2 hours
- **API Rate Limits**: Use authenticated requests (5000/hour limit)
- **Data Scope**: Focus on packages/ directory, exclude tests and examples
- **Build Analysis**: Only analyze production builds, not development

## EXAMPLES
- See `analysis/examples/webpack-bundle-analysis.md` for bundle analysis patterns
- Similar analysis done for React: `outputs/2024-01-05-react-bundle/`
- Reference Webpack Bundle Analyzer reports format

## ADDITIONAL CONTEXT
- Next.js uses a monorepo structure with multiple packages
- The build system uses Webpack 5 and SWC for compilation
- Some packages are meant for server-side only (should not be in client bundles)
- The team is particularly interested in the impact of the App Router on bundle size
- Results will be used to prioritize optimization work for Next.js 15
- Please highlight any "quick wins" that could reduce bundle size significantly