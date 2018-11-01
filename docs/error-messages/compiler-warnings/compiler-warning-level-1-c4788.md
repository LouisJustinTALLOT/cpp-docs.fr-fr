---
title: Avertissement du compilateur (niveau 1) C4788
ms.date: 11/04/2016
f1_keywords:
- C4788
helpviewer_keywords:
- C4788
ms.assetid: 47d75bda-f833-4bdd-93a0-a134df0cd303
ms.openlocfilehash: c51a4409c2a3028823462539343654b5eac365d0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598170"
---
# <a name="compiler-warning-level-1-c4788"></a>Avertissement du compilateur (niveau 1) C4788

'identificateur' : identificateur tronqué à 'nombre' caractères

Le compilateur limite la longueur maximale autorisée pour un nom de fonction. Lorsque le compilateur génère funclets pour le code EH/SEH, il constitue le nom funclet en ajoutant le préfixe le nom de fonction avec du texte, par exemple « __catch, » «\__unwind », ou une autre chaîne.

Le nom de funclet résultant peut être trop long, et le compilateur tronquer et générer C4788.

Pour résoudre cet avertissement, raccourcissez le nom de fonction d’origine. Si la fonction est une fonction de modèle C++ ou une méthode, utilisez un typedef pour la partie du nom. Exemple :

```
C1<x, y, z<T>>::C2<a,b,c>::f
```

peut être remplacée par :

```
typedef C1<x, y, z<T>>::C2<a,b,c> new_class ;
new_class::f
```

Cet avertissement se produit uniquement dans le x64 compilateur.