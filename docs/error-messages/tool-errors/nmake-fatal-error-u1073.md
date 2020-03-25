---
title: Erreur irrécupérable NMAKE U1073
ms.date: 11/04/2016
f1_keywords:
- U1073
helpviewer_keywords:
- U1073
ms.assetid: d46bf2dd-400a-4802-9db2-f832e1c97f02
ms.openlocfilehash: 97d44594540d18bf008757506a9e36e6d16d2cd7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182693"
---
# <a name="nmake-fatal-error-u1073"></a>Erreur irrécupérable NMAKE U1073

Je ne sais pas comment faire de « NomCible »

La cible spécifiée n’existe pas et il n’existe aucune commande à exécuter ou règle d’inférence à appliquer.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Vérifiez l’orthographe du nom de la cible.

1. Si *TargetName* est une pseudocible, spécifiez-la en tant que cible dans un autre bloc de description.

1. Si *TargetName* est un appel de macro, assurez-vous qu’il ne s’étend pas à une chaîne NULL.
