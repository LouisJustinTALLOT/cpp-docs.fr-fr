---
title: Composants de boîte de dialogue dans le Framework | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], creating
- dialog classes [MFC], dialog box components
- MFC dialog boxes [MFC], about MFC dialog boxes
- dialog templates [MFC], MFC framework
- MFC dialog boxes [MFC], dialog resource
ms.assetid: 592db160-0a8a-49be-ac72-ead278aca53f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6936a48d1a3e1845d56c73524c84800d9d605155
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50065504"
---
# <a name="dialog-box-components-in-the-framework"></a>Composants de boîte de dialogue dans le Framework

Dans l’infrastructure MFC, une boîte de dialogue comporte deux composants :

- Une ressource de modèle de boîte de dialogue qui spécifie les contrôles de la boîte de dialogue et leur emplacement.

   La ressource de boîte de dialogue stocke un modèle de boîte de dialogue à partir duquel Windows crée la fenêtre de la boîte de dialogue et l’affiche. Le modèle spécifie les caractéristiques de la boîte de dialogue, y compris sa taille, emplacement, style et les types et les positions des contrôles de la boîte de dialogue. Vous utiliserez généralement un modèle de boîte de dialogue stocké en tant que ressource, mais vous pouvez également créer votre propre modèle en mémoire.

- Une classe de boîte de dialogue, dérivée de [CDialog](../mfc/reference/cdialog-class.md), fournir une interface de programmation pour la gestion de la boîte de dialogue.

   Une boîte de dialogue est une fenêtre et est attachée à une fenêtre Windows lorsqu’elle est visible. Lorsque la fenêtre de la boîte de dialogue est créée, la ressource de modèle de boîte de dialogue est utilisée comme modèle pour créer des contrôles de fenêtre pour la boîte de dialogue enfants.

## <a name="see-also"></a>Voir aussi

[Boîtes de dialogue](../mfc/dialog-boxes.md)<br/>
[Cycle de vie d’une boîte de dialogue](../mfc/life-cycle-of-a-dialog-box.md)

