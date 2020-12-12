---
description: 'En savoir plus sur : conteneurs de contrôles ActiveX : connexion d’un contrôle ActiveX à une variable membre'
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
ms.openlocfilehash: c3b890b5705624a18ec42583b143fbd33e4f0608
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97271900"
---
# <a name="activex-control-containers-connecting-an-activex-control-to-a-member-variable"></a>Conteneurs de contrôles ActiveX : association d'un contrôle ActiveX à une variable membre

Le moyen le plus simple d’accéder à un contrôle ActiveX à partir de son application de conteneur de contrôle consiste à associer le contrôle ActiveX à une variable membre de la classe Dialog qui contiendra le contrôle.

> [!NOTE]
> Il ne s’agit pas de la seule façon d’accéder à un contrôle incorporé à partir d’une classe de conteneur, mais dans le cadre de cet article, cela suffit.

### <a name="adding-a-member-variable-to-the-dialog-class"></a>Ajout d’une variable membre à la classe Dialog

1. Dans Affichage de classes, cliquez avec le bouton droit sur la classe principale de la boîte de dialogue pour ouvrir le menu contextuel. Par exemple, `CContainerDlg`.

1. Dans le menu contextuel, cliquez sur **Ajouter** , puis sur **Ajouter une variable**.

1. Dans l’Assistant Ajout de variable membre, cliquez sur **variable de contrôle**.

1. Dans la zone de liste **ID du contrôle** , sélectionnez l’ID de contrôle du contrôle ActiveX incorporé. Par exemple, `IDC_CIRCCTRL1`.

1. Dans la zone nom de la **variable** , entrez un nom.

   Par exemple, *m_circctl*.

1. Cliquez sur **Terminer** pour accepter vos choix et quitter l’Assistant Ajout de variable membre.

## <a name="see-also"></a>Voir aussi

[Conteneurs de contrôles ActiveX](activex-control-containers.md)
