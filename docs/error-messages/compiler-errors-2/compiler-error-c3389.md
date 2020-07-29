---
title: Erreur du compilateur C3389
ms.date: 11/04/2016
f1_keywords:
- C3389
helpviewer_keywords:
- C3389
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
ms.openlocfilehash: 823b28deae3e3cfc18cdad8d37007bf8e8cff494
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221053"
---
# <a name="compiler-error-c3389"></a>Erreur du compilateur C3389

> __declspec (*mot clé*) ne peut pas être utilisé avec/clr : pure ou/CLR : safe

## <a name="remarks"></a>Notes

Les options de compilateur **/clr : pure** et **/clr : safe** sont dépréciées dans Visual Studio 2015 et ne sont pas prises en charge dans Visual Studio 2017.

Un modificateur de [__declspec](../../cpp/declspec.md) utilisé implique un État par processus.  [/clr : pure](../../build/reference/clr-common-language-runtime-compilation.md) implique un État par [AppDomain](../../cpp/appdomain.md) .  Par conséquent, la déclaration d’une variable avec le `keyword` **`__declspec`** modificateur et la compilation avec **/clr : pure** ne sont pas autorisées.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3389 :

```cpp
// C3389.cpp
// compile with: /clr:pure /c
__declspec(dllexport) int g2 = 0;   // C3389
```
