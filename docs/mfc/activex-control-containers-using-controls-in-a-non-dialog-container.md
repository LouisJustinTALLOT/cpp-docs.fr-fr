---
title: 'Conteneurs de contrôles ActiveX : À l’aide de contrôles dans un conteneur sans boîte de dialogue'
ms.date: 11/04/2016
helpviewer_keywords:
- Create method [MFC], ActiveX controls
- CreateControl method [MFC]
- ActiveX controls [MFC], creating
- ActiveX control containers [MFC], non-dialog containers
- ActiveX control containers [MFC], inserting controls
ms.assetid: 46f195b0-b8ca-4409-8cca-fbfaf2c9ab9f
ms.openlocfilehash: 70a67a6952d5361177b89e3ba514d7036b5799b6
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57284240"
---
# <a name="activex-control-containers-using-controls-in-a-non-dialog-container"></a>Conteneurs de contrôles ActiveX : À l’aide de contrôles dans un conteneur sans boîte de dialogue

Dans certaines applications, telles que SDI ou une application MDI, vous devez incorporer un contrôle dans une fenêtre de l’application. Le **créer** fonction membre de la classe wrapper, insérée par Visual C++, peut créer une instance du contrôle de manière dynamique, sans avoir besoin d’une boîte de dialogue.

Le **créer** fonction membre possède les paramètres suivants :

*lpszWindowName*<br/>
Un pointeur vers le texte à afficher dans la propriété du contrôle Text ou Caption (le cas échéant).

*dwStyle*<br/>
Styles de Windows. Pour obtenir la liste complète, consultez [CWnd::CreateControl](../mfc/reference/cwnd-class.md#createcontrol).

*rect*<br/>
Spécifie la taille et la position du contrôle.

*pParentWnd*<br/>
Spécifie la fenêtre du contrôle parent, généralement un `CDialog`. Il ne doit pas être **NULL**.

*nID*<br/>
Spécifie l’ID de contrôle et peut être utilisé par le conteneur pour faire référence au contrôle.

Un exemple d’utilisation de cette fonction pour créer dynamiquement un contrôle ActiveX serait dans une vue de formulaire d’une application SDI. Vous pouvez ensuite créer une instance du contrôle dans le `WM_CREATE` Gestionnaire de l’application.

Pour cet exemple, `CMyView` est la classe de vue principale, `CCirc` est la classe wrapper et CIRC. H est l’en-tête (. H) du fichier de la classe wrapper.

Implémentation de cette fonctionnalité est un processus en quatre étapes.

### <a name="to-dynamically-create-an-activex-control-in-a-non-dialog-window"></a>Pour créer dynamiquement un contrôle ActiveX dans une fenêtre sans boîte de dialogue

1. Insérez CIRC. H dans CMYVIEW. H, juste avant la `CMyView` définition de classe :

   [!code-cpp[NVC_MFC_AxCont#12](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_1.h)]

1. Ajouter une variable membre (de type `CCirc`) à la section protégée de la `CMyView` située dans CMYVIEW de définition de classe. H :

   [!code-cpp[NVC_MFC_AxCont#13](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_2.h)]
    [!code-cpp[NVC_MFC_AxCont#14](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_3.h)]

1. Ajouter un `WM_CREATE` Gestionnaire de messages pour la classe `CMyView`.

1. Dans la fonction gestionnaire, `CMyView::OnCreate`, effectuez un appel à du contrôle `Create` à l’aide de la fonction le **cela** pointeur en tant que la fenêtre parente :

   [!code-cpp[NVC_MFC_AxCont#15](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_4.cpp)]

1. Regénérez le projet. Un contrôle CERC est créé dynamiquement chaque fois que la vue de l’application est créée.

## <a name="see-also"></a>Voir aussi

[Conteneurs de contrôles ActiveX](../mfc/activex-control-containers.md)
