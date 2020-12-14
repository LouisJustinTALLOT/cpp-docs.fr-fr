---
description: 'En savoir plus sur : barres de boîte de dialogue'
title: Barres de boîte de dialogue
ms.date: 11/19/2018
helpviewer_keywords:
- MFC, control bars
- CDialogBar class [MFC], dialog bars
- control bars [MFC], dialog bars
- dialog bars
- dialog bars [MFC], about dialog bars
ms.assetid: 485c8055-6bb0-4051-8417-dd2971499321
ms.openlocfilehash: 701954dc9ec682bd95258b26d7af1290ea2da521
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97261630"
---
# <a name="dialog-bars"></a>Barres de boîte de dialogue

Une barre de boîte de dialogue est une barre d’outils, un type de [barre de contrôle](control-bars.md) qui peut contenir tout type de contrôle. Comme il présente les caractéristiques d’une boîte de dialogue non modale, un objet [CDialogBar](reference/cdialogbar-class.md) fournit une barre d’outils plus puissante.

Il existe plusieurs différences clés entre une barre d’outils et un `CDialogBar` objet. Un `CDialogBar` objet est créé à partir d’une ressource de modèle de boîte de dialogue, que vous pouvez créer avec l’éditeur de boîtes de dialogue Visual C++ et qui peut contenir n’importe quel type de contrôle Windows. L’utilisateur peut effectuer une tabulation à partir du contrôle jusqu’au contrôle. Vous pouvez également spécifier un style d’alignement pour aligner la barre de boîte de dialogue avec n’importe quelle partie de la fenêtre frame parente ou même pour la conserver en place si le parent est redimensionné. L’illustration suivante montre une barre de boîte de dialogue avec un large éventail de contrôles.

![Barre de boîte de dialogue VC](../mfc/media/vc378t1.gif "Barre de boîte de dialogue VC") <br/>
Une barre de boîte de dialogue

À d’autres égards, l’utilisation d’un `CDialogBar` objet est semblable à l’utilisation d’une boîte de dialogue non modale. Utilisez l’éditeur de boîtes de dialogue pour concevoir et créer la ressource de boîte de dialogue.

L’une des causes des barres de boîte de dialogue est qu’elles peuvent inclure des contrôles autres que des boutons.

Bien qu’il soit normal de dériver vos propres classes de dialogue de `CDialog` , vous ne dérivez généralement pas votre propre classe pour une barre de boîte de dialogue. Les barres de boîte de dialogue sont des extensions d’une fenêtre principale et tous les messages de notification de contrôle de barre de boîte de dialogue, tels que **BN_CLICKED** ou **EN_CHANGE**, sont envoyés au parent de la barre de boîte de dialogue, la fenêtre principale.

## <a name="see-also"></a>Voir aussi

[Éléments de l’interface utilisateur](user-interface-elements-mfc.md)<br/>
[Exemple](../overview/visual-cpp-samples.md)
