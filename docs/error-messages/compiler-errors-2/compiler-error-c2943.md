---
title: Erreur du compilateur C2943
ms.date: 11/04/2016
f1_keywords:
- C2943
helpviewer_keywords:
- C2943
ms.assetid: ede6565e-d892-44c0-8eee-c69545f3be2e
ms.openlocfilehash: 53340611ef92aac7c9bed30f364fed424fdfe140
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50469525"
---
# <a name="compiler-error-c2943"></a>Erreur du compilateur C2943

'classe' : type-class-id redéfini comme argument de type d’un modèle

Vous ne pouvez pas utiliser une classe générique ni de modèle à la place d’un symbole comme argument de type générique ou d’un modèle.

L’exemple suivant génère l’erreur C2943 :

```
// C2943.cpp
// compile with: /c
template<class T>
class List {};

template<class List<int> > class MyList;   // C2943
template<class T >  class MyList;
```