---
title: Erreur du compilateur C2917
ms.date: 11/04/2016
f1_keywords:
- C2917
helpviewer_keywords:
- C2917
ms.assetid: ec9da9ee-0f37-47b3-87dd-19ef5a14dc4c
ms.openlocfilehash: 6926d96eccadacd427cc4d13b93db494809c3775
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530466"
---
# <a name="compiler-error-c2917"></a>Erreur du compilateur C2917

'name' : paramètre de modèle non valide

Une liste de paramètres de modèles contient un identificateur qui n’était pas un paramètre de modèle.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2917.

```
// C2917.cpp
// compile with: /c
template<class T> class Vector {
   void sort();
};

template<class T*> void Vector<T>::sort() {}   // C2917
// try the following line instead
// template<class T> void Vector<T>::sort() {}
```