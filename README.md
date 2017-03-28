# IntroFlow

This project implements a simplified onboarding process that works as follows:

- The app requests a [JSON document](onboarding-json.md) from the server (currently mocked).
- The app buils a list of potential questions and pages to show the user.
- The app displays a series of pages asking the user questions. Which pages get shown may depend on prior answers.
- Upon completion, the app starts over, to enable easy human testing.
