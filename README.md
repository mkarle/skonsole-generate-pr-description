# skonsole-generate-pr-description

This GitHub Action uses Microsoft's [Semantic Kernel](https://github.com/microsoft/semantic-kernel) and [SKonsole](https://github.com/lemillermicrosoft/skonsole) and LLMs to generate pull request descriptions. It is designed to help developers save time and effort in writing pull request descriptions by automatically generating them based on the changes made in the pull request.

## Usage

To use this action, you can add the following step to your workflow:

```yaml
    - name: Generate PR description
    uses: mkarle/skonsole-generate-pr-description@v1
    with:
        pull-request-diff-url: ${{ github.event.pull_request.diff_url }}
        pull-request-number: ${{ github.event.pull_request.number }}
        token: ${{ secrets.GITHUB_TOKEN }}
        update-type:  replace
    env: # Set Azure credentials secrets as environment variables
        AZURE_OPENAI_CHAT_DEPLOYMENT_NAME: ${{ vars.AZURE_OPENAI_CHAT_DEPLOYMENT_NAME }}
        AZURE_OPENAI_API_ENDPOINT: ${{ secrets.AZURE_OPENAI_API_ENDPOINT }}
        AZURE_OPENAI_API_KEY: ${{ secrets.AZURE_OPENAI_API_KEY }}
```

This step will generate a pull request description based on the changes made in the pull request and set it as the description of the pull request.

## Inputs

This action accepts the following inputs:

- **pull-request-number** (*required*): The pull request number.

- **pull-request-diff-url** (*required*): The pull request number.

- **token** (*required*): The GitHub Token to use by this Action (e.g. secrets.GITHUB_TOKEN)

- **update-type**: How to update the PR title/body. Options are `suffix`, `prefix`, and `replace`. Defaults to `suffix`

You will need to set these environment variables:

- **AZURE_OPENAI_CHAT_DEPLOYMENT_NAME**
- **AZURE_OPENAI_API_ENDPOINT**
- **AZURE_OPENAI_API_KEY**

## Outputs

This action does not have any outputs but will modify the PR title and body

## License

This project is licensed under the MIT License. See the LICENSE file for details.