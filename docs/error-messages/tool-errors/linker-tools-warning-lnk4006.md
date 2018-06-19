---
title: Avertissement LNK4006 des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4006
dev_langs:
- C++
helpviewer_keywords:
- LNK4006
ms.assetid: 3a637d17-1676-4ea6-bd8b-290137d28d3b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 261d5dcc27c44291ddc6de4a6440cde040a84ed7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302553"
---
# <a name="linker-tools-warning-lnk4006"></a>Avertissement des outils Éditeur de liens LNK4006
symbole déjà défini dans l’objet ; seconde définition ignorée  
  
 Le `symbol` donné, affiché dans sa forme décorée, a été défini plusieurs fois. Lorsque cet avertissement est rencontré, `symbol` sera ajouté deux fois, mais seule sa première forme sera utilisé.  
  
 Vous pouvez obtenir cet avertissement si vous essayez de fusionner deux bibliothèques d’importation en une seule.  
  
 Si vous régénérez la bibliothèque Runtime C, vous pouvez ignorer ce message.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.  
  
1.  La donnée `symbol` peut être une fonction packagée, créée par la compilation avec [/Gy](../../build/reference/gy-enable-function-level-linking.md). Ce symbole a été inclus dans plusieurs fichiers, mais a été modifié entre les compilations. Recompilez tous les fichiers qui incluent le `symbol`.  
  
2.  La donnée `symbol` peut avoir été défini différemment dans les deux objets membres de bibliothèques différentes.  
  
3.  Absolu peut avoir été défini à deux reprises, avec une valeur différente dans chaque définition.  
  
4.  Si le message d’erreur est reçu lors de la combinaison de bibliothèques, `symbol` existe déjà dans la bibliothèque ajoutée.