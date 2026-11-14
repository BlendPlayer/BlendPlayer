# Blend Player Experience Data

This public GitHub repository stores the GitHub copies of Blend Player Experience JSON. The application and its backend source belong to the [Blend Player application directory](https://github.com/mytech-today-now/slideshow-playlist-player.html/tree/main/src/blend.v5.0.11%20-%20Copy).

## Public data notice

This repository is public. Anyone can read every Experience JSON file stored here and its complete Git history. Deleting a file removes the live file from the latest revision, but earlier versions remain in history. Do not store confidential or personal information in these files.

The GUID is the permanent storage identity and path key. It is not an authentication credential. The backend must authorize users independently of their GUID.

## Experience file format

The planned path for an Experience is:

    experiences/{guid}/experience.json

The file must preserve the application's existing player.blend.experience.v2 format. Provider credentials, admin state, user registries, generated manifests, and logs do not belong in this repository.

## Repository role

This repository is for the GitHub copies of Experience files. It does not contain the application or backend source code. Backend code and deployment configuration are maintained in the Blend Player application directory linked above.

## Status

The Experience storage integration is still planned work. Provider writes, authentication, deletion, Bitbucket storage, and deployment behavior are not implemented or verified by this repository documentation.
