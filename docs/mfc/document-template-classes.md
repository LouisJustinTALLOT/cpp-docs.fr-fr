---
title: Classes de modèle de document | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.document
dev_langs:
- C++
helpviewer_keywords:
- document templates [MFC], classes
ms.assetid: 901749e9-8048-44a0-b5e2-361554650a73
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d9958484633dd736426fc91321d0964abf0ad7e1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343539"
---
# <a name="document-template-classes"></a>Classes de modèle de document
Les objets de modèle de document coordonnent la création de document, vue et les objets de fenêtre frame lorsqu’un document ou la vue est créée.  
  
 [CDocTemplate](../mfc/reference/cdoctemplate-class.md)  
 La classe de base pour les modèles de document. Vous n’utiliserez jamais cette classe directement. au lieu de cela, vous utilisez une des autres classes de modèle de document dérivés de cette classe.  
  
 [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)  
 Un modèle pour les documents de l’interface multidocument (MDI). Les applications MDI peuvent ouvrir plusieurs documents à la fois.  
  
 [CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md)  
 Un modèle pour les documents dans l’interface monodocument (SDI). Les applications SDI n'ont qu’un seul document à la fois.  
  
## <a name="related-class"></a>Classe connexe  
 [CCreateContext](../mfc/reference/ccreatecontext-structure.md)  
 Une structure passée par un modèle de document à des fonctions de création de fenêtre pour coordonner la création d’objets document, vue et fenêtre frame.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../mfc/class-library-overview.md)

