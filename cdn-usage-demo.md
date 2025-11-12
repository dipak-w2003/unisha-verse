# Accessing Files via GitHub / CDN

## Option A: Direct GitHub raw URLs
- Each file can be accessed using the “raw” link:

```text
https://raw.githubusercontent.com/<username>/<repo-name>/main/<path-to-file>

```

- Example:
```text
https://raw.githubusercontent.com/dipaktamang/unisha-verse/main/projects/project-a/images/cake.png
```

- Drawback: slower load, no caching, no CDN optimizations.

## Option B: Use jsDelivr CDN (Recommended)
- jsDelivr caches your files globally and delivers them fast.
- Format:

```text
https://cdn.jsdelivr.net/gh/<username>/<repo-name>@<branch>/<path-to-file>
```

- Example:
```text
https://cdn.jsdelivr.net/gh/dipaktamang/unisha-verse@main/projects/project-a/images/cake.png
```

- `@main` can be replaced with a commit hash or tag for version control.
- Browsers will cache these files, so repeated visits are fast.


# Use Files in Your Frontend Project
- Images:
```tsx
<img src="https://cdn.jsdelivr.net/gh/dipaktamang/unisha-verse@main/projects/project-a/images/cake.png" alt="Cake" />
```

- Audio/Video:
```tsx
<audio controls>
  <source src="https://cdn.jsdelivr.net/gh/dipaktamang/unisha-verse@main/projects/project-a/music/song.mp3" type="audio/mpeg" />
</audio>
```


- Lottie / JSON Animations
```tsx
import Lottie from "lottie-react";
<Lottie animationData={require("https://cdn.jsdelivr.net/gh/dipaktamang/unisha-verse@main/projects/project-a/animations/confetti.json")} />

```
  - Tip: For Lottie, you might need to `fetch` JSON via fetch and then pass it to Lottie instead of using `require`



# Optional: Versioning
- If you plan to update assets often, consider tagging versions:
```bash
git tag project-a-v1
git push --tags
```

- Then reference a specific version in jsDelivr URLs:
```rust
https://cdn.jsdelivr.net/gh/dipaktamang/unisha-verse@project-a-v1/projects/project-a/images/cake.png
```

This ensures your frontend doesn’t break when you update assets later.
