---
title: 'Exemple d’appel : Fonction Prototype et appel | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- calling conventions, examples [C++]
- examples [C++], calling conventions
ms.assetid: e4275d1f-df2e-4bfc-a162-eb43ec69554a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 04e681560854be4c93b1c93786d38771c07244ea
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099575"
---
# <a name="calling-example-function-prototype-and-call"></a>Exemple d'appel : Prototype et appel de fonction

## <a name="microsoft-specific"></a>Section spécifique à Microsoft

L’exemple suivant montre les résultats d’un appel de fonction effectué à l’aide de différentes conventions d’appel.

Cet exemple repose sur la structure de fonction suivante. Remplacez `calltype` par la convention d'appel appropriée.

```
void    calltype MyFunc( char c, short s, int i, double f );
.
.
.
void    MyFunc( char c, short s, int i, double f )
    {
    .
    .
    .
    }
.
.
.
MyFunc ('x', 12, 8192, 2.7183);
```

Pour plus d’informations, consultez [résultats de l’exemple appel](../cpp/results-of-calling-example.md).

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Conventions d’appel](../cpp/calling-conventions.md)