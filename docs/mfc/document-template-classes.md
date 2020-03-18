---
title: Classes de modèle de document
ms.date: 11/04/2016
helpviewer_keywords:
- document templates [MFC], classes
ms.assetid: 901749e9-8048-44a0-b5e2-361554650a73
ms.openlocfilehash: 82b9ce4c242df7c85ada0722b2c1e993a0cf3f81
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446917"
---
# <a name="document-template-classes"></a>Classes de modèle de document

Les objets de modèle de document coordonnent la création d’objets de fenêtre de document, de vue et de frame lors de la création d’un nouveau document ou d’une nouvelle vue.

[CDocTemplate](../mfc/reference/cdoctemplate-class.md)<br/>
Classe de base pour les modèles de document. Vous n’utiliserez jamais cette classe directement ; au lieu de cela, vous utilisez l’une des autres classes de modèle de document dérivées de cette classe.

[CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)<br/>
Modèle pour les documents dans l’interface multidocument (MDI, multiple document interface). Plusieurs documents peuvent être ouverts à la fois dans les applications MDI.

[CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md)<br/>
Modèle pour les documents dans l’interface SDI (single document interface). Les applications SDI n’ont qu’un seul document ouvert à la fois.

## <a name="related-class"></a>Classe associée

[CCreateContext](../mfc/reference/ccreatecontext-structure.md)<br/>
Structure passée par un modèle de document aux fonctions de création de fenêtre pour coordonner la création d’objets de document, de vue et de fenêtre frame.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)
