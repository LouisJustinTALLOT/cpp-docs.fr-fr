---
description: 'En savoir plus sur : initialisation de chaînes'
title: Initialisation de chaînes
ms.date: 11/04/2016
helpviewer_keywords:
- character arrays, initializing
- strings [C++], initializing
- initializing arrays, strings
ms.assetid: 0ab8079d-d0d3-48f9-afd1-36a7bb439b29
ms.openlocfilehash: 145fc55eaccd64b30bae2736dd78317dc5db7d7d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97137577"
---
# <a name="initializing-strings"></a>Initialisation de chaînes

Vous pouvez initialiser un tableau de caractères (ou des caractères larges) avec un littéral de chaîne (ou un littéral de chaîne étendu). Par exemple :

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

**Spécifique à Microsoft**

Dans Microsoft C, les littéraux de chaîne peuvent contenir jusqu'à 2048 octets au total.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[D’initialisation](../c-language/initialization.md)
