# Installation and integration

## Fetch matching source

Use the project's existing package manager and verify current instructions in the [installation guide](https://reactbits.dev/get-started/installation). React Bits supplies JS-CSS, JS-TW, TS-CSS, and TS-TW variants. Match the project rather than introducing a second styling system for one effect.

Official command patterns, verified October 27, 2026:

```bash
npx shadcn@latest add @react-bits/SplitText-TS-TW
npx jsrepo@latest add https://reactbits.dev/r/SplitText-TS-TW
```

These are alternatives, not sequential steps. SplitText is an example; verify the selected component's identifier and command. Adapt the runner to the project's package manager. Inspect generated changes and preserve unrelated components.json settings. If a registry configuration is needed, merge this entry into existing registries:

```json
{
  "registries": {
    "@react-bits": "https://reactbits.dev/r/{name}.json"
  }
}
```

Manual installation: open the official component's Code tab, select the matching variant, copy all required source/styles/assets, and install only its documented dependencies. Resolve imports to the actual installed location. Inspect the source before changing props or lifecycle behavior. Do not assume every component uses the same animation package.

## Rendering and layout

- In server-rendered frameworks, put browser-dependent effects behind the smallest suitable client boundary. Access window, document, and browser capabilities safely. Use deferred client-only loading only when the component needs it; preserve meaningful server-rendered content and reserve its space.
- Check parent dimensions, positioning, overflow, stacking contexts, and CSS imports. Give canvas/background containers explicit usable dimensions. Keep decorative layers behind content and prevent them from intercepting pointer events.
- Preserve the existing component API when adapting a local effect. Expose additional configuration only when the task needs it; avoid a general-purpose wrapper framework for a single integration.
- Reserve media dimensions and stable layout space. Check long text, narrow viewports, content wrapping, and loading states.

## Lifecycle, input, and cost

- Clean up listeners, timers, animation frames, observers, animation contexts, and graphics resources on unmount. Check repeated mounts and development Strict Mode when the effect has lifecycle work.
- Honor reduced motion on initial render and preference changes where applicable. Render static content or avoid mounting a costly decorative effect when motion is reduced. Verify no invisible text or inaccessible controls remain.
- Provide touch and keyboard alternatives to essential hover or drag behavior. Decorative pointer effects must not replace the system cursor or prevent ordinary clicking, scrolling, selection, and focus.
- Inspect the cost of canvas/WebGL, particle counts, device pixel ratio, and continuous loops. Use lazy loading, visibility pausing, lower quality, or simpler alternatives when observed cost warrants them. Avoid global scroll hijacking unless requested.
- Where graphics support is missing or initialization fails, retain readable content and a suitable static background. Do not assume upstream components already provide these safeguards.

## Verification scenarios

1. New marketing page: verify content hierarchy and primary action before effects, matching source variants, real props, responsive composition, and successful project checks.
2. Existing React interface: verify preserved tokens and behavior, reused local source where available, no duplicate dependencies, and a localized effect that does not block controls.
3. Mobile with reduced motion: emulate a narrow viewport, touch input, and reduced motion; verify static readable content, functional actions, no horizontal overflow, and no unnecessary continuous decorative rendering.

Use browser observation for visual and interaction claims. Build/type/lint checks complement browser verification but do not replace it. Run meaningful existing tests for changed behavior; avoid tests that simply assert copied source text.
