---
title: Classes de modèle de document
ms.date: 11/04/2016
helpviewer_keywords:
- document templates [MFC], classes
ms.assetid: 901749e9-8048-44a0-b5e2-361554650a73
ms.openlocfilehash: dffde80093f98fc1c81a6c20dfaf92b82e3b4c78
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618982"
---
# <a name="document-template-classes"></a>Classes de modèle de document

Les objets de modèle de document coordonnent la création d’objets de fenêtre de document, de vue et de frame lors de la création d’un nouveau document ou d’une nouvelle vue.

[CDocTemplate](reference/cdoctemplate-class.md)<br/>
Classe de base pour les modèles de document. Vous n’utiliserez jamais cette classe directement ; au lieu de cela, vous utilisez l’une des autres classes de modèle de document dérivées de cette classe.

[CMultiDocTemplate](reference/cmultidoctemplate-class.md)<br/>
Modèle pour les documents dans l’interface multidocument (MDI, multiple document interface). Plusieurs documents peuvent être ouverts à la fois dans les applications MDI.

[CSingleDocTemplate](reference/csingledoctemplate-class.md)<br/>
Modèle pour les documents dans l’interface SDI (single document interface). Les applications SDI n’ont qu’un seul document ouvert à la fois.

## <a name="related-class"></a>Classe associée

[CCreateContext](reference/ccreatecontext-structure.md)<br/>
Structure passée par un modèle de document aux fonctions de création de fenêtre pour coordonner la création d’objets de document, de vue et de fenêtre frame.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](class-library-overview.md)
