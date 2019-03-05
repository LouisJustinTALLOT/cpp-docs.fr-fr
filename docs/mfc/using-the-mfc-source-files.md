---
title: Utilisation des fichiers sources MFC
ms.date: 11/04/2016
helpviewer_keywords:
- public members
- source files
- MFC, source files
- MFC source files
- comments, MFC
- private member access
- protected member access
- source files, MFC
ms.assetid: 3230e8fb-3b69-4ddf-9538-365ac7ea5e72
ms.openlocfilehash: ac8d8ea64de9fd93487b3108857669931e31d0be
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57267028"
---
# <a name="using-the-mfc-source-files"></a>Utilisation des fichiers sources MFC

La bibliothèque Microsoft Foundation classes (MFC) fournit du code source complet. Fichiers d’en-tête (.h) se trouvent dans le répertoire \atlmfc\include ; fichiers d’implémentation (.cpp) sont dans le répertoire \atlmfc\src\mfc.

Cette série d’articles décrit les conventions utilisées par MFC pour commenter les différentes parties de chaque classe, ce que signifient ces commentaires, et ce que vous attendre à trouver dans chaque section. Les Assistants Visual C++ utilisent des conventions similaires pour les classes qu’il crée pour vous, et vous trouverez probablement ces conventions utiles pour votre propre code.

Vous connaissez peut-être le **public**, **protégé**, et **privé** mots clés C++. Lorsque vous examinez les fichiers d’en-tête MFC, vous trouverez que chaque classe peut avoir plusieurs de chacun d'entre eux. Par exemple, les fonctions et variables de membre public peuvent être sous plusieurs **public** mot clé. Il s’agit, car MFC sépare les variables membres et des fonctions selon leur utilisation, pas par le type d’accès autorisé. MFC utilise **privé** avec parcimonie ; y compris les éléments considérés comme des détails d’implémentation sont généralement protégés et très souvent publics. Bien que l’accès aux détails d’implémentation est déconseillée, MFC laisse la décision pour vous.

Dans les fichiers sources MFC et les fichiers de l’Assistant Application MFC crée, vous trouverez des commentaires comme celles-ci dans les déclarations de classe (généralement dans cet ordre) :

`// Constructors`

`// Attributes`

`// Operations`

`// Overridables`

`// Implementation`

Les sujets abordés dans cette série d’articles incluent :

- [Un exemple des commentaires](../mfc/an-example-of-the-comments.md)

- [Les / / commentaire d’implémentation](../mfc/decrement-implementation-comment.md)

- [Les / / constructeurs (commentaire)](../mfc/decrement-constructors-comment.md)

- [Les / / attributs commentaire](../mfc/decrement-attributes-comment.md)

- [Les / / opérations comment](../mfc/decrement-operations-comment.md)

- [Les / / remplaçable commentaire](../mfc/decrement-overridables-comment.md)

## <a name="see-also"></a>Voir aussi

[Rubriques MFC générales](../mfc/general-mfc-topics.md)
