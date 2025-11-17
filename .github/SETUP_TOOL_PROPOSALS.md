# Setup Guide: Tool Proposal System

This guide will walk you through setting up the GitHub Discussions-based tool proposal system for your co-design toolkit.

## Prerequisites

- Repository admin access
- GitHub Discussions feature available (free for public repos)

## Step 1: Enable GitHub Discussions

1. Go to your repository on GitHub
2. Click **Settings** (top menu)
3. Scroll down to the **Features** section
4. Check the box next to **Discussions**
5. Click **Set up discussions** if prompted

## Step 2: Configure Discussion Categories

Once Discussions are enabled:

1. Go to the **Discussions** tab in your repository
2. Click on **Categories** (gear icon or manage categories)
3. Create/configure the following categories:

### Recommended Categories:

| Category Name | Description | Format |
|--------------|-------------|---------|
| **Tool Proposals** | Propose new tools for the toolkit | Discussion |
| **General** | General discussions about the toolkit | Open-ended |
| **Ideas** | Share ideas and suggestions | Open-ended |
| **Q&A** | Questions about using the toolkit | Q&A |
| **Show and Tell** | Share how you've used the tools | Open-ended |

**Important**: Make sure the "Tool Proposals" category exists and uses the **Discussion** format.

### To Create a Category:

1. Click **New category**
2. Enter category name: `Tool Proposals`
3. Enter description: `Propose new tools for the co-design toolkit`
4. Select format: **Discussion**
5. Click **Create**

## Step 3: Add Repository Labels

Add these labels to help track proposal status:

| Label | Color | Description |
|-------|-------|-------------|
| `tool-proposal` | `#0E8A16` | Proposal for a new tool |
| `under-review` | `#FBCA04` | Being reviewed by maintainers |
| `needs-clarification` | `#D93F0B` | Requires more information |
| `approved` | `#0E8A16` | Approved for development |
| `deferred` | `#CCCCCC` | Good idea, not right now |
| `declined` | `#D73A4A` | Does not fit toolkit goals |
| `help-wanted` | `#008672` | Looking for contributors |
| `tool` | `#1D76DB` | Tool development issue |

### To Add Labels:

1. Go to repository **Issues** tab
2. Click **Labels**
3. Click **New label** for each one above
4. Enter name, description, and color code
5. Click **Create label**

## Step 4: Test the Template

1. Go to **Discussions** tab
2. Click **New discussion**
3. Select **Tool Proposals** category
4. Verify the tool-proposal.yml template loads with all fields
5. Fill out a test proposal to ensure it works correctly

## Step 5: Announce the New Process

Consider creating an announcement to inform your community:

### Sample Announcement (pin in Discussions):

```markdown
# 🎉 New Tool Proposal Process!

We've updated how tool proposals work to make them more collaborative and transparent.

**What's Changed:**
- Tool proposals are now submitted as Discussions (not Issues)
- Community can provide feedback and input before development
- Clear approval process before proposals become development tasks

**How to Propose a Tool:**
1. Go to Discussions → New Discussion
2. Select "Tool Proposals" category
3. Fill out the template
4. Engage with community feedback

**Review Process:**
- Community provides feedback and input
- Maintainers review and label proposals
- Approved proposals become development issues
- See full workflow: [TOOL_PROPOSAL_WORKFLOW.md](../.github/TOOL_PROPOSAL_WORKFLOW.md)

Questions? Ask in the General category!
```

## Step 6: Update Repository Documentation

Add information about the tool proposal process to your main README or CONTRIBUTING guide:

### Example Section for README.md:

```markdown
## 💡 Proposing New Tools

Have an idea for a new co-design tool? We'd love to hear it!

**Process:**
1. Check existing [Tool Proposals](../../discussions/categories/tool-proposals) to avoid duplicates
2. Start a [New Discussion](../../discussions/new) in the Tool Proposals category
3. Fill out the proposal template
4. Engage with community feedback
5. Maintainers will review and may approve for development

See the full [Tool Proposal Workflow](.github/TOOL_PROPOSAL_WORKFLOW.md) for details.
```

## Step 7: Set Up Notifications (Optional)

To stay on top of new proposals:

1. Go to repository **Settings**
2. Click **Notifications** (in your personal settings, not repo settings)
3. Or use the **Watch** button and select **Custom** → check **Discussions**

## Step 8: Create Workflow Automation (Optional)

You can automate parts of the process with GitHub Actions. For example:

### Auto-label New Tool Proposals

Create `.github/workflows/label-tool-proposals.yml`:

```yaml
name: Label Tool Proposals

on:
  discussion:
    types: [created]

jobs:
  label:
    runs-on: ubuntu-latest
    if: github.event.discussion.category.name == 'Tool Proposals'
    steps:
      - name: Add label
        uses: actions/github-script@v7
        with:
          script: |
            github.rest.issues.addLabels({
              owner: context.repo.owner,
              repo: context.repo.repo,
              issue_number: context.payload.discussion.number,
              labels: ['tool-proposal', 'under-review']
            });
```

### Auto-create Issue from Approved Discussion

Create `.github/workflows/approved-proposal-to-issue.yml`:

```yaml
name: Create Issue from Approved Proposal

on:
  discussion:
    types: [labeled]

jobs:
  create-issue:
    runs-on: ubuntu-latest
    if: github.event.label.name == 'approved'
    steps:
      - name: Create Issue
        uses: actions/github-script@v7
        with:
          script: |
            const discussion = context.payload.discussion;
            const issue = await github.rest.issues.create({
              owner: context.repo.owner,
              repo: context.repo.repo,
              title: `[Tool] ${discussion.title.replace('[Tool Proposal] ', '')}`,
              body: `This tool was approved from discussion #${discussion.number}\n\n${discussion.body}\n\n---\n\nOriginal proposal: ${discussion.html_url}`,
              labels: ['tool', 'approved-proposal']
            });

            // Comment on discussion with issue link
            await github.rest.discussions.createComment({
              owner: context.repo.owner,
              repo: context.repo.repo,
              discussion_number: discussion.number,
              body: `✅ This proposal has been approved!\n\nDevelopment issue: #${issue.data.number}`
            });
```

## Troubleshooting

### Template Not Showing Up

- Verify file is at `.github/DISCUSSION_TEMPLATE/tool-proposal.yml`
- Check YAML syntax is valid
- Ensure "Tool Proposals" category exists
- Try refreshing the page or clearing cache

### Labels Not Working

- Ensure labels are created in the repository
- Check spelling matches exactly
- Labels can be added manually if automation fails

### Community Not Engaging

- Pin important proposals
- Share in team channels or social media
- Ask specific people for feedback
- Set expectations for response times

## Next Steps

After setup:

1. ✅ Test with a sample proposal
2. ✅ Announce to your community
3. ✅ Monitor new proposals weekly
4. ✅ Respond within your committed timeframe
5. ✅ Convert approved proposals to issues

## Questions?

If you run into issues, check:
- [GitHub Discussions Documentation](https://docs.github.com/en/discussions)
- [Discussion Templates Documentation](https://docs.github.com/en/discussions/managing-discussions-for-your-community/creating-discussion-category-forms)

---

**You're all set!** The tool proposal system is ready to help your community collaborate on new tools. 🎉
