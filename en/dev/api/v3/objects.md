# Objects

## AlphaBetaAccess

Whether the user has access to alpha or beta versions.

### Fields

| Name          | Type                          | Description                                       |
| ------------- | ----------------------------- | ------------------------------------------------- |
| `betaAccess`  | [Boolean](./scalars#Boolean)! | Whether the user has access to the beta versions  |
| `alphaAccess` | [Boolean](./scalars#Boolean)! | Whether the user has access to the alpha versions |

---

## Benefit

A benefit for working for PreMiD

| Name          | Type                         | Description                |
| ------------- | ---------------------------- | -------------------------- |
| `description` | [String](./scalars#String)!  | Description of the benefit |
| `icon`        | [String](./scalars#Boolean)! | Icon of the benefit        |
| `title`       | [String](./scalars#Boolean)! | Title of the benefit       |

---

## BetaUsers

Amount of users in PreMiD's beta program

| Name                          | Description                         |
| ----------------------------- | ----------------------------------- |
| `number` [Int](./scalars#Int) | Amount of users on the beta program |

---

## Credits

A contributor to the PreMiD project

| Name          | Type                      | Description               |
| ------------- | ------------------------- | ------------------------- |
| `highestRole` | [Role](#Role)             | User's highest role       |
| `roles`       | [[Role](#Role)]           | Array of the user's roles |
| `user`        | [CreditUser](#CreditUser) |

---

## DiscordUser

A Discord User

| Name            | Type                       | Description                       |
| --------------- | -------------------------- | --------------------------------- |
| `avatar`        | [String](./scalars#String) |                                   |
| `created`       | [Float](./scalars#Float)   | Users's account created timestamp |
| `discriminator` | [String](./scalars#String) |                                   |
| `userId`        | [String](./scalars#String) |                                   |
| `username`      | [String](./scalars#String) |                                   |

---

## Presence

A Presence

| Name         | Type                                   | Description                          |
| ------------ | -------------------------------------- | ------------------------------------ |
| `iframeJs`   | [String](./scalars#String)             | Presence's iFrame.js file            |
| `metadata`   | [PresenceMetadata](#PresenceMetadata)! | Presence's metadata                  |
| `presenceJs` | [String](./scalars#String)!            | Presence's presence.js file          |
| `url`        | [String](./scalars#String)!            | Presence's URL(s)                    |
| `users`      | [Int](./scalars#Int)!                  | Amount of users who use the presence |

---

## Sponsor

| Name          | Type                        | Description                |
| ------------- | --------------------------- | -------------------------- |
| `description` | [String](./scalars#String)! | Description of the sponsor |
| `image`       | [String](./scalars#String)! | Logo of the sponsor        |
| `name`        | [String](./scalars#String)! | Name of the sponsor        |
| `tString`     | [String](./scalars#String)! |                            |

---

## Usage

| Name    |                       | Description                           |
| ------- | --------------------- | ------------------------------------- |
| `count` | [Int](./scalars#Int)! | Amount of user's who use the presence |

---

## Versions

| Name        | Type                               | Description                            |
| ----------- | ---------------------------------- | -------------------------------------- |
| `api`       | [String](./scalars#String)!        | Latest version of the API              |
| `app`       | [String](./scalars#String)!        | Latest version of the application      |
| `bot`       | [String](./scalars#String)!        | Latest version of the Discord Bot      |
| `extension` | [String](./scalars#String)!        | Latest version of the extension        |
| `linux`     | [String](./scalars#String)!        | Latest version of the Linux version    |
| `safari`    | ([SafariVersion](#SafariVersion)!) | Latest version of the Safari extension |

---

## Partner

A Partner

| Name          | Type                        | Description                               |
| ------------- | --------------------------- | ----------------------------------------- |
| `description` | [String](./scalars#String)! | Description of the partner                |
| `image`       | [String](./scalars#String)! | Logo of the partner                       |
| `name`        | [String](./scalars#String)! | Name of the partner                       |
| `storeName`   | [String](./scalars#String)! | Presence name associated with the partner |
| `url`         | [String](./scalars#String)! | URL to the website of the parnter         |

---

## Download

A download

| Name          | Type                              | Description              |
| ------------- | --------------------------------- | ------------------------ |
| `appLinks`    | [[String](./scalars#String)]!     | Links to the application |
| `enabled`     | [Boolean](./scalars#Float)!       |                          |
| `extLinks`    | [[DownloadLink](#downloadLink)!]! | Links to the extension   |
| `releaseType` | [String](./scalars#String)!       |                          |

---

## LangFile

A language file

| Name           | Type                       | Description               |
| -------------- | -------------------------- | ------------------------- |
| `lang`         | [String](./scalars#String) | Language's Locale         |
| `presence`     | [String](./scalars#String) | **beep**                  |
| `project`      | [String](./scalars#String) | **beep**                  |
| `translations` | (JSON)                     | **FIX THE TYPE HEREEEEE** |

---

## Role

A role

| Name   | Type                       | Description      |
| ------ | -------------------------- | ---------------- |
| `id`   | [String](./scalars#String) | ID of the role   |
| `name` | [String](./scalars#String) | Name of teh role |

---

## Job

A job

| Name           | Type                         | Description                              |
| -------------- | ---------------------------- | ---------------------------------------- |
| `available`    | [Boolean](./scalars#Boolean) | If the job is available or not           |
| `bonusPoints`  | [[String](./scalars#String)] |                                          |
| `jobName`      | [String](./scalars#String)   | Name of the job                          |
| `jobIcon`      | [String](./scalars#String)   | Font awesome icon of the job             |
| `questions`    | [JobQuestion](#JobQuestion)  | Questions for the application to the job |
| `requirements` | [[String](./scalars#String)] | Requirements for the job                 |
| `tasks`        | [[String](./scalars#String)] | Tasks fo the job                         |

---

## DownloadLink

| Name       | Type                        | Description               |
| ---------- | --------------------------- | ------------------------- |
| `link`     | [String](./scalars#String)! | Link to the download      |
| `platform` | [String](./scalars#String)! | Platform for the download |

---

## JobQuestion

| Name       | Type                         | Description                 |
| ---------- | ---------------------------- | --------------------------- |
| `id`       | [String](./scalars#String)   | ID of the question          |
| `question` | [String](./scalars#String)   | Question                    |
| `required` | [Boolean](./scalars#Boolean) | If the response is required |

---

## PresenceMetaData

| Name           | Type                                                   | Description                          |
| -------------- | ------------------------------------------------------ | ------------------------------------ |
| `altnames`     | [[String](./scalars#String)]                           | Presence alternative names           |
| `author`       | [PresenceMetadataUser](#presenceMetadataUser)          | Presence author                      |
| `button`       | [Boolean](./scalars#Boolean)                           |                                      |
| `category`     | [String](./scalars#String)!                            | Presence category                    |
| `color`        | [String](./scalars#String)!                            | Presence color                       |
| `contributors` | [[PresenceMetadataUser](#presenceMetadataUser)]<code>) | Presence contributors                |
| `description`  | (JSON)                                                 | **FIX THE TYPE HEREEEEE**            |
| `iframe`       | [Boolean](./scalars#Boolean)                           | If the Presence has an iFrame or not |
| `iframeRegExp` | [String](./scalars#String)                             |                                      |
| `logo          | ` [String](./scalars#String)!                          | Presence logo                        |
| `readLogs`     | [Boolean](./scalars#Boolean)                           |                                      |
| `regExp`       | [String](./scalars#String)                             | Presence RegExp                      |
| `service`      | [String](./scalars#String)!                            | Presence service name                |
| `settings`     | [[String](#presenceMetadataSettings)!]                 | Presence settings                    |
| `tags`         | [[String](./scalars#Strings)!]!                        | Presence tags                        |
| `thumbnail`    | [String](./scalars#String)!                            | Presence thumbnail                   |
| `url`          | ([Scalar](./scalars#Scalar)!)                          | **FIX THE TYPE HEREEEEE**            |
| `versions`     | [String](./scalars#String)!                            | Presence version                     |
| `warning`      | [Boolean](./scalars#String)                            |                                      |

---

## PresenceMetadataUser

| Name   | Type                        | Description         |
| ------ | --------------------------- | ------------------- |
| `id`   | [String](./scalars#String)! | ID of the author    |
| `name` | [String](./scalars#String)! | Name of the authour |

---

## PresenceMetadataSettings

| Name            | Type                                                      | Description                        |
| --------------- | --------------------------------------------------------- | ---------------------------------- |
| `icon`          | [String](./scalars#String)                                | Font awesome icon for the presence |
| `id`            | [String](./scalars#String)!                               |                                    |
| `if`            | [PresenceMetadataSettingsIf](#presenceMetadataSettingsIf) |                                    |
| `multiLanguage` | ([Scalar](./scalars#Scalars))                             | **FIX THE TYPE HEREEEEE**          |
| `placeholder`   | [String](./scalars#String)                                | Place holder text                  |
| `title`         | [String](./scalars#String)                                | Title of teh setting               |
| `value`         | [String](./scalars#String)                                |                                    |
| `values`        | [String](./scalars#String)                                |                                    |

---

## PresenceMetadataSettingsIf

| Name               | Type                       | Description                |
| ------------------ | -------------------------- | -------------------------- |
| `patternProprties` | **FIX THE TYPE HEREEEEE**  | [Scalar](./scalars#Scalar) |
| `propertyNames`    | [String](./scalars#String) |                            |

---

## SafariVersion

| Name      | Type                         | Description                     |
| --------- | ---------------------------- | ------------------------------- |
| `urgent`  | [Boolean](./scalars#Boolean) |                                 |
| `version` | [String](./scalars#String)   | Version of the Safari extension |

---

## AddBetaUserResult

| Name      | Type                                             | Description                               |
| --------- | ------------------------------------------------ | ----------------------------------------- |
| `message` | [String](./scalars#String)!                      |                                           |
| `success` | <code><code>[Boolean](./scalars#Boolean)</code>! | If the beta user was successfully created |

---

|

## AddScienceResult

| Name         | Type                         | Description |
| ------------ | ---------------------------- | ----------- |
| `arch`       | [String](./scalars#String)!  |             |
| `identifier` | [String](./scalars#String)!  |             |
| `os`         | [String](./scalars#String)!  |             |
| `presences`  | [[String](./scalars#String)] |             |

---

## DeleteScienceResult

| Name         | Type                        | Description |
| ------------ | --------------------------- | ----------- |
| `identifier` | [String](./scalars#String)! |

## CreditUser

| Name            | Type                         | Description                                                                                      |
| --------------- | ---------------------------- | ------------------------------------------------------------------------------------------------ |
| `avatar`        | [String](./scalars#String)   | User's avatar                                                                                    |
| `flags`         | [[String](./scalars#String)] | User's [flags](https://discord.com/developers/docs/resources/user#user-object-user-flags)        |
| `id`            | [String](./scalars#String)   | The user's                                                                                       |
| `name`          | [String](./scalars#String)   | The username of the user                                                                         |
| `premium_since` | [Float](./scalars#Float)     | Timestamp of when the user started boosting the guild                                            |
| `role`          | [String](./scalars#String)   | An array of role ids                                                                             |
| `roleColor`     | [String](./scalars#String)   | RGB color value                                                                                  |
| `roleId`        | [String](./scalars#String)   | ID of a role                                                                                     |
| `rolePosition`  | [Int](./scalars#Int)         | Position of the role                                                                             |
| `status`        | [String](./scalars#String)   | a [status type](https://discord.com/developers/docs/topics/gateway#update-presence-status-types) |
| `tag`           | [String](./scalars#String)   | integer representation of hexadecimal color code                                                 |

---
