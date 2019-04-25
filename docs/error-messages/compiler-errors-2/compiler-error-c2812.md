---
title: Erreur du compilateur C2812
ms.date: 11/04/2016
f1_keywords:
- C2812
helpviewer_keywords:
- C2812
ms.assetid: 22aadb8c-7232-489d-a3ad-60662dda30a8
ms.openlocfilehash: 88b071f38cf41db9c929d25ffd526b3f2b7ca468
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62382955"
---
# <a name="compiler-error-c2812"></a>Erreur du compilateur C2812

> \#importation n’est pas prise en charge avec/clr : pure et/CLR : safe

## <a name="remarks"></a>Notes

Le **/CLR : pure** et **/CLR : safe** options du compilateur sont déconseillées dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

[directive #import](../../preprocessor/hash-import-directive-cpp.md) n’est pas pris en charge avec **/CLR : pure** et **/CLR : safe** car `#import` nécessite l’utilisation de bibliothèques de prise en charge du compilateur natif.

## <a name="example"></a>Exemple

L’exemple suivant génère C2812.

```cpp
// C2812.cpp
// compile with: /clr:pure /c
#import "importlib.tlb"   // C2812
```