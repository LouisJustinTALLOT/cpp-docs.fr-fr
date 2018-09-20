---
title: Barres de boîte de dialogue | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, control bars
- CDialogBar class [MFC], dialog bars
- control bars [MFC], dialog bars
- dialog bars
- dialog bars [MFC], about dialog bars
ms.assetid: 485c8055-6bb0-4051-8417-dd2971499321
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ed0e773dda8a1a31a028a0b6c5e349b2e3655982
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401496"
---
# <a name="dialog-bars"></a>Barres de boîte de dialogue

Une barre de boîte de dialogue est une barre d’outils, un type de [barre de contrôle](../mfc/control-bars.md) qui peut contenir n’importe quel type de contrôle. Car il présente les caractéristiques d’une boîte de dialogue non modale, une [CDialogBar](../mfc/reference/cdialogbar-class.md) objet fournit une barre d’outils plus puissant.

Il existe plusieurs différences clés entre une barre d’outils et un `CDialogBar` objet. Un `CDialogBar` objet est créé à partir d’une ressource de modèle de boîte de dialogue, que vous pouvez créer avec l’éditeur de boîtes de dialogue Visual C++ et qui peut contenir n’importe quel type de contrôle de Windows. L’utilisateur peut tabuler de contrôle au contrôle. Et vous pouvez spécifier un style d’alignement pour aligner la barre de boîte de dialogue avec n’importe quelle partie de la fenêtre frame parente ou même à laisser en place si le parent est redimensionné. La figure suivante illustre une barre de boîte de dialogue avec un large éventail de contrôles.

![Barre de boîte de dialogue VC](../mfc/media/vc378t1.gif "vc378t1") une barre de boîte de dialogue

Dans les autres égards, travaillez sur un `CDialogBar` objet est semblable à l’utilisation avec une boîte de dialogue non modale. Utiliser l’éditeur de boîtes de dialogue pour concevoir et créer la ressource de boîte de dialogue.

L’un des avantages des barres de boîte de dialogue est qu’ils peuvent inclure des contrôles autres que des boutons.

S’il est normal pour dériver vos propres classes de boîte de dialogue à partir de `CDialog`, vous ne dérivez pas généralement votre propre classe pour une barre de boîte de dialogue. Barres de boîte de dialogue sont des extensions à la fenêtre principale et les messages de notification de contrôle de barre de boîte de dialogue, tel que **BN_CLICKED** ou **EN_CHANGE**, sera envoyé au parent de la boîte de dialogue de la barre, la fenêtre principale.

## <a name="see-also"></a>Voir aussi

[Éléments d’Interface utilisateur](../mfc/user-interface-elements-mfc.md)<br/>
[Exemple](../visual-cpp-samples.md)

