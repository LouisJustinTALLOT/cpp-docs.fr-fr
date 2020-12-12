---
description: 'En savoir plus sur : avertissement des outils Éditeur de liens LNK4022'
title: Avertissement des outils Éditeur de liens LNK4022
ms.date: 11/04/2016
f1_keywords:
- LNK4022
helpviewer_keywords:
- LNK4022
ms.assetid: 890f487e-db98-45dd-a226-c7ccead82b1e
ms.openlocfilehash: f0f968bf8e562d87e2227fb67f7a37b450c813b1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331937"
---
# <a name="linker-tools-warning-lnk4022"></a>Avertissement des outils Éditeur de liens LNK4022

Impossible de trouver une correspondance unique pour le symbole’Symbol'

LINK ou LIB a trouvé plusieurs correspondances pour le symbole non décoré donné et il n’a pas pu résoudre l’ambiguïté. Aucun fichier de sortie (. exe,. dll,. exp ou. lib) n’est produit. Cet avertissement est suivi d’un avertissement [LNK4002](../../error-messages/tool-errors/linker-tools-warning-lnk4002.md) pour chaque symbole dupliqué et est enfin suivi de l’erreur irrécupérable [LNK1152](../../error-messages/tool-errors/linker-tools-error-lnk1152.md).

Pour éviter cet avertissement, spécifiez le symbole sous sa forme décorée. Exécutez [DUMPBIN](../../build/reference/dumpbin-options.md) sur l’objet pour afficher les noms décorés.
