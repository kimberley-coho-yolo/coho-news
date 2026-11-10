# IT support ticket: Microsoft Forms blueprint

Folders starting with `_` aren't published on the website. Because the repository is public, though, this file can still be seen on GitHub.

The questions for each category are listed in `_data/it_support.yml` (`common_asks` and each category's `form_asks`). Build the form to match, so the website and the form say the same thing.

## Recommended: one form with branching

One form keeps all tickets in one response list and one Excel sheet.

1. **forms.office.com → New Form.** Title: `IT support request`. Add the Coho Group logo under **Style → Customise theme**, with Coho Red `#EC1B2D` as the colour.
2. **Section 1: About you.** Add the `common_asks` questions. "How much is this affecting your work?" is a **Choice** question.
3. **Question: "What do you need help with?"** (Choice, required). Use the category titles exactly:
   - Set up a new starter
   - Software problem or question
   - Laptop, phone or equipment problem
   - Sign-in, password or Authenticator
   - Access to a folder, mailbox or system
   - Something else
4. **Add one Section per category** (**+ Add new → Section**) and add that category's `form_asks` questions. Where the YAML lists `options`, use a **Choice** question with those options. Otherwise use **Text** (turn on *Long answer* for descriptions) or **Date**. Use **Upload file** for screenshots. This only works when respondents sign in, and files are saved to your OneDrive.
5. **Set up branching:** **⋯ → Branching**. On "What do you need help with?", point each answer to its section. At the end of each section, choose **End of the form**.
6. **Settings:**
   - **Who can fill out this form:** *Only people in my organisation* (records names automatically and allows file uploads).
   - Turn on **Get email notification of each response**.
   - Turn on the **receipt** so the person gets a copy of their answers.
   - Customise the thank-you message: "Thanks, IT has your request. We'll be in touch if we need more detail."
7. **Collect responses → Copy link.** Paste it into `ticket_form_url` in `_data/it_support.yml` and commit.

## Optional: skip the category question

If your Forms has **⋯ → Get pre-filled URL**, make a pre-filled link for each category with "What do you need help with?" already answered. Paste each link into that category's `form_url` in `_data/it_support.yml`. The button for that category then opens the form at the right section.

## Turning responses into tickets

- **Simple:** **Responses → Open in Excel**, and add Status, Assigned to and Resolved date columns.
- **Better, still free with Microsoft 365:** use a Power Automate flow (*When a new response is submitted*) to create a task in **Planner** or a row in a **Microsoft List**, and email the IT contractor.

## Improvement request form

This form already exists. The website uses the clean link
`https://forms.cloud.microsoft/Pages/ResponsePage.aspx?id=…`
rather than the Teams link, because the `{locale}`, `{groupId}` and other placeholders only work inside Teams.

To show the form inside the page, it must be set to **Anyone can respond**. If it's organisation-only, set `embed: false` in `_data/it_support.yml` and staff will get a button instead.
