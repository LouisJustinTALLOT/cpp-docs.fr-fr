---
title: --Implementation, commentaire
ms.date: 11/04/2016
helpviewer_keywords:
- Implementation comment in MFC source files
- comments, MFC
- MFC source files, Implementation comment
- comments, Implementation comments
ms.assetid: 4d799c07-8e71-4a6b-90ab-8282d6ff48ce
ms.openlocfilehash: 377997b66c5b9c005d1e1bee24890b756621b672
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261045"
---
# <a name="-implementation-comment"></a>// Commentaire sur l'implémentation

Le `// Implementation` section est la partie la plus importante de toute déclaration de classe MFC.

Cette section contient tous les détails d’implémentation. Variables membres et les fonctions membres peuvent apparaître dans cette section. Tout élément sous cette ligne peut changer dans une future version de MFC. À moins que vous ne pouvez pas l’éviter, vous fiez pas aux détails ci-dessous le `// Implementation` ligne. En outre, les membres déclarés sous la ligne d’implémentation ne sont pas documentées, bien qu’une implémentation est décrite dans les notes techniques. Les substitutions de fonctions virtuelles dans la classe de base se trouvent dans cette section, quelle que soit la section laquelle la fonction de la classe de base est définie, car le fait qu’une fonction substitue l’implémentation de classe de base est considéré comme un détail d’implémentation. En règle générale, ces membres sont protégés, mais pas toujours.

Remarquez, dans le `CStdioFile` sous [un exemple des commentaires](../mfc/an-example-of-the-comments.md) que les membres déclarés sous le `// Implementation` commentaire peut-être être déclaré comme **public**, **protégé**, ou **privé**. Vous devez uniquement utiliser ces membres avec précaution, car elles peuvent changer à l’avenir. Déclaration d’un groupe de membres en tant que **public** peut s’avérer nécessaire pour l’implémentation de bibliothèque de classe fonctionne correctement. Toutefois, cela ne signifie pas que vous pouvez utiliser en toute sécurité des membres déclarés donc.

> [!NOTE]
>  Vous pouvez rechercher des commentaires les autres types au-dessus ou au-dessous de la `// Implementation` commentaire. Dans les deux cas, ils décrivent les types de membres déclarés ci-dessous les. S’ils apparaissent sous la `// Implementation` commentaire, vous devez supposer que les membres peuvent changer dans les futures versions de MFC.

## <a name="see-also"></a>Voir aussi

[Utilisation des fichiers sources MFC](../mfc/using-the-mfc-source-files.md)<br/>
[Un exemple des commentaires](../mfc/an-example-of-the-comments.md)<br/>
[/ Constructeurs, commentaire](../mfc/decrement-constructors-comment.md)<br/>
[Commentaire d’attributs](../mfc/decrement-attributes-comment.md)<br/>
[Commentaire d’opérations](../mfc/decrement-operations-comment.md)<br/>
[Remplaçable (commentaire)](../mfc/decrement-overridables-comment.md)
