---
title: Erreur du compilateur C3389
ms.date: 11/04/2016
f1_keywords:
- C3389
helpviewer_keywords:
- C3389
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
ms.openlocfilehash: 8a040e649074e115b1b86ea56db6c9ef48f4c0d0
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520471"
---
# <a name="compiler-error-c3389"></a>Erreur du compilateur C3389

> __declspec (*mot clé*) ne peut pas être utilisé avec/clr : pure ou/CLR : safe

## <a name="remarks"></a>Notes

Les **`/clr:pure`** **`/clr:safe`** Options du compilateur et sont dépréciées dans visual studio 2015 et ne sont pas prises en charge dans visual studio 2017.

Un [`__declspec`](../../cpp/declspec.md) modificateur utilisé implique un État par processus.  [`/clr:pure`](../../build/reference/clr-common-language-runtime-compilation.md)implique un par [`appdomain`](../../cpp/appdomain.md) État.  Par conséquent, la déclaration d’une variable avec le modificateur de *mot clé* **`__declspec`** et la compilation avec **`/clr:pure`** ne sont pas autorisées.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3389 :

```cpp
// C3389.cpp
// compile with: /clr:pure /c
__declspec(dllexport) int g2 = 0;   // C3389
```
