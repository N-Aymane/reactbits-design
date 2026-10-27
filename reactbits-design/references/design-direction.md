# Design direction and composition

## Complete pages

Start with audience, primary action, real content, and any supplied visual reference. Establish hierarchy, type scale, spacing rhythm, palette, and image treatment before selecting animation. Follow an existing design system when present; otherwise choose a direction that fits the brief instead of imposing dark backgrounds, neon gradients, glass cards, or bento grids universally.

Give prominent motion a clear role. A headline reveal can support an introduction; a background can establish atmosphere; a card interaction can help explore media. Keep secondary motion quieter so effects do not compete with the main content. Avoid stacking multiple independent text, pointer, and background effects in one focal area unless the brief specifically benefits from it.

## Existing interfaces

Inspect the current page before editing. Preserve its tokens, typography, spacing, information hierarchy, and working interactions. Prefer a localized addition or an existing component's customization surface. If an effect requires a larger layout change, explain the reason and keep the change proportional to the request.

## Selection criteria

- Choose by the content and interaction needed, then verify the component's actual behavior and API.
- Prefer simpler effects when they provide the same visual benefit with less runtime cost.
- Keep navigation and primary actions recognizable and operable throughout transitions.
- Let text remain legible without waiting for long reveals. Avoid repeatedly animating content the user is actively reading.
- Customize examples to the brand. Do not add unrelated decorative sections just to display more components.

## Motion and accessibility

Honor prefers-reduced-motion with readable static states or gentler alternatives. Ensure content is visible when animation is disabled; removing a transition while leaving opacity at zero is not a fallback. For JavaScript, canvas, and WebGL motion, disable or simplify the actual animation path rather than relying only on CSS.

Keep meaningful text and controls in semantic DOM. Hide purely decorative canvases and duplicate visual text from assistive technology while retaining one accessible representation. Preserve focus visibility and contrast across animated states. Hover may enhance an interaction, but essential content and actions must also work through touch and keyboard.
