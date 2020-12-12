---
description: 'En savoir plus sur : erreur du compilateur C3179'
title: Erreur du compilateur C3179
ms.date: 11/04/2016
f1_keywords:
- C3179
helpviewer_keywords:
- C3179
ms.assetid: 60d7e41b-25fd-48ac-8b79-830c062f4dcd
ms.openlocfilehash: 5f4b573c822eff68d972517f9fac093071cf2a0c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97174154"
---
# <a name="compiler-error-c3179"></a>Erreur du compilateur C3179

type managé ou WinRT sans nom interdit

Tous les structs et toutes les classes CLR et WinRT doivent avoir des noms.

L'exemple suivant génère l'erreur C3179 et montre comment la corriger :

```cpp
// C3179a.cpp
// compile with: /clr /c
typedef value struct { // C3179
// try the following line instead
// typedef value struct MyStruct {
   int i;
} V;
```
