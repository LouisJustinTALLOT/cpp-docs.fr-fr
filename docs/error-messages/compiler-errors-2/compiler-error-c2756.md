---
description: 'En savoir plus sur : erreur du compilateur C2756'
title: Erreur du compilateur C2756
ms.date: 11/04/2016
f1_keywords:
- C2756
helpviewer_keywords:
- C2756
ms.assetid: 42eb988d-4043-4dee-8fd4-596949f69a55
ms.openlocfilehash: 94a3211bd45136f74e87a971aa3fd3717355f8d6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336202"
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
