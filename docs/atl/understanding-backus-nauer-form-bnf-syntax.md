---
title: ATL (inscription) et Backus Nauer forment la syntaxe (BNF) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- BNF notation
- Backus Nauer Form (BNF) syntax
ms.assetid: 994bbef0-9077-4aa8-bdfe-b7e830af9acc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e615068580bcc9078959cc6cdd7831d05b5a4acd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020873"
---
# <a name="understanding-backus-nauer-form-bnf-syntax"></a>Syntaxe de Backus Nauer Form (BNF)

Les scripts utilisés par le bureau d’enregistrement ATL sont décrits dans cette rubrique à l’aide de la syntaxe BNF, qui utilise la notation indiquée dans le tableau suivant.

|Convention/symbole|Signification|
|------------------------|-------------|
|::=|Équivalent|
|&#124;|OU|
|X +|Un ou plusieurs des Xs.|
|[X]|X est facultatif. Les délimiteurs facultatifs sont indiqués par \[].|
|N’importe quel **gras** texte|Un littéral de chaîne.|
|N’importe quel *en italique* texte|Comment construire le littéral de chaîne.|

Comme indiqué dans le tableau précédent, scripts d’inscription utilisent des littéraux de chaîne. Ces valeurs sont le texte réel qui doit apparaître dans votre script. Le tableau suivant décrit les littéraux de chaîne utilisées dans un script ATL (inscription).

|Littéral de chaîne|Action|
|--------------------|------------|
|**ForceRemove**|Supprime complètement la clé suivante (si elle existe) et la recrée.|
|**NoRemove**|Ne supprime pas la clé suivante au cours de désinscription.|
|**Val**|Spécifie que `<Key Name>` est en fait une valeur nommée.|
|**Supprimer**|Supprime la clé suivante pendant l’inscription.|
|**s**|Spécifie que la valeur suivante est une chaîne (REG_SZ).|
|**d**|Spécifie que la valeur suivante est un DWORD (REG_DWORD).|
|**m**|Spécifie que la valeur suivante est une multiple de longueur fixe (REG_MULTI_SZ).|
|**b**|Spécifie que la valeur suivante est une valeur binaire (REG_BINARY).|

## <a name="bnf-syntax-examples"></a>Exemples de syntaxe BNF

Voici quelques exemples de syntaxe pour vous aider à comprendre le fonctionnement les littéraux de chaîne et de notation dans un script ATL (inscription).

### <a name="syntax-example-1"></a>Exemple de syntaxe 1

```
<registry expression> ::= <Add Key>
```

Spécifie que `registry expression` équivaut à `Add Key`.

### <a name="syntax-example-2"></a>Exemple de syntaxe 2

```
<registry expression> ::= <Add Key> | <Delete Key>
```

Spécifie que `registry expression` équivaut au type `Add Key` ou `Delete Key`.

### <a name="syntax-example-3"></a>Exemple de syntaxe 3

```
<Key Name> ::= '<AlphaNumeric>+'
```

Spécifie que `Key Name` équivaut à un ou plusieurs `AlphaNumerics`.

### <a name="syntax-example-4"></a>Exemple de syntaxe 4

```
<Add Key> ::= [ForceRemove | NoRemove | val]<Key Name>
```

Spécifie que `Add Key` équivaut à `Key Name`et que les littéraux de chaîne, `ForceRemove`, `NoRemove`, et `val`, sont facultatives.

### <a name="syntax-example-5"></a>Exemple de syntaxe 5

```
<AlphaNumeric> ::= any character not NULL, that is, ASCII 0
```

Spécifie que `AlphaNumeric` équivaut à n’importe quel caractère NULL.

### <a name="syntax-example-6"></a>Exemple de syntaxe 6

```
val 'testmulti' = m 'String 1\0String 2\0'
```

Spécifie que le nom de clé `testmulti` est une valeur de chaîne multiple composée de `String 1` et `String 2`.

### <a name="syntax-example-7"></a>Exemple de syntaxe 7

```
val 'testhex' = d '&H55'
```

Spécifie que le nom de clé `testhex` est une valeur DWORD définie à 55 hexadécimal (85 décimal). Notez que ce format respecte le **& H** notation en tant que trouvée dans la spécification de Visual Basic.

## <a name="see-also"></a>Voir aussi

[Création de scripts d’inscription](../atl/creating-registrar-scripts.md)

