---
description: 'En savoir plus sur : erreur du compilateur C2943'
title: Erreur du compilateur C2943
ms.date: 11/04/2016
f1_keywords:
- C2943
helpviewer_keywords:
- C2943
ms.assetid: ede6565e-d892-44c0-8eee-c69545f3be2e
ms.openlocfilehash: f85000ae554e25f2ca783b605b036abb3f04eadb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97249579"
---
# <a name="compiler-error-c2943"></a>Erreur du compilateur C2943

'classe' : type-class-id redéfini comme argument de type d’un modèle

Vous ne pouvez pas utiliser une classe générique ni de modèle à la place d’un symbole comme argument de type générique ou d’un modèle.

L’exemple suivant génère l’erreur C2943 :

```cpp
// C2943.cpp
// compile with: /c
template<class T>
class List {};

template<class List<int> > class MyList;   // C2943
template<class T >  class MyList;
```
