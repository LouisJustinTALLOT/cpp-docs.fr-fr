---
title: Erreur irrécupérable RW1025 du compilateur de ressources | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW1025
dev_langs:
- C++
helpviewer_keywords:
- RW1025
ms.assetid: 561a02af-e7e0-442a-8ad3-a00b2ca1b62e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2bf7bdeed320c004ffb75fa1d25d9b89147b0c13
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117398"
---
# <a name="resource-compiler-fatal-error-rw1025"></a>Erreur irrécupérable RW1025 du compilateur de ressources 

Insuffisance de mémoire de tas lointain

Recherchez les logiciels résidant en mémoire qui peut être occuper trop d’espace. Utilisez le programme CHKDSK pour connaître la quantité de mémoire vous disposez.

Si vous créez un fichier de ressources de grande taille, fractionner le script de ressources en deux fichiers. Après avoir créé les deux fichiers .res, utilisez la ligne de commande MS-DOS pour les joindre :

```
copy first.res /b + second.res /b full.res
```