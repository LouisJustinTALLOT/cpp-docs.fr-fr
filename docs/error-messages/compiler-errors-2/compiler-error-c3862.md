---
title: Erreur du compilateur C3862 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3862
dev_langs:
- C++
helpviewer_keywords:
- C3862
ms.assetid: ba547366-4189-4077-8c00-ab45e08a9533
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5b21e457feb6d090e4abaf531293987eb3504457
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704969"
---
# <a name="compiler-error-c3862"></a>Erreur du compilateur C3862

> '*fonction*' : Impossible de compiler une fonction non managée avec/clr : pure ou/CLR : safe

## <a name="remarks"></a>Notes

Le **/CLR : pure** et **/CLR : safe** options du compilateur sont déconseillées dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

Une compilation avec **/CLR : pure** ou **/CLR : safe** produira une image MSIL uniquement, une image avec aucune du code natif (non managé).  Par conséquent, vous ne pouvez pas utiliser le `unmanaged` pragma dans un **/CLR : pure** ou **/CLR : safe** compilation.

Pour plus d’informations, consultez [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) et [managé, non managé](../../preprocessor/managed-unmanaged.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3862 :

```cpp
// C3862.cpp
// compile with: /clr:pure /c
#pragma unmanaged
void f() {}   // C3862
```