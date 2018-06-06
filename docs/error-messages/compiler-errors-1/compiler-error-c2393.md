---
title: Erreur du compilateur C2393 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2393
dev_langs:
- C++
helpviewer_keywords:
- C2393
ms.assetid: 4bd95728-e813-4ce8-844a-c6ebe235ca82
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 057537c8efcf6e827d9ac9aaf36c0eace6d24156
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704028"
---
# <a name="compiler-error-c2393"></a>Erreur du compilateur C2393

> '*symbole*' : symbole par appdomain ne peut pas être alloué dans le segment '*segment*'

## <a name="remarks"></a>Notes

Le **/CLR : pure** et **/CLR : safe** options du compilateur sont déconseillées dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

L’utilisation de [appdomain](../../cpp/appdomain.md) variables implique que vous compilez avec **/CLR : pure** ou **/CLR : safe**, et une image safe ou pure ne peut pas contenir de segments de données.

Consultez [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) pour plus d’informations.

## <a name="example"></a>Exemple

L’exemple suivant génère C2393. Pour résoudre ce problème, ne créez pas un segment de données.

```cpp
// C2393.cpp
// compile with: /clr:pure /c
#pragma data_seg("myseg")
int n = 0;   // C2393
```