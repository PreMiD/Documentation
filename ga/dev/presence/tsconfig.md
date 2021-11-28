---
title: Cumraíocht TypeScript
description: Cúntóir beag do TypeScript
published: true
date: 2021-09-18T14:31:22.005Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:45:10.473Z
---

# Cumraíocht TypeScript

## Réamhrá

Nuair a rinne tú an spás oibre a íoslódáil agus a dhíphacáil, feicfidh tú comhad darb ainm ` tsconfig.json ` i bhfillteáin fréimhe agus láithreachta, úsáidtear an comhad seo chun an tiomsaitheoir ** TypeScript ** a chumrú. Tá sé cumraithe duit cheana féin, mar sin ná bíodh imní ort faoi sin.

Níl uainn ach cur síos a dhéanamh ar roinnt socruithe ar chóir duit a bheith ar an eolas fúthu.

## Cumraíocht Fréamh

Sa chomhad cumraíochta fréimhe feicfidh tú rud mar seo.

```javascript
{
  "compilerOptions": {
    "module": "CommonJS",
    "target": "ES2020",
    "removeComments": true,
    "noEmitOnError": true,
    "noFallthroughCasesInSwitch": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "inlineSourceMap": true,
    "typeRoots": ["@types"],
    "esModuleInterop": true
  }
}
```

| Maoin                      | Cur síos                                                                                                                                                                                    |
|:-------------------------- |:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **compilerOptions**        | Úsáidtear an chuid is mó de na hairíonna anseo chun an tiomsaitheoir a chumrú.                                                                                                              |
| module                     | Is féidir leat níos mó a léamh faoi sin [ anseo](https://www.typescriptlang.org/docs/handbook/modules.html).                                                                                |
| target                     | Sainmhínítear an leagan JavaScript atá á chur le chéile agat.                                                                                                                               |
| removeComments             | Tuairimí a bhaint ó chomhaid tiomsaithe.                                                                                                                                                    |
| noEmitOnError              | Ná astaíonn aschuir má tuairiscíodh aon earráidí.                                                                                                                                           |
| noFallthroughCasesInSwitch | Tuairiscigh earráidí i gcásanna cinn sa ráiteas lasc.                                                                                                                                       |
| noUnusedLocals             | Tuairiscigh earráidí ar mhuintir na háite nár úsáideadh.                                                                                                                                    |
| noUnusedParameters         | Tuairiscigh earráidí ar pharaiméadair nár úsáideadh.                                                                                                                                        |
| inlineSourceMap            | Cuireann mapáil foinse leis                                                                                                                                                                 |
| typeRoots                  | Is féidir leat níos mó a léamh faoi sin [ anseo](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html#types-typeroots-and-types).                                                |
| esModuleInterop            | Scaoil cúntóirí __importStar agus __importDefault le haghaidh comhoiriúnacht éiceachóras babel runtime agus cumasaigh --allowSyntheticDefaultImports le haghaidh comhoiriúnacht córais. |

## Cumraíocht Láithreachta

```javascript
{
  "extends": "../../../tsconfig.json",
  "compilerOptions": {
    "outDir": "./dist/"
  }
}
```

| Maoin               | Cur síos                                                                                                    |
|:------------------- |:----------------------------------------------------------------------------------------------------------- |
| **extends**         | Úsáidtear é chun an comhad ` tsconfig ` bonn a leathnú le haghaidh tascanna éagsúla.                        |
| **compilerOptions** | Féach [ ** Cumraíocht Fréamh ** ](/dev/presence/tsconfig#root-configuration) chun tuilleadh eolais a fháil. |
| outDir              | Sainmhínítear an eolaire aschuir do chomhaid tiomsaithe.                                                    |
