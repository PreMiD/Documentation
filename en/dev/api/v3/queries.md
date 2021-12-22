# Queries

## alphaBetaAccess

Type: [AlphaBetaAccess](./objects#AlphaBetaAccess)

Whether the user has access to alpha or beta versions.

### Arguments

| Name     | Type                                    | Description       |
| -------- | --------------------------------------- | ----------------- |
| `userId` | <code>[String](./scalars#String)</code> | User's Discord ID |

---

## benefits

Returns the list of staff benefits

Type: [[Benefits](./objects#Benefits)]

## This query takes no arguments

---

## betaUsers

Gives you the amount of users signed up for the PreMiD beta program

Type: [BetaUsers](./objects#BetaUsers)

This query takes no arguments

---

## credits

Returns an object array of users who have contributed to the project

Type: [Credits](./objects#Credits)

| Name     | Type                                      | Description                                                           |
| -------- | ----------------------------------------- | --------------------------------------------------------------------- |
| `id`     | <code>[String](./scalars#String)</code>   | User's Discord ID                                                     |
| `limit`  | <code>[Int](./scalars#Int)</code>         | Maximum number of users to be returned, if the `id` param is provided |
| `random` | <code>[Boolean](./scalars#Boolean)</code> | Fetches a random contibutor                                           |

---

## discordUsers

Returns an array of users in the PreMiD guild

Type: [DiscordUser](./objects#DiscordUser)

| Name     | Type                                    | Description       |
| -------- | --------------------------------------- | ----------------- |
| `userId` | <code>[String](./scalars#String)</code> | User's Discord ID |

---

## downloads

Returns an array of the downloads for PreMiD

Type: [Download](./objects#Download)

| Name          | Type                                    | Description                 |
| ------------- | --------------------------------------- | --------------------------- |
| `releaseType` | <code>[String](./scalars#String)</code> | Software release life cycle |
| `token`       | <code>[String](./scalars#String)</code> |                             |

---

## langFiles

Gives you

Type: [LangFile](./objects#LangFile)

| Name       | Type                                    | Description            |
| ---------- | --------------------------------------- | ---------------------- |
| `lang`     | <code>[String](./scalars#String)</code> | Locale of the language |
| `project`  | <code>[String](./scalars#String)</code> |
| `presence` | <code>[String](./scalars#String)</code> |

---

## partners

Returns an array of PreMiD's Partners

Type: [Partner](./objects#Partner)

| Name   | Type                                    | Description         |
| ------ | --------------------------------------- | ------------------- |
| `name` | <code>[String](./scalars#String)</code> | Name of the Partner |

---

## presences

Returns a Presence

Type: [Presence](./objects#Presence)

| Name          | Type                                    | Description                                |
| ------------- | --------------------------------------- | ------------------------------------------ |
| `service`     | <code>[String](./scalars#String)</code> | Name of the presence                       |
| `author`      | <code>[String](./scalars#String)</code> | Author of the presence                     |
| `contributor` | <code>[String](./scalars#String)</code> | Users who have contributed to the presence |
| `start`       | <code>[Int](./scalars#Int)</code>       |                                            |
| `limit`       | <code>[Int](./scalars#Int)</code>       |                                            |
| `query`       | <code>[String](./scalars#String)</code> | Query to request a specific presence       |
| `tag`         | <code>[String](./scalars#String)</code> | Tags for the presence                      |

---

## sponsors

Returns array of the sponsors of PreMiD

Type: [[Sponsor](./objects#Sponsor)]

This query takes no arguments

---

## usage

Returns an integer of the number of users for the given presence

Type: [Usage](./objects#Usage)

This query takes no arguments

---

## versions

Returns the latest versions for the extension and application for each platform

Type: [Versions](./objects#Versions)

This query takes no arguments

---

## jobs

Returns the vacant jobs

Type: [Job](./objects#Job)

This query takes no arguments

---

## changelog

This query has been deprecated and no longer works{.is-danger}

---
