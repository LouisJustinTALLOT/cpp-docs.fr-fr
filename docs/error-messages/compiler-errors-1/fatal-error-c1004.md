---
description: 'En savoir plus sur : erreur irrécupérable C1004'
title: Erreur irrécupérable C1004
ms.date: 11/04/2016
f1_keywords:
- C1004
helpviewer_keywords:
- C1004
ms.assetid: dbe034b0-6eb0-41b4-a50c-2fccf9e78ad4
ms.openlocfilehash: f21978f5ff314a8273dde60428dc89ca0c5767b0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97262683"
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

- Une `#if` directive qui prend la valeur false ne dispose pas d’une directive de fermeture `#endif` .

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
