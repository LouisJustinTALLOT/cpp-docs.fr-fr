---
title: --Opérations commentaire | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Operations comment in MFC source files
- comments, MFC
- MFC source files, Operations comments
ms.assetid: f3bff48d-26be-4db6-8435-9e4d079838c9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0ee6bf4a330a5fdf1ac294157e69dab39b5f2bdd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342269"
---
# <a name="-operations-comment"></a>// Opérations, commentaires
La `// Operations` section d’une déclaration de classe MFC contient des fonctions de membre que vous pouvez appeler sur l’objet pour effectuer les opérations ou effectuer des actions (opérations). Ces fonctions sont généralement non -**const** , car ils ont généralement des effets secondaires. Ils peuvent être virtuelles ou non virtuelles selon les besoins de la classe. En règle générale, ces membres sont publics.  
  
 Dans l’exemple de liste à partir de la classe `CStdioFile`, dans [un exemple des commentaires](../mfc/an-example-of-the-comments.md), la liste inclut deux fonctions membres sous ce commentaire : `ReadString` et `WriteString`.  
  
 Comme avec les attributs, les opérations peuvent être subdivisées.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des fichiers sources MFC](../mfc/using-the-mfc-source-files.md)   
 [Un exemple des commentaires](../mfc/an-example-of-the-comments.md)   
 [Commentaire sur l’implémentation](../mfc/decrement-implementation-comment.md)   
 [Commentaire de constructeurs](../mfc/decrement-constructors-comment.md)   
 [Commentaire d’attributs](../mfc/decrement-attributes-comment.md)   
 [Remplaçable commentaire](../mfc/decrement-overridables-comment.md)

