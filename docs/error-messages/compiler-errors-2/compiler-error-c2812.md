---
title: Erreur du compilateur C2812 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2812
dev_langs:
- C++
helpviewer_keywords:
- C2812
ms.assetid: 22aadb8c-7232-489d-a3ad-60662dda30a8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0c5469e4f7be3c164cc63fa30f5069009846be48
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34705021"
---
# <a name="compiler-error-c2812"></a>Erreur du compilateur C2812

> \#importation n’est pas prise en charge avec/clr : pure et/CLR : safe

## <a name="remarks"></a>Notes

Le **/CLR : pure** et **/CLR : safe** options du compilateur sont déconseillées dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

[directive #import](../../preprocessor/hash-import-directive-cpp.md) n’est pas pris en charge avec **/CLR : pure** et **/CLR : safe** car `#import` requiert l’utilisation de bibliothèques de prise en charge du compilateur natif.

## <a name="example"></a>Exemple

L’exemple suivant génère C2812.

```cpp
// C2812.cpp
// compile with: /clr:pure /c
#import "importlib.tlb"   // C2812
```