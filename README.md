# Telegram Atlas

A visual gallery of 1,000 sampled Telegram conversations, containing 153,066 supplied message records.

## Audience

This is a data proposal for humans&. The framing emphasizes multi-person understanding, knowledge sharing and coordination, informed by the lab’s stated focus on people and their relationships (https://humansand.ai/). These are candidate research uses, not demonstrated model improvements. The landing page opens with “Understand people. In conversation.” beside a real exchange from the sample, followed by a single corpus-statistics strip and the conversation gallery. The gallery lets researchers inspect original exchanges. An optional “Dataset comparisons” table under About the data compares reported message counts with TeraGram and the USC Telegram election dataset, with sources, access distinctions, and a note that raw counts are not training-ready example counts.

## Explore

Browse three conversations at a time. Search, click the visible topic buttons, choose a language, or try Surprise me. Cards preview actual original messages and open at that exchange in the full conversation. Follow a reply traces a substantive response to its parent message. Participants reveals all speakers. Conversation summaries and corpus source notes are available on demand.

The right sidebar shows statistics computed from the loaded messages: people, messages, replies, reactions, attachment records, elapsed time, activity over 12 equal time intervals, and the top five speakers’ shares of messages. Activity bars and speaker rows jump to the corresponding messages. On narrow screens, the stats are collapsed above the chat.

## Full corpus versus sample

The landing page reports 143.76 billion text messages, 622 million users, 18 million channels and 16.15 billion reactions from the [supplied corpus proposal](https://docs.google.com/document/d/1fzcF5MxTMlcaz8onwqoVjFYEMg7mz3gjzXRXG_X2VaM/edit). These are source-reported full-corpus figures, not independently audited or calculated from the sample. An expandable source note also lists the proposal’s approximate token estimates by tokenizer. The gallery and conversation statistics refer only to the supplied sample.

## Download

The complete application and all 1,000 sample conversations are included in `telegram-atlas.zip`. Download and extract it, then open the extracted `telegram-atlas` folder. Local credentials are excluded.

## Run locally

From this folder, run:

```sh
python3 server.py --port 4173
```

Open http://127.0.0.1:4173. The local server serves only `dist/` and binds only to localhost.

## Native English translation

1. Enable the Cloud Translation API and billing in a Google Cloud project and create an API key restricted to Cloud Translation API.
2. Copy `.env.example` to `.env` if the latter does not exist.
3. Add the key after `GOOGLE_CLOUD_TRANSLATION_API_KEY=` in `.env`. Alternatively set that environment variable before starting the server. The environment variable takes precedence.
4. Choose **Read in English**, then **Translate conversation**. The server reads `.env` for each request, so no restart is needed after configuring the key.

Translations appear directly in the message bubbles, including quoted replies. **View original** reveals the original underneath an individual translation; **Show original** switches the entire conversation back. Search matches both originals and translated text. Loading progress is displayed and originals remain visible until their translation arrives.

Only selected conversation message text is sent to Google when translation is requested. Speaker IDs, timestamps and other metadata stay local. Google automatically detects the source language per text, including mixed-language sessions. Machine translations can contain errors and are not research annotations. Google Cloud usage charges and quotas apply.

Translations are cached in server memory by source-text hash for this local server session and in browser memory while the page remains open. Reloading the browser reuses the server cache; restarting the server clears it. Nothing is written back to the source data.

The key stays server-side, outside `dist/`. Do not commit `.env` or include it in a download. The ZIP deliberately excludes `.env`, and all test fixtures live outside the app. A plain static web server can display the collection but cannot provide native translation.

[Google Cloud setup](https://docs.cloud.google.com/translate/docs/setup) · [Translation API reference](https://docs.cloud.google.com/translate/docs/reference/rest/v2/translate)

## Data notes

Original text and translations are escaped and rendered as inert content. English titles and summaries come from supplied curation. Participant labels are local to each session; stable pseudonymous identifiers remain strings in the underlying records. The sample is curated, not representative of Telegram or human behavior generally. Reaction counts do not establish sentiment. Attachment records are metadata only; media files were not supplied.

## Publishing

The app and sample are archived in this private GitHub repository. Website deployment remains separate. The included Python server is intended for local use; a hosted release needs a server-side translation service and appropriate access and usage controls.
