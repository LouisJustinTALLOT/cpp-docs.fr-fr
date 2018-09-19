---
title: Initialisation de chaînes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- character arrays, initializing
- strings [C++], initializing
- initializing arrays, strings
ms.assetid: 0ab8079d-d0d3-48f9-afd1-36a7bb439b29
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e954fc417fb62d3bd08b1c37d445a3d7f2bc9ec9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46034874"
---
# <a name="initializing-strings"></a>Initialisation de chaînes

Vous pouvez initialiser un tableau de caractères (ou des caractères larges) avec un littéral de chaîne (ou un littéral de chaîne étendu). Exemple :

```
char code[ ] = "abc";
```

initialise `code` en tant que tableau de caractères à quatre éléments. Le quatrième élément est le caractère Null, qui termine tous les littéraux de chaîne.

Une liste d'identificateurs ne peut pas dépasser le nombre d'identificateurs à initialiser. Si vous spécifiez une taille de tableau inférieure à celle de la chaîne, les caractères supplémentaires sont ignorés. Par exemple, la déclaration suivante initialise `code` en tant que tableau de caractères à trois éléments :

```
char code[3] = "abcd";
```

Seuls les trois premiers caractères de l'initialiseur sont assignés à `code`. Le caractère `d` et le caractère Null de terminaison de la chaîne sont ignorés. Notez que cela crée une chaîne non terminée (autrement dit, une chaîne sans valeur 0 pour marquer sa terminaison) et génère un message de diagnostic indiquant cette condition.

La déclaration

```
char s[] = "abc", t[3] = "abc";
```

est identique à

```
char s[]  = {'a', 'b', 'c', '\0'},
     t[3] = {'a', 'b', 'c' };
```

Si la chaîne est plus courte que la taille de tableau spécifiée, les éléments restants du tableau sont initialisés à 0.

**Section spécifique à Microsoft**

Dans Microsoft C, les littéraux de chaîne peuvent contenir jusqu'à 2048 octets au total.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Initialisation](../c-language/initialization.md)