---
title: 'Conteneurs de contrôles ActiveX : Association d’un contrôle ActiveX à une Variable membre | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ActiveX control containers [MFC], accessing ActiveX controls
- ActiveX controls [MFC], member variables of project
- connecting ActiveX controls to container member variables
- ActiveX controls [MFC], accessing
- member variables [MFC], ActiveX controls in project
- ActiveX control containers [MFC], ActiveX controls as member variables
ms.assetid: 7898a336-440d-4a60-be43-cb062b807aee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b3aa243ab8c0fb49e20e5b7485acdcd8bb808831
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930466"
---
# <a name="activex-control-containers-connecting-an-activex-control-to-a-member-variable"></a>Conteneurs de contrôles ActiveX : association d'un contrôle ActiveX à une variable membre
Pour accéder à un contrôle ActiveX à partir de son application conteneur, le plus simple consiste à associer le contrôle ActiveX à une variable membre de la classe de boîte de dialogue qui contiendra le contrôle.  
  
> [!NOTE]
>  Ce n’est pas la seule façon d’accéder à un contrôle incorporé à partir d’une classe de conteneur, mais elle est suffisante pour les besoins de cet article.  
  
### <a name="adding-a-member-variable-to-the-dialog-class"></a>Ajout d’une variable de membre à la classe de boîte de dialogue  
  
1.  À partir de l’affichage de classes, cliquez sur la classe de boîte de dialogue principale pour ouvrir le menu contextuel. Par exemple, `CContainerDlg`.  
  
2.  Dans le menu contextuel, cliquez sur **ajouter** , puis **ajouter une Variable**.  
  
3.  Dans l’Assistant Ajout de Variable membre, cliquez sur **la variable de contrôle**.  
  
4.  Dans le **ID de contrôle** zone de liste, sélectionnez l’ID de contrôle du contrôle ActiveX incorporé. Par exemple, `IDC_CIRCCTRL1`.  
  
5.  Dans le **nom de la Variable** , entrez un nom.  
  
     Par exemple, *m_circctl*.  
  
6.  Cliquez sur **Terminer** pour valider vos sélections et quitter l’Assistant Ajout de Variable membre.  
  
## <a name="see-also"></a>Voir aussi  
 [Conteneurs de contrôles ActiveX](../mfc/activex-control-containers.md)

