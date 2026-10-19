# Browser workflow

Read the active browser tool's documentation before using its APIs; tool names and handles vary by environment. Use only the supported browser-control surface. These are observed Pro UI landmarks, not permanent selectors or a guarantee of feature availability for every account.

## Entry and editor

- Start at `https://app.grammarly.com/` or an explicitly supplied Grammarly document.
- The Docs screen includes `New doc`, `Upload`, document search, and a Pro badge.
- `New doc` can redirect to `https://coda.grammarly.com/d/...`; this has been observed as Grammarly's editor. Follow the actual navigation and verify the title and editable content.
- The editor has a `Document name` field and a page editor, observed as `Untitled page editor` in a new document. AI Chat has a separate text entry area: identify the editor by its current accessible label, never the first generic contenteditable element.
- Use fresh accessibility state or DOM snapshots after interactions. Numeric element IDs and document URLs must be discovered each session.
- A new document or analysis can first show a loading screen. Check the fresh state before deciding the operation failed. Avoid reloading or inserting twice while navigation is pending.

## Visible agents

The right-side agent controls include `Grammarly`, `AI Detector`, `AI Rewriter`, `Humanizer`, `Paraphraser`, `Citation Finder`, `Plagiarism Checker`, and `Word Count`. Additional agents may appear. Select the requested agent by its current visible name.

### Grammarly

`Proofread` and `Strengthen writing` are separate views. Proofread can show Grammar, Clarity, and Delivery filters and individual suggestion cards. A score in the document toolbar is labeled `Overall score`; the panel can show `Writing quality`. Capture the labels as displayed rather than assuming the scores are interchangeable.

Do not accept a temporary empty suggestions list as completed analysis. Wait for suggestions or an explicit completed result.

### AI Detector

The panel can start with `Analyzing your text`, then display a percentage and explanation, such as `No AI-generated text detected`. Keep any prose explanation alongside the number where useful. Do not submit accuracy-feedback buttons as part of scoring.

### Plagiarism Checker

The panel has a Citation Style selector and can initially show `Analyzing your text`. Wait for completion, then inspect the result and sources. A completed check can show `No copied text detected` with a displayed percentage. Do not change the citation style unless requested or needed for the user's stated output. If the check remains unavailable, say so; do not treat an empty result or spinner as 0%.

### Humanizer and other rewrite agents

Humanizer is a native Grammarly agent where available. It may first show placeholder controls while loading. Voices observed: The Naturalist, The Precisionist, The Everyday Voice, The Executive, and The Scholar; it also offers custom voice controls. Creating or training a custom voice is separate from selecting an existing voice.

Preserve the original before voice selection, since agent behavior may change and the selection may modify content. In the observed workflow, selecting The Everyday Voice showed `Applying the voice`, then an inline rewrite preview with `Accept`, `Dismiss`, and individual undo controls. The original editor value remained unchanged before acceptance. Review evidential wording carefully: changing “the survey suggests” to “the results show” can strengthen a claim. Never infer successful application from a selected voice or a completed preview.

## Completion

Read back edited content, not just the insertion call's success. Verify the original and revised versions are distinguishable and scores correspond to the version checked. Keep the final result tab using the browser's deliverable marking API. Capture final browser evidence through the documented screenshot API.
