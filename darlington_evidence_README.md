# Darlington Evidence

**Darlington Evidence** is a standalone, commercial-ready evidence and chain-of-custody management resource for FiveM.

**Developer:** Darlington Script  
**Contact:** [Darlington Script on Discord](https://discord.com/users/930243127812431873)  
**Version:** 1.0.0  
**Resource:** `darlington_evidence`

---

## Features

- Dark, premium Darlington Script NUI
- Case management
- Automatic case numbering (`DS-0001`, `DS-0002`, etc.)
- Evidence records attached to cases
- Evidence types and statuses
- Serial/identifier tracking
- Quantity tracking
- Storage location tracking
- Tags and searchable metadata
- Chain-of-custody history
- Check-out / return workflow
- Release workflow
- Controlled destruction workflow
- Permanent deletion protection
- Server-side permission checks
- Configurable ACE permissions
- Persistent JSON storage with no database dependency
- Audit log
- Lua exports for MDT/dispatch/other resources
- Clean configuration file
- No required third-party UI library
- No external web requests
- No telemetry or hidden callbacks
- Darlington Script branding and GitHub-ready documentation

## Requirements

- FXServer / FiveM with OneSync enabled
- A current FiveM server artifact
- No framework is required

The resource uses the modern `fxmanifest.lua` format and CfxLua/Lua 5.4 runtime.

## Installation

1. Put the `darlington_evidence` folder in your server's resources directory.
2. Make sure `data/storage.json` exists. The included file is ready to use.
3. Add this to `server.cfg`:

```cfg
ensure darlington_evidence
```

4. Add ACE permissions:

```cfg
add_ace group.police darlington.evidence allow
add_ace group.police darlington.evidence.destroy allow

add_ace group.admin darlington.evidence allow
add_ace group.admin darlington.evidence.admin allow
add_ace group.admin darlington.evidence.destroy allow
```

5. Restart the resource/server.

Open the system with `/evidence` or the configured key.

## Permissions

The default permission is:

```text
darlington.evidence
```

Admin deletion permission:

```text
darlington.evidence.admin
```

Evidence destruction permission:

```text
darlington.evidence.destroy
```

You can change these in `config.lua`.

## Storage

The default edition uses:

```text
data/storage.json
```

This makes the resource dependency-free and easy to deploy.

For larger production servers, Darlington Script can replace the storage layer with an SQL adapter while keeping the same UI and export API.

## Exports

### Get a case

```lua
local case = exports.darlington_evidence:GetCase(caseId)
```

### Get evidence

```lua
local evidence = exports.darlington_evidence:GetEvidence(evidenceId)
```

### Get all cases

```lua
local cases = exports.darlington_evidence:GetAllCases()
```

### Get all evidence

```lua
local evidence = exports.darlington_evidence:GetAllEvidence()
```

### Create a case from another resource

```lua
local case, err = exports.darlington_evidence:CreateCase({
    title = 'Robbery Investigation',
    description = 'Bank robbery investigation.',
    location = 'Downtown',
    priority = 'high'
}, 'MDT Integration')
```

## Framework Integration

The resource is intentionally standalone.

This makes it suitable for:

- QBCore
- Qbox
- ESX
- vMenu
- custom frameworks
- custom police/MDT systems

A framework-specific adapter can be added to connect jobs, ranks, callsigns, identifiers, inventory evidence items, and department permissions.

## Commercial Use

This resource is developed and maintained by **Darlington Script**.

You may deploy and sell this resource only according to the commercial license supplied with the package. Do not redistribute the source as a free public release or claim authorship.

If you resell or provide the resource as part of a server development package, the license holder remains Darlington Script unless a separate written agreement says otherwise.

## Security

Important actions are validated server-side. Client UI input is never treated as trusted permission data.

The resource does not include:

- credential collection
- hidden HTTP requests
- remote code loading
- resource infection logic
- global bans
- unauthorized file access
- obfuscated malicious code

## Support

Developer: **Darlington Script**  
Discord: [Contact Darlington Script](https://discord.com/users/930243127812431873)

For customization, framework integration, SQL storage, MDT integration, evidence item integration, photo storage, department permissions, or additional workflows, contact Darlington Script on Discord.
## Changelog

See `CHANGELOG.md`.
