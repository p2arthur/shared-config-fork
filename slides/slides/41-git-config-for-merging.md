---
layout: two-cols-header
---

# Git Config for Merging

::left::

### Why Git Config Is Still Needed

**Two different concerns:**

- **Authentication** (GitHub App token) → "Can I push?"
- **Identity** (git config) → "Who is committing?"

**GitHub App token alone = incomplete**
- Token proves authorization to push
- Git still needs author name/email for commit metadata

**Error you'll see:**
```
Author identity unknown
```

::right::

### The Fix

```yaml
# release.yml (lines 207-211)
- run: |
    # Set identity (who is committing)
    git config user.name \
      "${{ steps.bot-token.outputs.app-slug }}[bot]"
    git config user.email \
      "${{ secrets.BOT_ID }}+\
      ${{ steps.bot-token.outputs.app-slug }}[bot]\
      @users.noreply.github.com"

    # Now commit works (has both auth + identity)
    git merge origin/${{ github.ref_name }} \
      -m "chore: merge..."
    git push origin main
```

**Key insight:** Token = keycard to building, git config = name badge

<!--
Even with a valid GitHub App token, you still need git config. Think of it this way: the token is your keycard to the building (proves you can push), but git config is your name badge (identifies who's committing). The bot-token action outputs an app-slug we use for consistent naming, and the email format combines the App ID with app-slug for the noreply address. Without git config, git refuses to create commits with an "Author identity unknown" error, even though the token would allow pushing.
-->
