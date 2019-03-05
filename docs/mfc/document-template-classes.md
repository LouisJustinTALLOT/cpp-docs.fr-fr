---
title: Classes de modèle de document
ms.date: 11/04/2016
f1_keywords:
- vc.classes.document
helpviewer_keywords:
- document templates [MFC], classes
ms.assetid: 901749e9-8048-44a0-b5e2-361554650a73
ms.openlocfilehash: 2589bc8f04e791f73529af91ffb148c2c717cd08
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57294575"
---
# <a name="document-template-classes"></a>Classes de modèle de document

Objets de modèle de document coordonnent la création de document, vue et les objets de fenêtre frame lorsqu’un document ou la vue est créée.

[CDocTemplate](../mfc/reference/cdoctemplate-class.md)<br/>
La classe de base pour les modèles de document. Vous n’utiliserez jamais cette classe directement. au lieu de cela, vous utilisez une des autres classes de modèle de document dérivés de cette classe.

[CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)<br/>
Un modèle pour les documents dans l’interface multidocument (MDI). Les applications MDI peuvent ouvrir plusieurs documents à la fois.

[CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md)<br/>
Un modèle pour les documents dans l’interface monodocument (SDI). Les applications SDI n'ont qu’un seul document à la fois.

## <a name="related-class"></a>Classe connexe

[CCreateContext](../mfc/reference/ccreatecontext-structure.md)<br/>
Une structure passée par un modèle de document à des fonctions de création de la fenêtre pour coordonner la création des objets document, vue et fenêtre frame.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)
