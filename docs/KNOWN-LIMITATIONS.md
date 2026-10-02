# Known Limitations

- The package cannot honestly claim a completed production deployment without a configured Supabase project and external provider credentials.
- Live salary/market data is deliberately unavailable in production until a current source with date, region, currency and methodology is configured.
- Arbitrary user code execution is deliberately marked unavailable until an isolated worker/container execution service is deployed.
- GitHub OAuth setup is environment-dependent; repository analysis of explicit GitHub URLs is available where GitHub access permits.
- Full browser E2E and WCAG audits require a browser test environment.
- Some legacy non-canonical screens remain in the source archive for compatibility; the canonical shell and high-value product screens no longer depend on the Stitch mock-data layer.
