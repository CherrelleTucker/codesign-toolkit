# Tool Proposal Workflow

This document outlines the process for proposing, reviewing, and approving new tools for the Co-Design Toolkit.

## Overview

Tool proposals are submitted as **GitHub Discussions** to allow community input and refinement before development begins. This ensures that new tools are well-thought-out, meet real needs, and have community support.

## Process

### 1. Submission (Community Member)

- Navigate to the **Discussions** tab in the repository
- Click **New Discussion**
- Select the **Tool Proposal** category
- Fill out the tool proposal template with details about:
  - What the tool is and what problem it solves
  - Who would use it and when
  - How it might be implemented
- Submit the discussion

### 2. Community Feedback (Open to All)

- Community members can:
  - Ask clarifying questions
  - Suggest improvements or alternatives
  - Share related use cases
  - Upvote/react to show interest
  - Offer to help with development

- Proposer should:
  - Respond to questions
  - Refine the proposal based on feedback
  - Update the discussion with new information

### 3. Review (Maintainers)

Project maintainers will review proposals considering:

- **Need**: Does this solve a real problem in co-design work?
- **Fit**: Does it align with the toolkit's goals and existing tools?
- **Feasibility**: Can this be built with available resources?
- **Community Support**: Is there interest and engagement from the community?
- **Clarity**: Is the proposal well-defined enough to move to development?

Maintainers will add labels to track review status:
- `under-review` - Being actively reviewed
- `needs-clarification` - Requires more information
- `approved` - Ready for development
- `deferred` - Good idea but not right now
- `declined` - Does not fit the toolkit at this time

### 4. Decision

**If Approved:**
1. Maintainer marks the discussion as **Answered** or adds `approved` label
2. A new GitHub **Issue** is created referencing the discussion
3. The issue is added to the project roadmap
4. Development can begin (either by the proposer, maintainers, or contributors)

**If Declined or Deferred:**
1. Maintainer provides clear explanation in the discussion
2. Discussion is marked with appropriate label (`declined` or `deferred`)
3. Discussion remains open for future reference

## Timeline

- **Initial Response**: Maintainers aim to acknowledge new proposals within 1 week
- **Review Timeline**: Full review typically takes 2-4 weeks depending on complexity
- **Community Feedback Period**: Minimum 1 week for community input before final decision

## Tips for Great Proposals

1. **Be Specific**: Clearly define the problem and how the tool solves it
2. **Show Examples**: Reference similar tools or provide mockups if possible
3. **Explain Use Cases**: Help reviewers understand when and how it would be used
4. **Engage with Feedback**: Respond to questions and be open to refinement
5. **Offer to Help**: Proposals with committed contributors are more likely to be prioritized

## Converting a Discussion to an Issue

When a tool proposal is approved, maintainers will:

1. Create a new issue with:
   - Title: `[Tool] Tool Name`
   - Labels: `tool`, `approved-proposal`, and relevant category labels
   - Description linking back to the original discussion
   - Implementation checklist based on the proposal

2. Reference in the discussion:
   ```
   ✅ This proposal has been approved!

   Development issue: #[issue-number]
   ```

3. Close or lock the discussion (optional) to move conversation to the issue

## Questions?

If you have questions about the tool proposal process, please:
- Review existing tool proposal discussions for examples
- Ask in the General Discussions category
- Contact the maintainers directly
