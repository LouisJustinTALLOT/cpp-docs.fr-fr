---
title: Avertissement du compilateur (niveau 1) C4715
ms.date: 11/04/2016
f1_keywords:
- C4715
helpviewer_keywords:
- C4715
ms.assetid: 1c819bf7-0d8b-4f5e-b338-9cc292870439
ms.openlocfilehash: f165ea3b54b78e2f8fae995815e309d55101244e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501229"
---
# <a name="compiler-warning-level-1-c4715"></a>Avertissement du compilateur (niveau 1) C4715

'fonction' : pas de tous les chemins de contrôle retournent une valeur

La fonction spécifiée ne peut pas retourner une valeur.

## <a name="example"></a>Exemple

```
// C4715a.cpp
// compile with: /W1 /LD
int func1( int i )
{
   if( i )
   return 3;  // C4715 warning, nothing returned if i == 0
}
```

Pour éviter cet avertissement, modifiez le code afin que tous les chemins d’affectent une valeur de retour à la fonction :

```
// C4715b.cpp
// compile with: /LD
int func1( int i )
{
   if( i ) return 3;
   else return 0;     // OK, always returns a value
}
```

Il est possible que votre code peut contenir un appel à une fonction qui ne retourne jamais, comme dans l’exemple suivant :

```
// C4715c.cpp
// compile with: /W1 /LD
void fatal()
{
}
int glue()
{
   if(0)
      return 1;
   else if(0)
      return 0;
   else
      fatal();   // C4715
}
```

Ce code génère également un avertissement, car le compilateur ne sait pas que `fatal` ne retourne jamais. Pour éviter que ce code génère un message d’erreur, déclarez `fatal` à l’aide de [__declspec (noreturn)](../../cpp/noreturn.md).