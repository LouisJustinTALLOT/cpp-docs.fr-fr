---
title: Évaluation des jetons
ms.date: 11/04/2016
helpviewer_keywords:
- tokens, evaluating
ms.assetid: 28870b62-dff6-4644-8b75-d58f340b48d2
ms.openlocfilehash: 15775ca9a7ada46aaf4e53ae952cd67e95bbf8d3
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152545"
---
# <a name="evaluation-of-tokens"></a>Évaluation des jetons

Lorsque le compilateur interprète les jetons, il inclut autant de caractères que possible dans un jeton avant de passer au jeton suivant. En raison de ce comportement, le compilateur peut ne pas interpréter les jetons comme prévu, s'ils ne sont pas correctement séparés par des espaces blancs. Prenons l'expression suivante :

```
i+++j
```

Dans cet exemple, le compilateur commence par créer l'opérateur le plus long possible (`++`) à partir des trois signes plus, puis traite le signe plus restant comme opérateur d'addition (`+`). Ainsi, l'expression est interprétée comme `(i++) + (j)`, et non pas comme `(i) + (++j)`. Dans ce cas et des cas similaires, utilisez des espaces blancs et des parenthèses pour éviter toute ambiguïté et garantir l'évaluation de l'expression appropriée.

**Section spécifique à Microsoft**

Le compilateur C traite un caractère CTRL+Z comme un indicateur de fin de fichier. Il ignore le texte après CTRL+Z.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Jetons C](../c-language/c-tokens.md)
