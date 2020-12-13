---
description: 'En savoir plus sur : erreur irrécupérable C1071'
title: Erreur irrécupérable C1071
ms.date: 11/04/2016
f1_keywords:
- C1071
helpviewer_keywords:
- C1071
ms.assetid: 489f1786-370e-4ecd-af67-538fe6e5bd4e
ms.openlocfilehash: c4a6734dcb515b6d495eac720f83ba39be3c3677
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344378"
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
