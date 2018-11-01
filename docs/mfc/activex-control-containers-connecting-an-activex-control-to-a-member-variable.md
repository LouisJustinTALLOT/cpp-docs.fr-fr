---
title: "Conteneurs de contrôles ActiveX : association d'un contrôle ActiveX à une variable membre"
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX control containers [MFC], accessing ActiveX controls
- ActiveX controls [MFC], member variables of project
- connecting ActiveX controls to container member variables
- ActiveX controls [MFC], accessing
- member variables [MFC], ActiveX controls in project
- ActiveX control containers [MFC], ActiveX controls as member variables
ms.assetid: 7898a336-440d-4a60-be43-cb062b807aee
ms.openlocfilehash: 2234647e933e37ff82845c4b40dc93cefeb55575
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50446460"
---
# <a name="activex-control-containers-connecting-an-activex-control-to-a-member-variable"></a>Conteneurs de contrôles ActiveX : association d'un contrôle ActiveX à une variable membre

Pour accéder à un contrôle ActiveX à partir de son application de conteneur de contrôle le plus simple consiste à associer le contrôle ActiveX à une variable de membre de la classe de boîte de dialogue qui contiendra le contrôle.

> [!NOTE]
>  Ce n’est pas la seule façon d’accéder à un contrôle incorporé à partir d’une classe de conteneur, mais dans le cadre de cet article, il est suffisant.

### <a name="adding-a-member-variable-to-the-dialog-class"></a>Ajout d’une variable de membre à la classe de boîte de dialogue

1. À partir de l’affichage de classes, cliquez sur la classe de boîte de dialogue principale pour ouvrir le menu contextuel. Par exemple, `CContainerDlg`.

1. Dans le menu contextuel, cliquez sur **ajouter** , puis **ajouter une Variable**.

1. Dans l’Assistant Ajout de Variable membre, cliquez sur **variable de contrôle**.

1. Dans le **ID de contrôle** zone de liste, sélectionnez l’ID de contrôle du contrôle ActiveX incorporé. Par exemple, `IDC_CIRCCTRL1`.

1. Dans le **nom de la Variable** , entrez un nom.

   Par exemple, *m_circctl*.

1. Cliquez sur **Terminer** pour accepter votre choix et de quitter l’Assistant Ajout de Variable membre.

## <a name="see-also"></a>Voir aussi

[Conteneurs de contrôles ActiveX](../mfc/activex-control-containers.md)

