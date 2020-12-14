---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4788'
title: Avertissement du compilateur (niveau 1) C4788
ms.date: 11/04/2016
f1_keywords:
- C4788
helpviewer_keywords:
- C4788
ms.assetid: 47d75bda-f833-4bdd-93a0-a134df0cd303
ms.openlocfilehash: 2aa87fd8a09b9f308e7fbb51fc4f05792210b0c1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97234603"
---
# <a name="compiler-warning-level-1-c4788"></a>Avertissement du compilateur (niveau 1) C4788

'identificateur' : l’identificateur a été tronqué en caractères’nombre'

Le compilateur limite la longueur maximale autorisée pour un nom de fonction. Lorsque le compilateur génère funclets pour le code EH/SEH, il forme le nom funclet en ajoutant au début du nom de la fonction un texte, par exemple « __catch », « \_ _unwind » ou une autre chaîne.

Le nom de funclet résultant peut être trop long et le compilateur le tronque et génère C4788.

Pour résoudre cet avertissement, raccourcissez le nom de la fonction d’origine. Si la fonction est une méthode ou une fonction de modèle C++, utilisez un typedef pour une partie du nom. Par exemple :

```cpp
C1<x, y, z<T>>::C2<a,b,c>::f
```

peut être remplacé par :

```cpp
typedef C1<x, y, z<T>>::C2<a,b,c> new_class ;
new_class::f
```

Cet avertissement se produit uniquement dans le compilateur x64.
