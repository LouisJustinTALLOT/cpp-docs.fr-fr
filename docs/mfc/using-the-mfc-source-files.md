---
title: À l’aide de la bibliothèque MFC des fichiers sources | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e63383e372227dc14ce90843b03b6cb0c029b52a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46383855"
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

