---
title: Erreur du compilateur C3389
ms.date: 11/04/2016
f1_keywords:
- C3389
helpviewer_keywords:
- C3389
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
ms.openlocfilehash: b166096390169939f01bcb976a57612f10f7df2e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201134"
---
# <a name="compiler-error-c3389"></a>Erreur du compilateur C3389

> __declspec (*mot clé*) ne peut pas être utilisé avec/clr : pure ou/CLR : safe

## <a name="remarks"></a>Notes

Les options de compilateur **/clr : pure** et **/clr : safe** sont dépréciées dans Visual Studio 2015 et ne sont pas prises en charge dans Visual Studio 2017.

Un modificateur de [__declspec](../../cpp/declspec.md) utilisé implique un État par processus.  [/clr : pure](../../build/reference/clr-common-language-runtime-compilation.md) implique un État par [AppDomain](../../cpp/appdomain.md) .  Par conséquent, la déclaration d’une variable avec le modificateur **__declspec** `keyword`et la compilation avec **/clr : pure** ne sont pas autorisées.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3389 :

```cpp
// C3389.cpp
// compile with: /clr:pure /c
__declspec(dllexport) int g2 = 0;   // C3389
```
