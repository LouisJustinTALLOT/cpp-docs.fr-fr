---
title: Erreur du compilateur C2812
ms.date: 11/04/2016
f1_keywords:
- C2812
helpviewer_keywords:
- C2812
ms.assetid: 22aadb8c-7232-489d-a3ad-60662dda30a8
ms.openlocfilehash: cec92982646c64e6c5b669df328e4836d4f44df8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202097"
---
# <a name="compiler-error-c2812"></a>Erreur du compilateur C2812

> l’importation \#n’est pas prise en charge avec/clr : pure et/CLR : safe

## <a name="remarks"></a>Notes

Les options de compilateur **/clr : pure** et **/clr : safe** sont dépréciées dans Visual Studio 2015 et ne sont pas prises en charge dans Visual Studio 2017.

[#import directive](../../preprocessor/hash-import-directive-cpp.md) n’est pas prise en charge avec **/clr : pure** et **/clr : safe** , car `#import` requiert l’utilisation de bibliothèques de prise en charge du compilateur natif.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2812.

```cpp
// C2812.cpp
// compile with: /clr:pure /c
#import "importlib.tlb"   // C2812
```
