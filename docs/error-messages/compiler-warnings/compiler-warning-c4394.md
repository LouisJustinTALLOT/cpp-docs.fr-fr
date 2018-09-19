---
title: Avertissement du compilateur C4394 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4394
dev_langs:
- C++
helpviewer_keywords:
- C4394
ms.assetid: 5de94de0-17e3-4e7c-92f4-5c3c1b825120
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d99200dd01db610aa558e8a9df18b7afacdf3d7d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099503"
---
# <a name="compiler-warning-c4394"></a>Avertissement du compilateur C4394

'fonction' : symbole par appdomain ne doit pas être marqué avec __declspec (dllexport)

Une fonction marquée avec le [appdomain](../../cpp/appdomain.md) `__declspec` modificateur est compilé en code MSIL (non natif) et les tables d’exportation ([exporter](../../windows/export.md) `__declspec` modificateur) ne sont pas pris en charge pour les fonctions managées.

Vous pouvez déclarer une fonction managée à avoir une accessibilité publique. Pour plus d’informations, consultez [tapez visibilité](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) et [visibilité des membres](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Member_visibility).

C4394 est toujours émis en tant qu’erreur.  Vous pouvez désactiver cet avertissement avec le `#pragma warning` ou **WD**; consultez [avertissement](../../preprocessor/warning.md) ou [wln, / W0, W1, W2, / w3, / W4, W1, W2, / w3, / W4, Wall, WD, / we, Wo, / WV, /WX (niveau d’avertissement)](../../build/reference/compiler-option-warning-level.md)pour plus d’informations.

## <a name="example"></a>Exemple

L’exemple suivant génère C4394.

```
// C4394.cpp
// compile with: /clr /c
__declspec(dllexport) __declspec(appdomain) int g1 = 0;   // C4394
__declspec(dllexport) int g2 = 0;   // OK
```