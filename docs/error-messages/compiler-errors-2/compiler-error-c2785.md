---
title: Erreur du compilateur C2785
ms.date: 11/04/2016
f1_keywords:
- C2785
helpviewer_keywords:
- C2785
ms.assetid: d8d13360-0d00-4815-8475-b49c7f0dc0f3
ms.openlocfilehash: 6aff2e5c96e3c79fc748d8a95779d6a08647ab03
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739621"
---
# <a name="compiler-error-c2785"></a>Erreur du compilateur C2785

'déclaration1 'et’déclaration2 'ont des types de retour différents

Le type de retour de la spécialisation de modèle de fonction diffère du type de retour du modèle de fonction principal.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Vérifiez la cohérence de toutes les spécialisations du modèle de fonction.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2785 :

```cpp
// C2785.cpp
// compile with: /c
template<class T> void f(T);

template<> int f(int); // C2785
template<> void f(int); // OK
```
