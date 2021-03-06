---
description: 'En savoir plus sur : erreur du compilateur C2482'
title: Erreur du compilateur C2482
ms.date: 09/15/2017
f1_keywords:
- C2482
helpviewer_keywords:
- C2482
ms.assetid: 98c87da2-625c-4cc2-9bf7-78d15921e779
ms.openlocfilehash: 1ffde4d7ea9f4eccdd643b3ac6efe0545775816a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123927"
---
# <a name="compiler-error-c2482"></a>Erreur du compilateur C2482

>'*identificateur*' : l’initialisation dynamique des données’thread’n’est pas autorisée dans le code managé/WinRT

## <a name="remarks"></a>Notes

Dans le code managé ou WinRT, les variables déclarées à l’aide de l’attribut de modificateur de classe de stockage [__declspec (thread)](../../cpp/thread.md) ou le spécificateur de classe de stockage [thread_local](../../cpp/storage-classes-cpp.md#thread_local) ne peuvent pas être initialisées avec une expression qui requiert une évaluation au moment de l’exécution. Une expression statique est requise pour initialiser `__declspec(thread)` ou **`thread_local`** des données dans ces environnements d’exécution.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2482 dans le code managé (**/CLR**) et dans le code WinRT (**/ZW**) :

```cpp
// C2482.cpp
// For managed example, compile with: cl /EHsc /c /clr C2482.cpp
// For WinRT example, compile with: cl /EHsc /c /ZW C2482.cpp
#define Thread __declspec( thread )
Thread int tls_i1 = tls_i1;   // C2482

int j = j;   // OK in C++; C error
Thread int tls_i2 = sizeof( tls_i2 );   // Okay in C and C++
```

Pour résoudre ce problème, initialisez le stockage local des threads à l’aide d’une constante, ou d’une **`constexpr`** expression statique. Effectuez une initialisation spécifique au thread séparément.
