---
title: Erreur irrécupérable NMAKE U1035
ms.date: 11/04/2016
f1_keywords:
- U1035
helpviewer_keywords:
- U1035
ms.assetid: 68f0cc59-007e-4109-ac30-7ac4ac447e6d
ms.openlocfilehash: 3eda424574dfa48901cf4dc6aea3b28beb739dc0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193717"
---
# <a name="nmake-fatal-error-u1035"></a>Erreur irrécupérable NMAKE U1035

erreur de syntaxe : séparateur' : 'ou' = 'attendu

Un signe deux-points ( **:** ) ou un signe égal ( **=** ) était attendu.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Un signe deux-points ne suit pas une cible.

1. Un signe deux-points et aucun espace (par exemple, :) suivi d’une cible à une seule lettre. NMAKE l’a interprété comme une spécification de lecteur.

1. Un signe deux-points ne suit pas une règle d’inférence.

1. Une définition de macro n’a pas été suivie d’un signe égal.

1. Un caractère suit une barre oblique inverse ( **\\** ) qui a été utilisée pour continuer une commande sur une nouvelle ligne.

1. Une chaîne apparaissant n’a pas suivi une règle de syntaxe NMAKE.

1. Le Makefile a été mis en forme par un traitement de texte.
