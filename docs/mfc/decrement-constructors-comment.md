---
title: --Commentaire de constructeurs | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f58c8410de51a4692dd0e7f018d40eaa28c0dae8
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929580"
---
# <a name="-constructors-comment"></a>// Constructeurs, commentaire
La `// Constructors` section d’une déclaration de classe MFC déclare des constructeurs (dans le sens C++), ainsi que toutes les fonctions d’initialisation requises pour utiliser réellement l’objet. Par exemple, `CWnd::Create` est dans la section des constructeurs car avant d’utiliser le `CWnd` de l’objet, il doit être « entièrement construit » en appelant le constructeur C++ d’abord, puis le `Create` (fonction). En règle générale, ces membres sont publics.  
  
 Par exemple, la classe `CStdioFile` a trois constructeurs, dont est indiqué dans la liste sous [un exemple des commentaires](../mfc/an-example-of-the-comments.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des fichiers sources MFC](../mfc/using-the-mfc-source-files.md)   
 [Commentaire sur l’implémentation](../mfc/decrement-implementation-comment.md)   
 [Commentaire d’attributs](../mfc/decrement-attributes-comment.md)   
 [Commentaire d’opérations](../mfc/decrement-operations-comment.md)   
 [Remplaçable commentaire](../mfc/decrement-overridables-comment.md)

