---
title: --Constructors, commentaire
ms.date: 11/04/2016
helpviewer_keywords:
- constructors comment
- declarations, constructors
- MFC source files, Constructors comment
- declaring constructors, code comments
- comments, MFC
- comments, constructors comment
- constructors [MFC], declaring
- instance constructors, code comments
ms.assetid: f400774e-ba85-49ed-85b7-70ef2f7dcb2b
ms.openlocfilehash: ee36ad991f2a19211b494010d6ff0a5338b80557
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480702"
---
# <a name="-constructors-comment"></a>// Constructeurs, commentaire

La `// Constructors` section d’une déclaration de classe MFC déclare des constructeurs (dans le sens C++), ainsi que toutes les fonctions d’initialisation requises pour utiliser réellement l’objet. Par exemple, `CWnd::Create` est dans la section de constructeurs car avant d’utiliser le `CWnd` de l’objet, il doit être « entièrement construit » en appelant tout d’abord le constructeur C++, puis le `Create` (fonction). En règle générale, ces membres sont publics.

Par exemple, la classe `CStdioFile` a trois constructeurs, un d'entre eux est indiqué dans la liste sous [un exemple des commentaires](../mfc/an-example-of-the-comments.md).

## <a name="see-also"></a>Voir aussi

[Utilisation des fichiers sources MFC](../mfc/using-the-mfc-source-files.md)<br/>
[Commentaire sur l’implémentation](../mfc/decrement-implementation-comment.md)<br/>
[Commentaire d’attributs](../mfc/decrement-attributes-comment.md)<br/>
[Commentaire d’opérations](../mfc/decrement-operations-comment.md)<br/>
[Remplaçable (commentaire)](../mfc/decrement-overridables-comment.md)

