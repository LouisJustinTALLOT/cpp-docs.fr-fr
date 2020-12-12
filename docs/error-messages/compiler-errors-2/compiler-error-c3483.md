---
description: 'En savoir plus sur : erreur du compilateur C3483'
title: Erreur du compilateur C3483
ms.date: 11/04/2016
f1_keywords:
- C3483
helpviewer_keywords:
- C3483
ms.assetid: 18b3a2c5-dfc9-4661-9653-08a5798474cf
ms.openlocfilehash: 7c67e1e4d44c64fbcc023ee410dff2ecdd92c361
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113383"
---
# <a name="compiler-error-c3483"></a>Erreur du compilateur C3483

'var' figure déjà dans la liste de capture lambda

Vous avez passé plusieurs fois la même variable à la liste de capture d’une expression lambda.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Supprimez toutes les instances supplémentaires de la variable de la liste de capture.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3483, car la variable `n` apparaît plusieurs fois dans la liste de capture de l’expression lambda :

```cpp
// C3483.cpp

int main()
{
   int m = 6, n = 5;
   [m,n,n] { return n + m; }(); // C3483
}
```

## <a name="see-also"></a>Voir aussi

[Expressions lambda](../../cpp/lambda-expressions-in-cpp.md)
