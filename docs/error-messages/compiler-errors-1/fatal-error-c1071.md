---
title: Erreur irrécupérable C1071
ms.date: 11/04/2016
f1_keywords:
- C1071
helpviewer_keywords:
- C1071
ms.assetid: 489f1786-370e-4ecd-af67-538fe6e5bd4e
ms.openlocfilehash: 2f39359d55b5564c6379c84f07e942cf3484e011
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747408"
---
# <a name="fatal-error-c1071"></a>Erreur irrécupérable C1071

fin de fichier inattendue dans un commentaire

Le compilateur a atteint la fin du fichier lors de l’analyse d’un commentaire.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Indicateur de fin de commentaire manquant (*/).

1. Caractère de saut de ligne manquant après un commentaire sur la dernière ligne d’un fichier source.

L’exemple suivant génère l’C1071 :

```cpp
// C1071.cpp
int main() {
}

/* this comment is fine */
/* forgot the closing tag        // C1071
```
