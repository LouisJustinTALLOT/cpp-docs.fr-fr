---
title: Erreur du compilateur C3389 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3389
dev_langs:
- C++
helpviewer_keywords:
- C3389
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b540f87458c75ddf7d57626b6251248652b96213
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704303"
---
# <a name="compiler-error-c3389"></a>Erreur du compilateur C3389

> __declspec (*mot clé*) ne peut pas être utilisé avec/clr : pure ou/CLR : safe

## <a name="remarks"></a>Notes

Le **/CLR : pure** et **/CLR : safe** options du compilateur sont déconseillées dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

A [__declspec](../../cpp/declspec.md) modificateur utilisé implique un état par processus.  [/ CLR : pure](../../build/reference/clr-common-language-runtime-compilation.md) implique un par [appdomain](../../cpp/appdomain.md) état.  Par conséquent, déclarer une variable avec le `keyword` **__declspec** modificateur et la compilation avec **/CLR : pure** n’est pas autorisée.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3389 :

```cpp
// C3389.cpp
// compile with: /clr:pure /c
__declspec(dllexport) int g2 = 0;   // C3389
```