name: Bugbot AI Reviewer
on:
  pull_request:
    types: [opened, synchronize]

jobs:
  review:
    runs-on: ubuntu-latest
    steps:
      - name: Generate Bugbot Token
        id: app-token
        uses: actions/create-github-app-token@v1
        with:
          app-id: 5204152
          private-key: ${{ secrets.BUGBOT_PRIVATE_KEY }}
          
      - name: Crush Bugs - AI Review
        uses: Seskakiller/Bugbot@main
        with:
          token: ${{ steps.app-token.outputs.token }}
