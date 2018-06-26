---
title: --Commentaire d’attributs | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- comments, Attributes
- Attributes comment in MFC source files
- MFC source files, Attributes comment
- public attributes comment
ms.assetid: 96388e11-42df-4994-aedf-decd152961a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 44b34c2e2d22d0a0a2feb15f6bf2793b68dc7042
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929567"
---
# <a name="-attributes-comment"></a>// Attributs, commentaire
La `// Attributes` section d’une déclaration de classe MFC contient les attributs (ou propriétés) publics de l’objet. En général, il s’agit de variables membres ou fonctions Get/Set. Les fonctions « Get » et « Set » peuvent ou ne peuvent pas être virtuelles. Les fonctions « Get » sont généralement **const**, car dans la plupart des cas ils n’ont pas d’effets secondaires. Ces membres sont normalement publiques ; attributs protégés et privés sont généralement détectées dans la section d’implémentation.  
  
 Dans l’exemple de liste à partir de la classe `CStdioFile`, sous [un exemple des commentaires](../mfc/an-example-of-the-comments.md), la liste inclut une variable membre, *m_pStream*. Classe `CDC` répertorie près de 20 membres sous ce commentaire.  
  
> [!NOTE]
>  Grandes classes, telles que `CDC` et `CWnd`, ne peuvent avoir des membres autant qui simplement répertoriant tous les attributs d’un groupe ajouteriez pas beaucoup plus de clarté. Dans ce cas, la bibliothèque de classes utilise les autres commentaires comme en-têtes pour délimiter davantage les membres. Par exemple, `CDC` utilise `// Device-Context Functions`, `// Drawing Tool Functions`, `// Drawing Attribute Functions`et bien plus encore. Les groupes qui représentent les attributs suit la syntaxe habituelle décrite ci-dessus. Nombreuses classes OLE possèdent une section d’implémentation appelée `// Interface Maps`.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des fichiers sources MFC](../mfc/using-the-mfc-source-files.md)   
 [Un exemple des commentaires](../mfc/an-example-of-the-comments.md)   
 [Commentaire sur l’implémentation](../mfc/decrement-implementation-comment.md)   
 [Commentaire de constructeurs](../mfc/decrement-constructors-comment.md)   
 [Commentaire d’opérations](../mfc/decrement-operations-comment.md)   
 [Remplaçable commentaire](../mfc/decrement-overridables-comment.md)

