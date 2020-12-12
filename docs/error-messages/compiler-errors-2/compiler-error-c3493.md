---
description: 'En savoir plus sur : erreur du compilateur C3493'
title: Erreur du compilateur C3493
ms.date: 11/04/2016
f1_keywords:
- C3493
helpviewer_keywords:
- C3493
ms.assetid: 734b4257-12a3-436f-8488-c8c55ec81634
ms.openlocfilehash: 8f16a53dbaf5b9924a4874d29d560f9c089eb244
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315528"
---
# <a name="compiler-error-c3493"></a>Erreur du compilateur C3493

Impossible de capturer implicitement 'var', car aucun mode de capture par défaut n’a été spécifié

La capture de l’expression lambda vide, `[]`, spécifie que l’expression lambda ne capture pas de variables explicitement ou implicitement.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Spécifiez un mode de capture par défaut, ou

- Capturez explicitement une ou plusieurs variables.

## <a name="examples"></a>Exemples

L’exemple suivant génère l’erreur C3493 parce qu’il modifie une variable externe, alors qu’il spécifie la clause de capture vide :

```cpp
// C3493a.cpp

int main()
{
   int m = 55;
   [](int n) { m = n; }(99); // C3493
}
```

L’exemple suivant corrige C3493 en spécifiant la capture par référence comme mode de capture par défaut.

```cpp
// C3493b.cpp

int main()
{
   int m = 55;
   [&](int n) { m = n; }(99);
}
```

## <a name="see-also"></a>Voir aussi

[Expressions lambda](../../cpp/lambda-expressions-in-cpp.md)
