---
description: 'En savoir plus sur : erreur du compilateur C3113'
title: Erreur du compilateur C3113
ms.date: 11/04/2016
f1_keywords:
- C3113
helpviewer_keywords:
- C3113
ms.assetid: 3afdc668-b29e-474e-9ea3-aa027d42db7c
ms.openlocfilehash: dcad27e26e0795b8d1901cca51dc5cd16a88ae5c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97115987"
---
# <a name="compiler-error-c3113"></a>Erreur du compilateur C3113

une’structure’ne peut pas être un modèle/générique

Vous avez tenté de créer un modèle de classe ou un générique de classe à partir d’une interface ou d’une énumération.

L’exemple suivant génère l’C3113 :

```cpp
// C3113.cpp
// compile with: /c
template <class T>
enum E {};   // C3113
// try the following line instead
// class MyClass{};
```
