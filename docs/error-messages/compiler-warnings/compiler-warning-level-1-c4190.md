---
title: Compilateur Warning (level 1) C4190
ms.date: 11/04/2016
f1_keywords:
- C4190
helpviewer_keywords:
- C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
ms.openlocfilehash: 05984594a57878aad8037861a15ac9284ff65192
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50521227"
---
# <a name="compiler-warning-level-1-c4190"></a>Compilateur Warning (level 1) C4190

'identificateur1' a une liaison C spécifiée, mais retourne UDT 'identificateur2' qui est incompatible avec C

Une fonction ou un pointeur vers une fonction a un UDT (défini par l’utilisateur type, classe, structure, enum ou union) en tant que type de retour et `extern` une liaison « C ». Cela est légal si :

- Tous les appels à cette fonction se produisent à partir de C++.

- La définition de la fonction est en C++.

## <a name="example"></a>Exemple

```cpp
// C4190.cpp
// compile with: /W1 /LD
struct X
{
   int i;
   X ();
   virtual ~X ();
};

extern "C" X func ();   // C4190
```