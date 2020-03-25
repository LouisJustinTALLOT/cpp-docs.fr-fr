---
title: Erreur irrécupérable RW1025 du compilateur de ressources
ms.date: 11/04/2016
f1_keywords:
- RW1025
helpviewer_keywords:
- RW1025
ms.assetid: 561a02af-e7e0-442a-8ad3-a00b2ca1b62e
ms.openlocfilehash: 9b6697dff0a445cc342f30d08bd79822b02df7b8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172722"
---
# <a name="resource-compiler-fatal-error-rw1025"></a>Erreur irrécupérable RW1025 du compilateur de ressources

Mémoire du tas Far insuffisante

Recherchez les logiciels résidant en mémoire qui peuvent occuper trop d’espace. Utilisez le programme CHKDSK pour déterminer la quantité de mémoire dont vous disposez.

Si vous créez un fichier de ressources volumineux, fractionnez le script de ressources en deux fichiers. Après avoir créé deux fichiers. res, utilisez la ligne de commande MS-DOS pour les joindre :

```
copy first.res /b + second.res /b full.res
```
