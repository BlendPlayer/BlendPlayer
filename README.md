# Blend Player Backend

This repository is the planned server-side component for Blend Player. The browser application is currently served at [mytech.today/tools/player/v](https://mytech.today/tools/player/v/index.html) and is designed to work locally.

## Project status

This repository is at its initial setup stage. It does not yet contain an API implementation, provider integration, automated tests, or deployment configuration. The behavior described below is planned work, not a deployed or verified service.

## Planned responsibilities

The backend is intended to:

- Accept, validate, retrieve, and delete a user's Experience JSON.
- Keep the existing player.blend.experience.v2 format compatible with the browser application.
- Synchronize each Experience independently to the selected GitHub and Bitbucket repositories and report each provider's result.
- Provide user and administrative operations through authenticated server endpoints.
- Keep provider credentials, session credentials, and administrative secrets on the server.

The planned provider data path is experiences/{guid}/experience.json. The GUID is the stable storage identity and path key. It must not be treated as the user's authentication credential.

## Security and privacy requirements

- Authenticate and authorize each request on the server. Knowledge of a GUID alone must not grant access.
- Assume Experience files in public repositories can be read by anyone. Do not use public files for confidential or personal data.
- Keep provider tokens, OAuth secrets, signing keys, admin keys, and session secrets out of source control, browser storage, frontend bundles, logs, and API responses.
- Keep user registries, administrative state, generated manifests, and logs out of the Experience data repositories.
- Validate GUIDs, request sizes, Experience schemas, origins, and authorization before provider operations.
- Preserve provider history when updating or deleting a live Experience file.

## Compatibility goals

Cloud storage is optional. The browser application should retain its existing local playback, import, export, and offline behavior when the backend is unavailable. A provider failure should be reported separately and should not be presented as a successful sync.

The backend must preserve the existing Experience JSON format unless a separately reviewed migration is approved.

## Hosting direction

The account owner reports that the cPanel account exposes Node.js instances, PHP and Python settings, scheduled jobs, outgoing connection controls, Redis, and Supervisor. Node.js is the current hosting direction for this service. The exact Node.js version, process limits, request routing, secret configuration, database or session storage, and provider connectivity still need confirmation with the host.

The frontend URL above does not establish the backend API URL. Choose and verify the API route and same-origin or cross-origin policy before deployment. Production credentials and provider configuration must be provisioned through the host's protected settings.

## Decisions still required

Before implementing provider writes, confirm:

- The GitHub and Bitbucket repositories that will store Experience files, including their visibility.
- How users authenticate independently of their GUID.
- The backend API origin and the cPanel account's runtime, storage, and resource limits.
- The provider application, permission, and token configuration, verified against current official documentation.

## Development

No runtime dependencies, package scripts, test commands, or deployment steps are defined yet. Add them when the backend implementation is selected and keep this document aligned with verified behavior.
