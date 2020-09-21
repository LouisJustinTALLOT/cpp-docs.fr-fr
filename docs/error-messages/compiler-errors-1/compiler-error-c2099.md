---
title: Erreur du compilateur C2099
ms.date: 11/04/2016
f1_keywords:
- C2099
helpviewer_keywords:
- C2099
ms.assetid: 30e151ee-d458-4901-b0c0-d45054a913f5
ms.openlocfilehash: 84070b36506a657dde5d2e7bd5594c2b7434d81d
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743410"
---
# <a name="compiler-error-c2099"></a>Erreur du compilateur C2099

l'initialiseur n'est pas une constante

Cette erreur est émise uniquement par le compilateur C et ne se produit que pour les variables non automatiques.  Le compilateur initialise des variables non automatiques au début du programme et les valeurs avec lesquelles elles sont initialisées doivent être des constantes.

## <a name="examples"></a>Exemples

L’exemple suivant génère l’erreur C2099.

```c
// C2099.c
int j;
int *p;
j = *p;   // C2099 *p is not a constant
```

L’erreur C2099 peut également se produire si le compilateur ne parvient pas à effectuer un repli de constante sur une expression sous **/fp:strict** , ce qui peut être dû au fait que les paramètres de l’environnement de précision en virgule flottante diffèrent entre le moment de la compilation et celui de l’exécution. Pour plus d’informations, consultez [_controlfp_s](../../c-runtime-library/reference/controlfp-s.md) .

En cas d’échec du repli de constante, le compilateur appelle l’initialisation dynamique, ce qui n’est pas autorisé en C.

Pour résoudre cette erreur, compilez le module en tant que fichier .cpp ou simplifiez l’expression.

Pour plus d’informations, consultez l’article [/fp (Spécifier le comportement de virgule flottante)](../../build/reference/fp-specify-floating-point-behavior.md).

L’exemple suivant génère l’erreur C2099.

```c
// C2099_2.c
// compile with: /fp:strict /c
float X = 2.0 - 1.0;   // C2099
float X2 = 1.0;   // OK
```
