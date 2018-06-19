---
title: Erreur du compilateur C2482 | Documents Microsoft
ms.custom: ''
ms.date: 09/15/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2482
dev_langs:
- C++
helpviewer_keywords:
- C2482
ms.assetid: 98c87da2-625c-4cc2-9bf7-78d15921e779
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c3dd23069f389d0a02e10d26edb7ee4fd3c373cb
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34256004"
---
# <a name="compiler-error-c2482"></a>Erreur du compilateur C2482

>'*identificateur*' : l’initialisation dynamique de données 'thread' non autorisée dans le code managé/WinRT

## <a name="remarks"></a>Notes

Dans managé ou WinRT de code, les variables déclarées à l’aide de la [__declspec (thread)](../../cpp/thread.md) attribut de modificateur de classe de stockage ou la [thread_local](../../cpp/storage-classes-cpp.md#thread_local) spécificateur de classe de stockage ne peut pas être initialisée avec une expression nécessitant une évaluation au moment de l’exécution. Une expression statique est requise pour initialiser `__declspec(thread)` ou `thread_local` les données dans ces environnements d’exécution.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2482 dans gérés (**/CLR**) et WinRT (**/ZW**) code :

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