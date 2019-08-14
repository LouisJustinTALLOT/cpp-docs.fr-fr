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
ms.openlocfilehash: 6f23f792f750e4352494bf3e4bde08f0fe360439
ms.sourcegitcommit: db1ed91fa7451ade91c3fb76bc7a2b857f8a5eef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68980491"
---
# <a name="using-the-mfc-source-files"></a>Utilisation des fichiers sources MFC

La bibliothèque MFC (Microsoft Foundation Class) fournit du code source complet. Les fichiers d’en-tête (. h) se trouvent dans le répertoire \atlmfc\include les fichiers d’implémentation (. cpp) se trouvent dans le répertoire \atlmfc\src\mfc

Cette famille d’articles explique les conventions utilisées par MFC pour commenter les différentes parties de chaque classe, ce que signifient ces commentaires et ce que vous devez trouver dans chaque section. Les assistants visuels C++ utilisent des conventions similaires pour les classes qu’ils créent pour vous, et vous trouverez probablement ces conventions utiles pour votre propre code.

Vous connaissez peut-être les mots clés **public**, **protected**et **Private** C++ . Dans les fichiers d’en-tête MFC, vous trouverez chaque classe peut avoir plusieurs de chacune d’elles. Par exemple, les variables et les fonctions des membres publics peuvent être sous plusieurs mots clés **publics** . C’est parce que MFC sépare les variables et les fonctions membres en fonction de leur utilisation, et non du type d’accès autorisé. MFC utilise la modération **privée** . Même les éléments considérés comme des détails d’implémentation sont souvent **protégés**et les nombreuses fois sont **publics**. Bien que l’accès aux détails d’implémentation soit déconseillé, les MFC ne quittent pas la décision.

Dans les fichiers sources MFC et les fichiers d’en-tête créés par l’Assistant Application MFC, vous trouverez des commentaires tels que ceux-ci dans les déclarations de classe (généralement dans cet ordre):

`// Constructors`

`// Attributes`

`// Operations`

`// Overridables`

`// Implementation`

Les sujets abordés dans cette série d’articles sont les suivants:

- [Un exemple des commentaires](../mfc/an-example-of-the-comments.md)

- [//Commentaire sur l’implémentation](../mfc/decrement-implementation-comment.md)

- [Le commentaire des constructeurs//](../mfc/decrement-constructors-comment.md)

- [Le commentaire//Attributes](../mfc/decrement-attributes-comment.md)

- [Le commentaire//Operations](../mfc/decrement-operations-comment.md)

- [Commentaire//remplaçable](../mfc/decrement-overridables-comment.md)

## <a name="see-also"></a>Voir aussi

[Rubriques MFC générales](../mfc/general-mfc-topics.md)
