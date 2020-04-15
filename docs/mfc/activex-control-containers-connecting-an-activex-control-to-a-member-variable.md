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
ms.openlocfilehash: 620a9ec58b3a5a8fcdac63626b81fbc4620de399
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371622"
---
# <a name="activex-control-containers-connecting-an-activex-control-to-a-member-variable"></a>Conteneurs de contrôles ActiveX : association d'un contrôle ActiveX à une variable membre

La façon la plus simple d’accéder à un contrôle ActiveX à partir de son application de conteneur de contrôle est d’associer le contrôle ActiveX à une variable membre de la classe de dialogue qui contiendra le contrôle.

> [!NOTE]
> Ce n’est pas la seule façon d’accéder à un contrôle intégré à partir d’une classe de conteneurs, mais aux fins de cet article, il est suffisant.

### <a name="adding-a-member-variable-to-the-dialog-class"></a>Ajout d’une variable de membre à la classe de dialogue

1. De Class View, cliquez à droite sur la classe de dialogue principal pour ouvrir le menu raccourci. Par exemple : `CContainerDlg`.

1. À partir du menu raccourci, cliquez sur **Ajouter** puis **ajouter Variable**.

1. Dans l’Assistant Variable De membre Ajouter, cliquez sur **la variable de contrôle**.

1. Dans la boîte de liste **d’identification de contrôle,** sélectionnez l’ID de contrôle du contrôle ActiveX intégré. Par exemple : `IDC_CIRCCTRL1`.

1. Dans la boîte **à noms variables,** entrez un nom.

   Par exemple, *m_circctl*.

1. Cliquez sur **Finition** pour accepter vos choix et sortir de l’Assistant Variable Membre Ajouter.

## <a name="see-also"></a>Voir aussi

[Conteneurs de contrôle ActiveX](../mfc/activex-control-containers.md)
