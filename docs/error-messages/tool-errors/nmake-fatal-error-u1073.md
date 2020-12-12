---
description: 'En savoir plus sur : erreur irrécupérable NMAKE NMAKE U1073'
title: Erreur irrécupérable NMAKE U1073
ms.date: 11/04/2016
f1_keywords:
- U1073
helpviewer_keywords:
- U1073
ms.assetid: d46bf2dd-400a-4802-9db2-f832e1c97f02
ms.openlocfilehash: bd622f37720cf5e992a1d82ea97ca1ff50344c0c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345444"
---
# <a name="nmake-fatal-error-u1073"></a>Erreur irrécupérable NMAKE U1073

Je ne sais pas comment faire de « NomCible »

La cible spécifiée n’existe pas et il n’existe aucune commande à exécuter ou règle d’inférence à appliquer.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Vérifiez l’orthographe du nom de la cible.

1. Si *TargetName* est une pseudocible, spécifiez-la en tant que cible dans un autre bloc de description.

1. Si *TargetName* est un appel de macro, assurez-vous qu’il ne s’étend pas à une chaîne NULL.
