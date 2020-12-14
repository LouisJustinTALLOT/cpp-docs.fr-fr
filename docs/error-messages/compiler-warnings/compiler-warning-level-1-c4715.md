---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4715'
title: Avertissement du compilateur (niveau 1) C4715
ms.date: 11/04/2016
f1_keywords:
- C4715
helpviewer_keywords:
- C4715
ms.assetid: 1c819bf7-0d8b-4f5e-b338-9cc292870439
ms.openlocfilehash: 41682beae6e32ba397f3c9dae43d57a182b09b65
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97249098"
---
# <a name="compiler-warning-level-1-c4715"></a>Avertissement du compilateur (niveau 1) C4715

'fonction' : les chemins de contrôle ne retournent pas tous une valeur

La fonction spécifiée peut potentiellement ne pas retourner de valeur.

## <a name="example"></a>Exemple

```cpp
// C4715a.cpp
// compile with: /W1 /LD
int func1( int i )
{
   if( i )
   return 3;  // C4715 warning, nothing returned if i == 0
}
```

Pour éviter cet avertissement, modifiez le code afin que tous les chemins d’accès assignent une valeur de retour à la fonction :

```cpp
// C4715b.cpp
// compile with: /LD
int func1( int i )
{
   if( i ) return 3;
   else return 0;     // OK, always returns a value
}
```

Il est possible que votre code puisse contenir un appel à une fonction qui ne retourne jamais, comme dans l’exemple suivant :

```cpp
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
