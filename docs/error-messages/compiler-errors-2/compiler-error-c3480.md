---
title: Erreur du compilateur C3480
ms.date: 11/04/2016
f1_keywords:
- C3480
helpviewer_keywords:
- C3480
ms.assetid: 7b2e055a-9604-4d13-861b-b38bda1a6940
ms.openlocfilehash: 2ebcce496fd06c30420558d80cc0a0c9318d4376
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62173418"
---
# <a name="compiler-error-c3480"></a>Erreur du compilateur C3480

'variable' : une variable de capture lambda doit provenir d’une portée de fonction englobante

La variable de capture lambda ne provient pas d’une portée de fonction englobante.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Supprimez la variable de la liste de capture de l’expression lambda.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3480, car la variable `global` ne provient pas d’une portée de fonction englobante :

```
// C3480a.cpp

int global = 0;
int main()
{
   [&global] { global = 5; }(); // C3480
}
```

## <a name="example"></a>Exemple

L’exemple suivant résout l’erreur C3480 en supprimant la variable `global` de la liste de capture de l’expression lambda :

```
// C3480b.cpp

int global = 0;
int main()
{
   [] { global = 5; }();
}
```

## <a name="see-also"></a>Voir aussi

[Expressions lambda](../../cpp/lambda-expressions-in-cpp.md)