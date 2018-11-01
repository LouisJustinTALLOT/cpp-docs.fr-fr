---
title: --Operations, commentaire
ms.date: 11/04/2016
helpviewer_keywords:
- Operations comment in MFC source files
- comments, MFC
- MFC source files, Operations comments
ms.assetid: f3bff48d-26be-4db6-8435-9e4d079838c9
ms.openlocfilehash: 6b84da721bd22723d0eb5a0b520462cd8a4613e8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653193"
---
# <a name="-operations-comment"></a>// Opérations, commentaires

La `// Operations` section d’une déclaration de classe MFC contient des fonctions membres que vous pouvez appeler sur l’objet pour effectuer des opérations ou effectuer des actions (effectuer des opérations). Ces fonctions sont généralement non -**const** , car elles ont généralement des effets secondaires. Ils peuvent être virtuelles ou non virtuelles selon les besoins de la classe. En règle générale, ces membres sont publics.

Dans l’exemple de liste à partir de la classe `CStdioFile`, dans [un exemple des commentaires](../mfc/an-example-of-the-comments.md), la liste inclut deux fonctions membres sous ce commentaire : `ReadString` et `WriteString`.

Comme avec les attributs, les opérations peuvent être subdivisées.

## <a name="see-also"></a>Voir aussi

[Utilisation des fichiers sources MFC](../mfc/using-the-mfc-source-files.md)<br/>
[Un exemple des commentaires](../mfc/an-example-of-the-comments.md)<br/>
[Commentaire sur l’implémentation](../mfc/decrement-implementation-comment.md)<br/>
[/ Constructeurs, commentaire](../mfc/decrement-constructors-comment.md)<br/>
[Commentaire d’attributs](../mfc/decrement-attributes-comment.md)<br/>
[Remplaçable (commentaire)](../mfc/decrement-overridables-comment.md)

