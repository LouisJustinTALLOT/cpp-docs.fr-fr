---
title: Erreur irrécupérable C1071
ms.date: 11/04/2016
f1_keywords:
- C1071
helpviewer_keywords:
- C1071
ms.assetid: 489f1786-370e-4ecd-af67-538fe6e5bd4e
ms.openlocfilehash: 8fe6b0f3bb1253f72c97f29070ba81cdbdf80508
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166657"
---
# <a name="fatal-error-c1071"></a>Erreur irrécupérable C1071

fin de fichier inattendue dans un commentaire

Le compilateur a atteint la fin du fichier lors de l’analyse d’un commentaire.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Terminaison de commentaire manquante (* /).

1. Caractères de saut de ligne manquants après un commentaire sur la dernière ligne d’un fichier source.

L’exemple suivant génère l’erreur C1071 :

```
// C1071.cpp
int main() {
}

/* this comment is fine */
/* forgot the closing tag        // C1071
```