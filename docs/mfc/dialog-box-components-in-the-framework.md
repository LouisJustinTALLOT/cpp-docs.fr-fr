---
title: Composants de boîte de dialogue dans le Framework
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], creating
- dialog classes [MFC], dialog box components
- MFC dialog boxes [MFC], about MFC dialog boxes
- dialog templates [MFC], MFC framework
- MFC dialog boxes [MFC], dialog resource
ms.assetid: 592db160-0a8a-49be-ac72-ead278aca53f
ms.openlocfilehash: 15d01924be811a9c9ec8ea333870f444bf9aa61a
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685831"
---
# <a name="dialog-box-components-in-the-framework"></a>Composants de boîte de dialogue dans le Framework

Dans l’infrastructure MFC, une boîte de dialogue comporte deux composants :

- Ressource de modèle de boîte de dialogue qui spécifie les contrôles de la boîte de dialogue et leur emplacement.

   La ressource de boîte de dialogue stocke un modèle de boîte de dialogue à partir duquel Windows crée la fenêtre de boîte de dialogue et l’affiche. Le modèle spécifie les caractéristiques de la boîte de dialogue, notamment sa taille, son emplacement, son style et les types et positions des contrôles de la boîte de dialogue. Vous allez généralement utiliser un modèle de boîte de dialogue stocké en tant que ressource, mais vous pouvez également créer votre propre modèle en mémoire.

- Classe Dialog, dérivée de [CDialog](../mfc/reference/cdialog-class.md), pour fournir une interface de programmation pour la gestion de la boîte de dialogue.

   Une boîte de dialogue est une fenêtre qui est attachée à une fenêtre Windows quand elle est visible. Lorsque la fenêtre de boîte de dialogue est créée, la ressource de modèle de boîte de dialogue est utilisée comme modèle pour créer des contrôles de fenêtre enfants pour la boîte de dialogue.

## <a name="see-also"></a>Voir aussi

[Boîtes de dialogue](../mfc/dialog-boxes.md)<br/>
[Utilisation des boîtes de dialogue dans MFC](../mfc/life-cycle-of-a-dialog-box.md)
