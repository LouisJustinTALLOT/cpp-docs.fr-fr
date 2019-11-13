---
title: Avertissement du compilateur (niveau 1) C4788
ms.date: 11/04/2016
f1_keywords:
- C4788
helpviewer_keywords:
- C4788
ms.assetid: 47d75bda-f833-4bdd-93a0-a134df0cd303
ms.openlocfilehash: 03ce38aaa910a410025c5cccdf39646d34104779
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052390"
---
# <a name="compiler-warning-level-1-c4788"></a>Avertissement du compilateur (niveau 1) C4788

'identificateur' : l’identificateur a été tronqué en caractères’nombre'

Le compilateur limite la longueur maximale autorisée pour un nom de fonction. Lorsque le compilateur génère funclets pour le code EH/SEH, il forme le nom du funclet en ajoutant au début le nom de la fonction avec du texte, par exemple « __catch », «\__unwind » ou une autre chaîne.

Le nom de funclet résultant peut être trop long et le compilateur le tronque et génère C4788.

Pour résoudre cet avertissement, raccourcissez le nom de la fonction d’origine. Si la fonction est une C++ fonction de modèle ou une méthode, utilisez un typedef pour une partie du nom. Exemple :

```cpp
C1<x, y, z<T>>::C2<a,b,c>::f
```

peut être remplacé par :

```cpp
typedef C1<x, y, z<T>>::C2<a,b,c> new_class ;
new_class::f
```

Cet avertissement se produit uniquement dans le compilateur x64.