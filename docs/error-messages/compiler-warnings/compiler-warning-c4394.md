---
description: 'En savoir plus sur : avertissement du compilateur C4394'
title: Avertissement du compilateur C4394
ms.date: 11/04/2016
f1_keywords:
- C4394
helpviewer_keywords:
- C4394
ms.assetid: 5de94de0-17e3-4e7c-92f4-5c3c1b825120
ms.openlocfilehash: 8a732e4cc1b3454a0dd602cd36b9ae8b959a8118
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97180758"
---
# <a name="compiler-warning-c4394"></a>Avertissement du compilateur C4394

'fonction' : le symbole par AppDomain ne doit pas être marqué avec __declspec (dllexport)

Une fonction marquée avec le [](../../cpp/appdomain.md) **`__declspec`** modificateur AppDomain est COMPILÉE en langage MSIL (et non native), et les tables d’exportation (modificateur d'[exportation](../../windows/attributes/export.md) **`__declspec`** ) ne sont pas prises en charge pour les fonctions managées.

Vous pouvez déclarer une fonction managée pour avoir une accessibilité publique. Pour plus d’informations, consultez [visibilité des types](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) et visibilité des [membres](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Member_visibility).

C4394 est toujours émis en tant qu’erreur.  Vous pouvez désactiver cet avertissement avec le `#pragma warning` ou **/WD**; consultez [Warning](../../preprocessor/warning.md) ou [/W,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/we,/WO,/WV,/WX (niveau d’avertissement)](../../build/reference/compiler-option-warning-level.md) pour plus d’informations.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4394.

```cpp
// C4394.cpp
// compile with: /clr /c
__declspec(dllexport) __declspec(appdomain) int g1 = 0;   // C4394
__declspec(dllexport) int g2 = 0;   // OK
```
