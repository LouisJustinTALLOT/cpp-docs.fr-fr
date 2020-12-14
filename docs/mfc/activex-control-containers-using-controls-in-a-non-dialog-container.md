---
description: 'En savoir plus sur : conteneurs de contrôles ActiveX : utilisation de contrôles dans un conteneur sans boîte de dialogue'
title: 'Conteneurs de contrôles ActiveX : utilisation de contrôles dans un conteneur autre que de boîte de dialogue'
ms.date: 11/04/2016
helpviewer_keywords:
- Create method [MFC], ActiveX controls
- CreateControl method [MFC]
- ActiveX controls [MFC], creating
- ActiveX control containers [MFC], non-dialog containers
- ActiveX control containers [MFC], inserting controls
ms.assetid: 46f195b0-b8ca-4409-8cca-fbfaf2c9ab9f
ms.openlocfilehash: 699f1faa5c88eb965a320c210de6e5e6c2ee94ef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97197671"
---
# <a name="activex-control-containers-using-controls-in-a-non-dialog-container"></a>Conteneurs de contrôles ActiveX : utilisation de contrôles dans un conteneur autre que de boîte de dialogue

Dans certaines applications, telles qu’une application SDI ou MDI, vous pouvez incorporer un contrôle dans une fenêtre de l’application. La fonction membre **Create** de la classe wrapper, insérée par Visual C++, peut créer une instance du contrôle de manière dynamique, sans avoir besoin d’une boîte de dialogue.

La fonction membre **Create** a les paramètres suivants :

*lpszWindowName*<br/>
Pointeur vers le texte à afficher dans la propriété Text ou Caption du contrôle (le cas échéant).

*dwStyle*<br/>
Styles Windows. Pour obtenir une liste complète, consultez [CWnd :: CreateControl](reference/cwnd-class.md#createcontrol).

*rectangulaire*<br/>
Spécifie la taille et la position du contrôle.

*pParentWnd*<br/>
Spécifie la fenêtre parente du contrôle, généralement `CDialog` . Il ne doit pas être **null**.

*nID*<br/>
Spécifie l’ID de contrôle et peut être utilisé par le conteneur pour faire référence au contrôle.

Un exemple d’utilisation de cette fonction pour créer dynamiquement un contrôle ActiveX serait dans une vue de formulaire d’une application SDI. Vous pouvez ensuite créer une instance du contrôle dans le `WM_CREATE` Gestionnaire de l’application.

Pour cet exemple, `CMyView` est la classe d’affichage principale, `CCirc` est la classe wrapper et CIRC. H est l’en-tête (. H) de la classe wrapper.

L’implémentation de cette fonctionnalité est un processus en quatre étapes.

### <a name="to-dynamically-create-an-activex-control-in-a-non-dialog-window"></a>Pour créer dynamiquement un contrôle ActiveX dans une fenêtre qui n’est pas une boîte de dialogue

1. Insérez CIRC. H dans CMYVIEW. H, juste avant la `CMyView` définition de classe :

   [!code-cpp[NVC_MFC_AxCont#12](codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_1.h)]

1. Ajoutez une variable membre (de type `CCirc` ) à la section protégée de la `CMyView` définition de classe située dans CMyView. Manutention

   [!code-cpp[NVC_MFC_AxCont#13](codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_2.h)]
    [!code-cpp[NVC_MFC_AxCont#14](codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_3.h)]

1. Ajoutez un `WM_CREATE` Gestionnaire de messages à la classe `CMyView` .

1. Dans la fonction gestionnaire, `CMyView::OnCreate` , effectuez un appel à la fonction du contrôle `Create` à l’aide du **`this`** pointeur en tant que fenêtre parente :

   [!code-cpp[NVC_MFC_AxCont#15](codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_4.cpp)]

1. Regénérez le projet. Un contrôle CIRC est créé dynamiquement chaque fois que la vue de l’application est créée.

## <a name="see-also"></a>Voir aussi

[Conteneurs de contrôles ActiveX](activex-control-containers.md)
