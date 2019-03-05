---
title: --Overridables, commentaire
ms.date: 11/04/2016
helpviewer_keywords:
- Overridables comment in MFC source files
- MFC source files, Overridables comment
- overriding, Overridables comment in MFC source files
- comments, MFC
ms.assetid: 8968dea5-0d94-451f-bcb2-991580e65ba2
ms.openlocfilehash: 90d6a585f62de589299147edce87332d96c6dbb8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57282043"
---
# <a name="-overridables-comment"></a>// Remplaçable, commentaire

La `// Overridables` section d’une déclaration de classe MFC contient des fonctions virtuelles que vous pouvez substituer dans une classe dérivée, lorsque vous avez besoin modifier le comportement de la classe de base. Ils sont généralement nommés en commençant par « On », bien qu’il ne soit pas strictement nécessaire. Fonctions ici sont conçues pour être remplacés et souvent d’implémenter ou de fournir une sorte de « rappel » ou « associer ». En règle générale, ces membres sont protégés.

Dans la bibliothèque MFC elle-même, les fonctions virtuelles pures sont toujours placées dans cette section. Une fonction virtuelle pure en C++ fait partie de la forme :

`virtual void OnDraw( ) = 0;`

Dans l’exemple de liste à partir de la classe `CStdioFile`, dans [un exemple des commentaires](../mfc/an-example-of-the-comments.md), la liste ne comprend pas de section overridables. Classe `CDocument`, quant à eux, répertorie les fonctions de membres substituables environ 10.

Dans certaines classes, vous pouvez également voir le commentaire `// Advanced Overridables`. Ce sont des fonctions n'avancées que les programmeurs doivent essayer de substituer. Vous devrez probablement jamais les remplacer.

> [!NOTE]
>  Les conventions décrites dans cet article fonctionnent également bien, en règle générale, pour les propriétés et méthodes Automation (anciennement appelé OLE Automation). Méthodes d’automatisation sont similaires aux opérations MFC. Propriétés d’Automation sont similaires aux attributs MFC. Les événements Automation (pris en charge pour les contrôles ActiveX, anciennement appelés contrôles OLE) sont similaires aux fonctions membres substituables MFC.

## <a name="see-also"></a>Voir aussi

[Utilisation des fichiers sources MFC](../mfc/using-the-mfc-source-files.md)<br/>
[Un exemple des commentaires](../mfc/an-example-of-the-comments.md)<br/>
[Commentaire sur l’implémentation](../mfc/decrement-implementation-comment.md)<br/>
[/ Constructeurs, commentaire](../mfc/decrement-constructors-comment.md)<br/>
[Commentaire d’attributs](../mfc/decrement-attributes-comment.md)<br/>
[Commentaire d’opérations](../mfc/decrement-operations-comment.md)
