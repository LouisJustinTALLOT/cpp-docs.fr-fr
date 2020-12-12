---
description: 'En savoir plus sur : erreur du compilateur C2785'
title: Erreur du compilateur C2785
ms.date: 11/04/2016
f1_keywords:
- C2785
helpviewer_keywords:
- C2785
ms.assetid: d8d13360-0d00-4815-8475-b49c7f0dc0f3
ms.openlocfilehash: f40b652e30b30f0ef17426b547337352181383e0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97297900"
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
