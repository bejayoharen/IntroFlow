# Onboaring Questions JSON

A variety of questions may be asked by the app when onboarding a new user. The questions, their order and grouping into pages is described by this JSON document which is returned by the server. This document also enables skip logic.

At the moment, internationalization is not supported. This could be handled either by the server returning a different document depending on the client's requested locale, or by extending this document to include text for every locale and having the client determine the best text to use.

    {
        // First we make a list of all questions we might ask:
        "questions": [
            {
                "name": "Display name of question 1"
                "id": uniqueStringId
                "type": ( "textual" | "integer" | "multi-select" | "single-select" ),
                "help": "Optional extra help info",
                // for textual and integer:
                "default": value,
                // for multi and single select:
                "options": [
                    "option 1",
                    "option 2",
                    "option 3",
                    ...
                ]
            },
            {
                "name": "Display name of question 2"
                "id": uniqueStringId
                "type": ( "textual" | "integer" | "multi-select" | "single-select" ),
                "help": "Optional extra help info",
                // for textual and integer:
                "default": value,
                // for multi and single select:
                "options": [
                    "option 1",
                    "option 2",
                    "option 3",
                    ...
                ]
            },
            ...
        ]

        // questions are then organized into pages:
        "pages": [
            {
                // title and intro should be able to reference values determined from questions:
                "title": "Page title",
                "intro": "Page intro",
                "questions": [
                    "id1",
                    "id2",
                    ...
                ]
            },
            {
                "title": "Page title",
                "intro": "Page intro",
                "show": { // optional. if included, we can limit when the page shows.
                    "condition": ( "equals" | "indexequals" | "contains" | "indexcontains" | "greaterthan" | "lessthan" )
                    "questionid": questionid,
                    "val": value
                }
                "questions": [
                    "id1",
                    "id2",
                    ...
                ]
            },
            ...
        ]
    }

