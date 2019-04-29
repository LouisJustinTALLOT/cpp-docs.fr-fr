---
title: Erreur du compilateur C2482
ms.date: 09/15/2017
f1_keywords:
- C2482
helpviewer_keywords:
- C2482
ms.assetid: 98c87da2-625c-4cc2-9bf7-78d15921e779
ms.openlocfilehash: 481920fa2d8c32bc872e7b8805188cc674e6fe28
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375052"
---
# <a name="compiler-error-c2482"></a>Erreur du compilateur C2482

>«*identificateur*' : l’initialisation dynamique de données de 'thread' non autorisée dans le code managé/WinRT

## <a name="remarks"></a>Notes

Dans le managé ou WinRT de code, les variables déclarées à l’aide de la [__declspec (thread)](../../cpp/thread.md) attribut de modificateur de classe de stockage ou le [thread_local](../../cpp/storage-classes-cpp.md#thread_local) spécificateur de classe de stockage ne peut pas être initialisée avec une expression qui requiert une évaluation au moment de l’exécution. Une expression statique est requise pour initialiser `__declspec(thread)` ou `thread_local` données dans ces environnements d’exécution.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2482 dans gérés (**/CLR**) et dans WinRT (**/ZW**) code :

```cpp
// C2482.cpp
// For managed example, compile with: cl /EHsc /c /clr C2482.cpp
// For WinRT example, compile with: cl /EHsc /c /ZW C2482.cpp
#define Thread __declspec( thread )
Thread int tls_i1 = tls_i1;   // C2482

int j = j;   // OK in C++; C error
Thread int tls_i2 = sizeof( tls_i2 );   // Okay in C and C++
```

Pour résoudre ce problème, initialiser le stockage local des threads à l’aide d’une constante, **constexpr**, ou une expression statique. Effectuer toute initialisation spécifique au thread séparément.