---
title: Avertissement du compilateur (niveau 1) C4788
ms.date: 11/04/2016
f1_keywords:
- C4788
helpviewer_keywords:
- C4788
ms.assetid: 47d75bda-f833-4bdd-93a0-a134df0cd303
ms.openlocfilehash: 76a33b24446debffb2c00bf1b0497cfc86022ce0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175136"
---
# <a name="compiler-warning-level-1-c4788"></a>Avertissement du compilateur (niveau 1) C4788

'identificateur' : l’identificateur a été tronqué en caractères’nombre'

Le compilateur limite la longueur maximale autorisée pour un nom de fonction. Lorsque le compilateur génère funclets pour le code EH/SEH, il forme le nom du funclet en ajoutant au début le nom de la fonction avec du texte, par exemple « __catch », «\__unwind » ou une autre chaîne.

Le nom de funclet résultant peut être trop long et le compilateur le tronque et génère C4788.

Pour résoudre cet avertissement, raccourcissez le nom de la fonction d’origine. Si la fonction est une C++ fonction de modèle ou une méthode, utilisez un typedef pour une partie du nom. Par exemple :

```cpp
C1<x, y, z<T>>::C2<a,b,c>::f
```

peut être remplacé par :

```cpp
typedef C1<x, y, z<T>>::C2<a,b,c> new_class ;
new_class::f
```

Cet avertissement se produit uniquement dans le compilateur x64.
