---
description: 'En savoir plus sur : erreur du compilateur C2341'
title: Erreur du compilateur C2341
ms.date: 11/04/2016
f1_keywords:
- C2341
helpviewer_keywords:
- C2341
ms.assetid: aa2a7da5-e1c8-4225-9939-5bdc50158f31
ms.openlocfilehash: 47869b6534664358fa80a3ace89fc44fdceefb08
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97234785"
---
# <a name="compiler-error-c2341"></a>Erreur du compilateur C2341

'section Name' : le segment doit être défini à l’aide de #pragma data_seg, code_seg ou section avant d’être utilisé

Une instruction [allocate](../../cpp/allocate.md) fait référence à un segment qui n’est pas encore défini par les pragmas [code_seg](../../preprocessor/code-seg.md), [data_seg](../../preprocessor/data-seg.md)ou [section](../../preprocessor/section.md) .

L’exemple suivant génère l’C2341 :

```cpp
// C2341.cpp
// compile with: /c
__declspec(allocate(".test"))   // C2341
int j = 1;
```

Solution possible :

```cpp
// C2341b.cpp
// compile with: /c
#pragma data_seg(".test")
__declspec(allocate(".test"))
int j = 1;
```
