---
title: "Barres de boîte de dialogue | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC, control bars
- CDialogBar class [MFC], dialog bars
- control bars [MFC], dialog bars
- dialog bars
- dialog bars [MFC], about dialog bars
ms.assetid: 485c8055-6bb0-4051-8417-dd2971499321
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 100d17c3b5594c7c44e6002d4f65577bb2ee701e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="dialog-bars"></a>Barres de boîte de dialogue
Une barre de boîte de dialogue est une barre d’outils, un type de [barre de contrôle](../mfc/control-bars.md) qui peut contenir tout type de contrôle. Car il présente les caractéristiques d’une boîte de dialogue non modale, un [CDialogBar](../mfc/reference/cdialogbar-class.md) objet fournit une barre d’outils plus puissant.  
  
 Il existe plusieurs différences importantes entre une barre d’outils et un `CDialogBar` objet. A `CDialogBar` objet est créé à partir d’une ressource de modèle de boîte de dialogue, que vous pouvez créer avec l’éditeur de boîte de dialogue Visual C++ et qui peut contenir tout type de contrôle de Windows. L’utilisateur peut tabuler de contrôle pour le contrôle. Et vous pouvez spécifier un style d’alignement pour aligner la barre de boîte de dialogue avec n’importe quelle partie de la fenêtre frame parente ou même de le laisser en place si le parent est redimensionné. La figure suivante illustre une barre de boîte de dialogue avec un large éventail de contrôles.  
  
 ![Barre de boîte de dialogue VC](../mfc/media/vc378t1.gif "vc378t1")  
Une barre de boîte de dialogue  
  
 Autres égards, utilisation avec un `CDialogBar` objet est semblable à l’utilisation avec une boîte de dialogue non modale. Utilisez l’éditeur de boîte de dialogue pour concevoir et créer la ressource de boîte de dialogue.  
  
 L’un des avantages des barres de boîte de dialogue est qu’ils peuvent inclure des contrôles autres que des boutons.  
  
 S’il est normal pour dériver vos propres classes de boîte de dialogue à partir de `CDialog`, vous ne pas généralement dériver votre propre classe d’une barre de boîte de dialogue. Barres de boîte de dialogue sont des extensions à la fenêtre principale et les messages de notification de contrôle de barre de boîte de dialogue, tel que **BN_CLICKED** ou **EN_CHANGE**, sera envoyé au parent de la boîte de dialogue de la barre, la fenêtre principale.  
  
## <a name="see-also"></a>Voir aussi  
 [Éléments d’Interface utilisateur](../mfc/user-interface-elements-mfc.md)   
 [Exemple](../visual-cpp-samples.md)

