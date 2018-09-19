---
title: Erreur irrécupérable C1071 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1071
dev_langs:
- C++
helpviewer_keywords:
- C1071
ms.assetid: 489f1786-370e-4ecd-af67-538fe6e5bd4e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1b4487de60148e1da7668bc44c996c5dfb955a9d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033002"
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