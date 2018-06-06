---
title: Compilateur avertissement (niveau 1) C4399 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4399
dev_langs:
- C++
helpviewer_keywords:
- C4399
ms.assetid: f58d9ba7-71a0-4c3b-b26f-f946dda8af30
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aedad6aed07a6056f74ad338037a7268c722627f
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34703718"
---
# <a name="compiler-warning-level-1-c4399"></a>Avertissement du compilateur (niveau 1) C4399

> '*symbole*' : symbole par processus ne doit pas être marqué avec __declspec (dllimport) lors de la compilation avec/clr : pure

## <a name="remarks"></a>Notes

Le **/CLR : pure** option du compilateur est déconseillée dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

Données à partir d’une image native ou une image avec des constructions natives et CLR ne peuvent pas être importées dans une image pure. Pour résoudre cet avertissement, compilez avec **/CLR** (pas **/CLR : pure**) ou supprimer `__declspec(dllimport)`.

## <a name="example"></a>Exemple

L’exemple suivant génère C4399.

```cpp
// C4399.cpp
// compile with: /clr:pure /doc /W1 /c
__declspec(dllimport) __declspec(process) extern const int i;   // C4399
```