---
description: 'En savoir plus sur : erreur du compilateur C3480'
title: Erreur du compilateur C3480
ms.date: 11/04/2016
f1_keywords:
- C3480
helpviewer_keywords:
- C3480
ms.assetid: 7b2e055a-9604-4d13-861b-b38bda1a6940
ms.openlocfilehash: dbeed462410d36b466e807d576549c1b73ee4917
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113413"
---
# <a name="compiler-error-c3480"></a>Erreur du compilateur C3480

'variable' : une variable de capture lambda doit provenir d’une portée de fonction englobante

La variable de capture lambda ne provient pas d’une portée de fonction englobante.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Supprimez la variable de la liste de capture de l’expression lambda.

## <a name="examples"></a>Exemples

L’exemple suivant génère l’erreur C3480, car la variable `global` ne provient pas d’une portée de fonction englobante :

```cpp
// C3480a.cpp

int global = 0;
int main()
{
   [&global] { global = 5; }(); // C3480
}
```

L’exemple suivant résout l’erreur C3480 en supprimant la variable `global` de la liste de capture de l’expression lambda :

```cpp
// C3480b.cpp

int global = 0;
int main()
{
   [] { global = 5; }();
}
```

## <a name="see-also"></a>Voir aussi

[Expressions lambda](../../cpp/lambda-expressions-in-cpp.md)
