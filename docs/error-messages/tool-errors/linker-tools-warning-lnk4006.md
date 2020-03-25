---
title: Avertissement des outils Éditeur de liens LNK4006
ms.date: 11/04/2016
f1_keywords:
- LNK4006
helpviewer_keywords:
- LNK4006
ms.assetid: 3a637d17-1676-4ea6-bd8b-290137d28d3b
ms.openlocfilehash: d949ba259de8e131f6191e757119b4c42effc3d4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194315"
---
# <a name="linker-tools-warning-lnk4006"></a>Avertissement des outils Éditeur de liens LNK4006

symbole déjà défini dans l’objet ; seconde définition ignorée

Le `symbol` donné, affiché dans sa forme décorée, a été défini plusieurs fois. Lorsque cet avertissement est rencontré, `symbol` est ajouté deux fois, mais seul son premier formulaire sera utilisé.

Vous pouvez recevoir cet avertissement si vous essayez de fusionner deux bibliothèques d’importation en une seule.

Si vous reconstruisez la bibliothèque Runtime C, vous pouvez ignorer ce message.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Le `symbol` donné peut être une fonction packagée, créée en compilant avec [/Gy](../../build/reference/gy-enable-function-level-linking.md). Ce symbole a été inclus dans plusieurs fichiers mais a été modifié entre les compilations. Recompilez tous les fichiers qui incluent l' `symbol`.

1. Le `symbol` donné peut avoir été défini différemment dans deux objets membres dans des bibliothèques différentes.

1. Un absolu peut avoir été défini deux fois, avec une valeur différente dans chaque définition.

1. Si le message d’erreur est reçu lors de la combinaison de bibliothèques, `symbol` existe déjà dans la bibliothèque ajoutée à.
