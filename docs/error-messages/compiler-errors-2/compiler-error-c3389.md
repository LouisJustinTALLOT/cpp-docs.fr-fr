---
description: 'En savoir plus sur : erreur du compilateur C3389'
title: Erreur du compilateur C3389
ms.date: 11/04/2016
f1_keywords:
- C3389
helpviewer_keywords:
- C3389
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
ms.openlocfilehash: b9fedf0993738d054cd5ded605d96001b3db13eb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97285498"
---
# <a name="compiler-error-c3389"></a>Erreur du compilateur C3389

> __declspec (*mot clé*) ne peut pas être utilisé avec/clr : pure ou/CLR : safe

## <a name="remarks"></a>Notes

Les **`/clr:pure`** **`/clr:safe`** Options du compilateur et sont dépréciées dans visual studio 2015 et ne sont pas prises en charge dans visual studio 2017.

Un [`__declspec`](../../cpp/declspec.md) modificateur utilisé implique un État par processus.  [`/clr:pure`](../../build/reference/clr-common-language-runtime-compilation.md) implique un par [`appdomain`](../../cpp/appdomain.md) État.  Par conséquent, la déclaration d’une variable avec le modificateur de *mot clé* **`__declspec`** et la compilation avec **`/clr:pure`** ne sont pas autorisées.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3389 :

```cpp
// C3389.cpp
// compile with: /clr:pure /c
__declspec(dllexport) int g2 = 0;   // C3389
```
