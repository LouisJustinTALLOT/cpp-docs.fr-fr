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
ms.openlocfilehash: 87cb560a1054a912a4e8574cfe2dee74d5e61fe6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625129"
---
# <a name="activex-control-containers-connecting-an-activex-control-to-a-member-variable"></a>Conteneurs de contrôles ActiveX : association d'un contrôle ActiveX à une variable membre

Le moyen le plus simple d’accéder à un contrôle ActiveX à partir de son application de conteneur de contrôle consiste à associer le contrôle ActiveX à une variable membre de la classe Dialog qui contiendra le contrôle.

> [!NOTE]
> Il ne s’agit pas de la seule façon d’accéder à un contrôle incorporé à partir d’une classe de conteneur, mais dans le cadre de cet article, cela suffit.

### <a name="adding-a-member-variable-to-the-dialog-class"></a>Ajout d’une variable membre à la classe Dialog

1. Dans Affichage de classes, cliquez avec le bouton droit sur la classe principale de la boîte de dialogue pour ouvrir le menu contextuel. Par exemple : `CContainerDlg`.

1. Dans le menu contextuel, cliquez sur **Ajouter** , puis sur **Ajouter une variable**.

1. Dans l’Assistant Ajout de variable membre, cliquez sur **variable de contrôle**.

1. Dans la zone de liste **ID du contrôle** , sélectionnez l’ID de contrôle du contrôle ActiveX incorporé. Par exemple : `IDC_CIRCCTRL1`.

1. Dans la zone nom de la **variable** , entrez un nom.

   Par exemple, *m_circctl*.

1. Cliquez sur **Terminer** pour accepter vos choix et quitter l’Assistant Ajout de variable membre.

## <a name="see-also"></a>Voir aussi

[Conteneurs de contrôles ActiveX](activex-control-containers.md)
