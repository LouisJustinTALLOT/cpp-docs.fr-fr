---
description: 'En savoir plus sur : erreur du compilateur C2998'
title: Erreur du compilateur C2998
ms.date: 11/04/2016
f1_keywords:
- C2998
helpviewer_keywords:
- C2998
ms.assetid: 8193d491-b5d9-4477-acb1-cf166889c070
ms.openlocfilehash: 43370ee8659335f6d14a2850ba0b874434786ca0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97253609"
---
# <a name="compiler-error-c2998"></a>Erreur du compilateur C2998

'identifier' : ne peut pas être une définition de modèle

Le compilateur n’a pas pu traiter la syntaxe utilisée dans la définition de modèle.

L’exemple suivant génère l’erreur C2998 :

```cpp
// C2998.cpp
// compile with: /c
template <class T> int x = 1018; // C2998
```
