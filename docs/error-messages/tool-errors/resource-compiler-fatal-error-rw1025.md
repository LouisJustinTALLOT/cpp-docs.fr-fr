---
description: 'En savoir plus sur : erreur irrécupérable du compilateur de ressources RW1025 du compilateur'
title: 'Erreur irrécupérable RW1025 du compilateur de ressources '
ms.date: 11/04/2016
f1_keywords:
- RW1025
helpviewer_keywords:
- RW1025
ms.assetid: 561a02af-e7e0-442a-8ad3-a00b2ca1b62e
ms.openlocfilehash: 40404f8d6dc16b73f93255a18ce8c632cc1e014a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97237190"
---
# <a name="resource-compiler-fatal-error-rw1025"></a>Erreur irrécupérable RW1025 du compilateur de ressources 

Mémoire du tas Far insuffisante

Recherchez les logiciels résidant en mémoire qui peuvent occuper trop d’espace. Utilisez le programme CHKDSK pour déterminer la quantité de mémoire dont vous disposez.

Si vous créez un fichier de ressources volumineux, fractionnez le script de ressources en deux fichiers. Après avoir créé deux fichiers. res, utilisez la ligne de commande MS-DOS pour les joindre :

```
copy first.res /b + second.res /b full.res
```
