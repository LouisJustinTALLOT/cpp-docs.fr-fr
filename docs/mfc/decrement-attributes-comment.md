---
title: --Attributes, commentaire
ms.date: 11/04/2016
helpviewer_keywords:
- comments, Attributes
- Attributes comment in MFC source files
- MFC source files, Attributes comment
- public attributes comment
ms.assetid: 96388e11-42df-4994-aedf-decd152961a7
ms.openlocfilehash: a74d0f9d6ffb0bd2d057cf46f7308d8b6a81f98c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62241499"
---
# <a name="-attributes-comment"></a>// Attributs, commentaire

La `// Attributes` section d’une déclaration de classe MFC contient les attributs (ou propriétés) publics de l’objet. En général, il s’agit de variables membres ou les fonctions Get/Set. Les fonctions « Get » et « Set » peuvent être ou non virtuelles. Les fonctions « Get » sont généralement **const**, car dans la plupart des cas, ils n’ont pas les effets secondaires. Ces membres sont normalement publics ; attributs protégés et privés se trouvent généralement dans la section d’implémentation.

Dans l’exemple de liste à partir de la classe `CStdioFile`, sous [un exemple des commentaires](../mfc/an-example-of-the-comments.md), la liste comprend une variable de membre, *m_pStream*. Classe `CDC` répertorie près de 20 membres sous ce commentaire.

> [!NOTE]
>  Classes de grande taille, telles que `CDC` et `CWnd`, peuvent avoir des membres autant que simplement répertoriant tous les attributs dans un seul groupe ajouteriez pas grand-chose à plus de clarté. Dans ce cas, la bibliothèque de classes utilise les commentaires des autres comme en-têtes pour délimiter davantage les membres. Par exemple, `CDC` utilise `// Device-Context Functions`, `// Drawing Tool Functions`, `// Drawing Attribute Functions`et bien plus encore. Les groupes qui représentent les attributs suivent la syntaxe habituelle décrite ci-dessus. De nombreuses classes OLE ont une section d’implémentation appelée `// Interface Maps`.

## <a name="see-also"></a>Voir aussi

[Utilisation des fichiers sources MFC](../mfc/using-the-mfc-source-files.md)<br/>
[Un exemple des commentaires](../mfc/an-example-of-the-comments.md)<br/>
[Commentaire sur l’implémentation](../mfc/decrement-implementation-comment.md)<br/>
[/ Constructeurs, commentaire](../mfc/decrement-constructors-comment.md)<br/>
[Commentaire d’opérations](../mfc/decrement-operations-comment.md)<br/>
[Remplaçable (commentaire)](../mfc/decrement-overridables-comment.md)
