---
description: 'En savoir plus sur : erreur du compilateur C2577'
title: Erreur du compilateur C2577
ms.date: 11/04/2016
f1_keywords:
- C2577
helpviewer_keywords:
- C2577
ms.assetid: fc79ef83-8362-40a2-9257-8037c3195ce4
ms.openlocfilehash: 9e54791070401f334a4dc0650ca2b1bcee5f32a6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97208851"
---
# <a name="compiler-error-c2577"></a>Erreur du compilateur C2577

'membre' : le destructeur/finaliseur ne peut pas avoir de type de retour

Un destructeur ou un finaliseur ne peut pas retourner une valeur de ou d’un **`void`** autre type. Supprimez l' **`return`** instruction de la définition du destructeur.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2577.

```cpp
// C2577.cpp
// compile with: /c
class A {
public:
   A() {}
   ~A(){
      return 0;   // C2577
   }
};
```
