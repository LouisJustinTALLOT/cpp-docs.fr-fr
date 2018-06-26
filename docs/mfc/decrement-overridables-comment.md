---
title: --Remplaçable commentaire | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Overridables comment in MFC source files
- MFC source files, Overridables comment
- overriding, Overridables comment in MFC source files
- comments, MFC
ms.assetid: 8968dea5-0d94-451f-bcb2-991580e65ba2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6a1b9b04647717fc5892421f2b45947ebd079a0c
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36928725"
---
# <a name="-overridables-comment"></a>// Remplaçable, commentaire
La `// Overridables` section d’une déclaration de classe MFC contient des fonctions virtuelles que vous pouvez substituer dans une classe dérivée, lorsque vous avez besoin modifier le comportement de la classe de base. Ils sont généralement nommés en commençant par « On », bien qu’il ne soit pas strictement nécessaire. Fonctions ici sont conçues pour être remplacés et souvent d’implémenter ou de fournir une sorte de « rappel » ou « raccorder ». En règle générale, ces membres sont protégés.  
  
 Dans l’application MFC elle-même, les fonctions virtuelles pures sont toujours placées dans cette section. Une fonction virtuelle pure en C++ fait partie de la forme :  
  
 `virtual void OnDraw( ) = 0;`  
  
 Dans l’exemple de liste à partir de la classe `CStdioFile`, dans [un exemple des commentaires](../mfc/an-example-of-the-comments.md), la liste ne comprend aucune section remplaçable. Classe `CDocument`, quant à eux, répertorie environ 10 fonctions membres substituables.  
  
 Dans certaines classes, vous pouvez également voir le commentaire `// Advanced Overridables`. Ce sont des fonctions n'avancées que les programmeurs doivent essayer de substituer. Vous devrez probablement jamais les remplacer.  
  
> [!NOTE]
>  Les conventions décrites dans cet article également fonctionnent correctement, en général, les propriétés et méthodes Automation (anciennement appelé OLE Automation). Les méthodes Automation sont similaires aux opérations MFC. Propriétés Automation sont similaires aux attributs MFC. Les événements Automation (pris en charge pour les contrôles ActiveX, anciennement appelés contrôles OLE) sont semblables aux fonctions membres substituables MFC.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des fichiers sources MFC](../mfc/using-the-mfc-source-files.md)   
 [Un exemple des commentaires](../mfc/an-example-of-the-comments.md)   
 [Commentaire sur l’implémentation](../mfc/decrement-implementation-comment.md)   
 [Commentaire de constructeurs](../mfc/decrement-constructors-comment.md)   
 [Commentaire d’attributs](../mfc/decrement-attributes-comment.md)   
 [Commentaire d’opérations](../mfc/decrement-operations-comment.md)

