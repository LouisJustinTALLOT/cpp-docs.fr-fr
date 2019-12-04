---
title: Erreur irrécupérable C1004
ms.date: 11/04/2016
f1_keywords:
- C1004
helpviewer_keywords:
- C1004
ms.assetid: dbe034b0-6eb0-41b4-a50c-2fccf9e78ad4
ms.openlocfilehash: 82a1a3e410505be53d4356e46d5521aebb72763c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756966"
---
# <a name="fatal-error-c1004"></a>Erreur irrécupérable C1004

fin de fichier inattendue trouvée

Le compilateur a atteint la fin d’un fichier source sans résoudre une construction. Il se peut qu’il manque l’un des éléments suivants dans le code :

- Accolade fermante

- Parenthèse fermante

- Marqueur de commentaire de fermeture (*/)

- Un point-virgule

Pour résoudre cette erreur, vérifiez les éléments suivants :

- Le lecteur de disque par défaut ne dispose pas de suffisamment d’espace pour les fichiers temporaires, ce qui nécessite environ deux fois plus d’espace que le fichier source.

- Une directive de `#if` qui prend la valeur false ne dispose pas d’une directive de `#endif` de fermeture.

- Un fichier source ne se termine pas par un retour chariot et un saut de ligne.

L’exemple suivant génère l’C1004 :

```cpp
// C1004.cpp
#if TEST
int main() {}
// C1004
```

Solution possible :

```cpp
// C1004b.cpp
#if TEST
#endif

int main() {}
```
