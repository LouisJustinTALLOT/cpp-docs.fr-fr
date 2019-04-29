---
title: Erreur irrécupérable NMAKE U1073
ms.date: 11/04/2016
f1_keywords:
- U1073
helpviewer_keywords:
- U1073
ms.assetid: d46bf2dd-400a-4802-9db2-f832e1c97f02
ms.openlocfilehash: 2aa02fd86906bd545373a313fa5e6e409ffb3cf9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366927"
---
# <a name="nmake-fatal-error-u1073"></a>Erreur irrécupérable NMAKE U1073

ignorez comment rendre 'targetname'

La cible spécifiée n’existe pas, et il n’existe aucune commande à exécuter ou une règle d’inférence à appliquer.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Vérifiez l’orthographe du nom de la cible.

1. Si *targetname* est une pseudocible, spécifiez-la en tant que cible dans un autre bloc de description.

1. Si *targetname* est un appel de macro, veillez à ne développe pas une chaîne null.