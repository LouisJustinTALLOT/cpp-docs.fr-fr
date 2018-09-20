---
title: --Operations, commentaire | Microsoft Docs
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
ms.openlocfilehash: 73c4a7a70c9f2ed987337426793bd462c2a94309
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46372494"
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

