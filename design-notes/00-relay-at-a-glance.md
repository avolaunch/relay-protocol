# Relay at a Glance

## An Introduction to the Relay Protocol

**Version 0.1**

---

# What is Relay?

Relay is an open protocol for digital identity, personal data and application interoperability.

Its purpose is simple:

> **People should own their digital identity and data in the same way they own their email address or their house—not merely rent access to it from an application.**

Today, most digital platforms combine several independent responsibilities into a single product.

When you join a social network, note-taking app, CRM, fitness platform or AI service, that company usually becomes all of the following:

- your identity provider;
- your data store;
- your application;
- your permission system;
- your migration system;
- your backup provider.

Because these responsibilities are tightly coupled, changing one often means losing the others.

Changing applications frequently means abandoning years of history.

Changing providers often requires exporting files that cannot be used elsewhere.

Relationships, followers, permissions and workflows become trapped inside individual products.

Relay separates these concerns.

Instead of one company owning every layer, Relay defines open standards that allow each layer to be replaced independently while preserving the person's digital continuity.

---

# The Problem Relay Solves

Imagine changing banks.

Your bank account number stays the same.

Your identity stays the same.

Your transaction history can be transferred.

Your salary still belongs to you.

Now imagine changing social media platforms.

Or your note-taking software.

Or your project management system.

Or your AI assistant.

Usually you lose some combination of:

- your identity;
- your followers;
- your documents;
- your permissions;
- your history;
- your integrations;
- your reputation.

This isn't a technical limitation.

It's largely an architectural one.

Most modern applications were never designed around the idea that users should be able to leave without losing themselves.

Relay begins with the opposite assumption.

Applications are temporary.

People are not.

---

# The Core Idea

Relay separates **identity** from **applications**.

Your Relay Identity belongs to you.

Applications receive permission to interact with that identity.

Repositories store your canonical records.

Providers host those repositories.

Applications present experiences built on top of them.

Because these responsibilities are independent, replacing one does not require replacing the others.

You may decide to:

- change applications;
- move to another hosting provider;
- use several applications simultaneously;
- authorise AI assistants;
- revoke permissions;
- migrate your repository;

without changing who you are.

---

# A Different Way to Think About Applications

Traditional software often treats the application as the centre of the user's digital life.

Relay treats the person as the centre.

Applications become tools.

Just as different email clients can all access the same email account, different Relay applications can interact with the same identity and repository—provided they have the necessary permissions.

Applications compete by offering better experiences, not by making it difficult to leave.

---

# The Building Blocks

Relay is built around a small number of core concepts.

## Relay Identity

A persistent identity controlled by a person or organisation.

It remains stable even if providers or applications change.

---

## Controller

The entity with ultimate authority over a Relay Identity.

The Controller decides:

- which applications receive access;
- which providers host repositories;
- when permissions are revoked;
- when migration occurs.

---

## Repository

A repository contains the canonical records associated with a Relay Identity.

Applications may cache or extend information locally, but the repository remains the authoritative source of portable data.

---

## Provider

A Provider stores and serves repositories.

Providers compete on service quality, performance, security and trust—not on ownership of user identity.

---

## Application

Applications provide user experiences.

They do not own the user's identity.

They do not own the user's repository.

They request permission to interact with both.

---

## Permission Grant

Permission Grants define exactly what an application may do.

Permissions are explicit, limited and revocable.

Applications receive only the authority that has been granted.

---

## Record

Everything meaningful within Relay is represented as records.

Examples include:

- profiles;
- documents;
- posts;
- messages;
- tasks;
- contacts;
- playlists;
- AI conversations.

Records have stable identities and can survive application replacement.

---

## Events

Events allow applications to stay synchronised with repository changes.

Applications can disconnect, reconnect and continue operating without losing continuity.

---

# Why Not Just Export Files?

Many platforms already allow users to export data.

Relay is designed around something stronger than export.

Export gives you a copy.

Relay gives you continuity.

Continuity means:

- identifiers remain stable;
- relationships remain intact;
- permissions remain meaningful;
- history remains verifiable;
- applications continue operating after migration.

Instead of rebuilding your digital life after moving, you simply continue it.

---

# AI and Relay

Artificial intelligence makes digital ownership more important, not less.

AI systems increasingly:

- read documents;
- generate content;
- organise information;
- automate workflows;
- communicate on behalf of users.

Relay ensures that AI systems operate through explicit permission rather than implicit ownership.

An AI assistant becomes another authorised application.

It receives only the permissions required for its purpose.

Those permissions can be reviewed, limited and revoked at any time.

The user's repository remains under the Controller's authority.

---

# What Relay Is Not

Relay is not:

- a social network;
- a cloud storage provider;
- a blockchain;
- a cryptocurrency;
- a single application;
- a hosting company;
- a commercial platform.

It is an open protocol.

Just as HTTP defines how web systems communicate, Relay defines how digital identities, repositories and applications can remain interoperable without sacrificing user continuity.

---

# Design Principles

Relay is guided by several permanent principles.

## People are persistent.

Applications are replaceable.

---

## Identity belongs to the Controller.

Not the Provider.

---

## Providers compete through service.

Not lock-in.

---

## Applications compete through experience.

Not ownership.

---

## Migration is a normal operation.

Not an exceptional event.

---

## Unknown valid data should survive.

---

## Interoperability is more valuable than market dominance.

---

## Backward continuity matters.

---

## Security must strengthen ownership.

Not weaken it.

---

# A Simple Example

Alice keeps her personal knowledge base using **Application A**.

Her repository is hosted by **Provider X**.

Several years later she discovers **Application B**, which has better search, AI features and collaboration tools.

With today's software, changing applications might require exporting files, recreating workflows and abandoning years of integrations.

With Relay:

- Alice authorises Application B.
- Application B reads her existing repository.
- Her notes keep the same identifiers.
- Her relationships remain intact.
- AI history remains available.
- She revokes Application A.
- Nothing about her identity changes.

Months later she decides to move from Provider X to Provider Y.

The repository migrates.

Applications reconnect.

Her identity remains unchanged.

Her digital life continues.

---

# Who Should Care About Relay?

Relay is relevant to:

- software developers;
- application builders;
- cloud providers;
- enterprises;
- governments;
- educational institutions;
- AI platform developers;
- open-source communities;
- privacy advocates;
- standards organisations;
- anyone who has ever worried about becoming locked into a single platform.

---

# The Long-Term Vision

Relay is not trying to build another application.

It is trying to make applications replaceable.

It is not trying to replace innovation.

It is trying to make innovation safer.

The web became successful because no browser owned websites.

Email became successful because no email client owned your inbox.

Relay applies the same philosophy to digital identity and personal data.

Instead of asking:

> "Which platform owns my digital life?"

Relay asks:

> **"Why should any platform own it at all?"**

---

# Where to Go Next

This document is an introduction.

The complete technical definition of Relay is contained in the **Relay Protocol Specification**, which defines:

- architecture;
- identity;
- repositories;
- permissions;
- providers;
- applications;
- migration;
- events;
- verification;
- conformance;
- governance.

Together, these documents describe a protocol designed to preserve one idea above all others:

> **Technology should evolve. Your digital self should not have to start over every time it does.**