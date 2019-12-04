---
title: Erreur du compilateur C2756
ms.date: 11/04/2016
f1_keywords:
- C2756
helpviewer_keywords:
- C2756
ms.assetid: 42eb988d-4043-4dee-8fd4-596949f69a55
ms.openlocfilehash: f9b3ea261db825f00004a2f447636c15d2d0d52e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759540"
---
# <a name="compiler-error-c2756"></a>Erreur du compilateur C2756

’type de modèle’ : les arguments template par défaut ne sont pas autorisés sur une spécialisation partielle

Le modèle pour une spécialisation partielle ne peut pas contenir d’argument par défaut.

L'exemple suivant génère l'erreur C2756 et montre comment la corriger :

```cpp
// C2756.cpp
template <class T>
struct S {};

template <class T=int>
// try the following line instead
// template <class T>
struct S<T*> {};   // C2756
```
