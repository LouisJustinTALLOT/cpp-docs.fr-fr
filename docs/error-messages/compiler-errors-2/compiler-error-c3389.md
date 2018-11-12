---
title: Erreur du compilateur C3389
ms.date: 11/04/2016
f1_keywords:
- C3389
helpviewer_keywords:
- C3389
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
ms.openlocfilehash: 6a9568f3c3be88438eae1f28e12dc780301ead0b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584299"
---
# <a name="compiler-error-c3389"></a>Erreur du compilateur C3389

> __declspec (*mot clé*) ne peut pas être utilisé avec/clr : pure ou/CLR : safe

## <a name="remarks"></a>Notes

Le **/CLR : pure** et **/CLR : safe** options du compilateur sont déconseillées dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

Un [__declspec](../../cpp/declspec.md) modificateur utilisé implique un état par processus.  [/ CLR : pure](../../build/reference/clr-common-language-runtime-compilation.md) implique un par [appdomain](../../cpp/appdomain.md) état.  Par conséquent, déclarer une variable avec le `keyword` **__declspec** modificateur et la compilation avec **/CLR : pure** n’est pas autorisée.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3389 :

```cpp
// C3389.cpp
// compile with: /clr:pure /c
__declspec(dllexport) int g2 = 0;   // C3389
```