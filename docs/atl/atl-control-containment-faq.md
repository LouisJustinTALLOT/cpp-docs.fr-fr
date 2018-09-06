---
title: Forum aux questions sur la contenance de contrôles ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- hosting controls using ATL
- ActiveX control containers [C++], ATL control hosting
- ATL, hosting ActiveX controls
- ActiveX controls [C++], hosting
- controls [ATL]
ms.assetid: d4bdfbe0-82ca-4f2f-bb95-cb89bdcc9b53
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ed30097e54460b66ee9bf76293217b8fcc7656a3
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43766706"
---
# <a name="atl-control-containment-faq"></a>FAQ sur la relation contenant-contenu des contrôles ATL

## <a name="which-atl-classes-facilitate-activex-control-containment"></a>Les Classes ATL qui facilitent la contenance de contrôles ActiveX ?

Le code d’hébergement des contrôles ATL ne vous oblige à utiliser les classes ATL ; Vous pouvez simplement créer un **« AtlAxWin80 »** fenêtre et utilisez l’API d’hébergement de contrôle si nécessaire (pour plus d’informations, consultez **quel est l’API hébergeant des contrôles ATL**. Toutefois, les classes suivantes rendent les fonctionnalités de relation contenant-contenu plus facile à utiliser.

|Classe|Description|
|-----------|-----------------|
|[Objet CAxWindow](../atl/reference/caxwindow-class.md)|Encapsule une **« AtlAxWin80 »** fenêtre, en fournissant des méthodes pour la création de la fenêtre, création d’un contrôle et/ou attacher un contrôle à la fenêtre et récupération des pointeurs d’interface sur l’objet hôte.|
|[CAxWindow2T](../atl/reference/caxwindow2t-class.md)|Encapsule une **« AtlAxWinLic80 »** fenêtre, en fournissant des méthodes pour la création de la fenêtre, création d’un contrôle et/ou attacher un contrôle sous licence à la fenêtre et récupération des pointeurs d’interface sur l’objet hôte.|
|[CComCompositeControl](../atl/reference/ccomcompositecontrol-class.md)|Agit comme une classe de base pour les classes de contrôle ActiveX basées sur une ressource de boîte de dialogue. Ces contrôles peuvent contenir d’autres contrôles ActiveX.|
|[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)|Agit comme une classe de base pour les classes de boîte de dialogue basées sur une ressource de boîte de dialogue. Ces boîtes de dialogue peuvent contenir des contrôles ActiveX.|
|[CWindow](../atl/reference/cwindow-class.md)|Fournit une méthode, [GetDlgControl](../atl/reference/cwindow-class.md#getdlgcontrol), qui retourne un pointeur d’interface sur un contrôle, en donnant l’ID de sa fenêtre hôte. En outre, les wrappers Windows API exposées par `CWindow` généralement faciliter la gestion des fenêtres.|  

## <a name="what-is-the-atl-control-hosting-api"></a>Quelle est la bibliothèque ATL API d’hébergement de contrôle ?

ATL qui héberge le contrôle de l’API est l’ensemble de fonctions qui permet de n’importe quelle fenêtre d’agir comme un conteneur de contrôles ActiveX. Ces fonctions peuvent être statiquement ou dynamiquement liées dans votre projet dans la mesure où ils sont disponibles sous forme de code source et exposées par ATL90.dll. Les fonctions de contrôle d’hébergement sont répertoriées dans le tableau ci-dessous.

|Fonction|Description|
|--------------|-----------------|
|[AtlAxAttachControl](reference/composite-control-global-functions.md#atlaxattachcontrol)|Crée un objet hôte, se connecte à la fenêtre fournie, puis attache un contrôle existant.|
|[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)|Crée un objet hôte, se connecte à la fenêtre fournie, puis charge un contrôle.|
|[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)|Crée un contrôle ActiveX sous licence, il initialise et héberge ce dernier dans la fenêtre spécifiée, similaire à [AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol).|
|[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)|Crée un objet hôte, se connecte à la fenêtre fournie, puis charge un contrôle (permet également de configurer des récepteurs d’événements).|
|[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrollicex)|Crée un contrôle ActiveX sous licence, il initialise et héberge ce dernier dans la fenêtre spécifiée, similaire à [AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic).|
|[API AtlAxCreateDialog](reference/composite-control-global-functions.md#atlaxcreatedialog)|Crée une boîte de dialogue non modale à partir d’une ressource de boîte de dialogue et retourne le handle de fenêtre.|
|[AtlAxDialogBox](reference/composite-control-global-functions.md#atlaxdialogbox)|Crée une boîte de dialogue modale à partir d’une ressource de boîte de dialogue.|
|[AtlAxGetControl](reference/composite-control-global-functions.md#atlaxgetcontrol)|Retourne le **IUnknown** pointeur d’interface du contrôle hébergé dans une fenêtre.|
|[AtlAxGetHost](reference/composite-control-global-functions.md#atlaxgethost)|Retourne le **IUnknown** pointeur d’interface de l’objet hôte connecté à une fenêtre.|
|[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)|Initialise le code d’hébergement du contrôle.|
|[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm)|N’initialise pas le code d’hébergement du contrôle.|

Le `HWND` paramètres dans les trois premières fonctions doivent être une fenêtre existante de (quasiment) tout type. Si vous appelez une de ces trois fonctions explicitement (en règle générale, vous ne devrez pas), ne passez pas un handle de fenêtre qui fait déjà Office en tant qu’hôte (si vous le faites, l’objet hôte existant ne serait pas libéré).

Les sept premières fonctions appellent [AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) implicitement.

> [!NOTE]
>  L’API d’hébergement de contrôle constitue la Fondation de prise en charge d’ATL pour les contrôles ActiveX. Toutefois, il est généralement pas nécessaire d’appeler ces fonctions directement si vous tirez parti d’ou Tirez pleinement parti des classes wrapper d’ATL. Pour plus d’informations, consultez [qui ATL Classes faciliter la contenance de contrôles ActiveX](which-atl-classes-facilitate-activex-control-containment-q.md).  

## <a name="what-is-atlaxwin100"></a>Qu’est AtlAxWin100 ?

`AtlAxWin100` est le nom d’une classe de fenêtre qui permet de fournir des fonctionnalités d’hébergement de contrôle d’ATL. Lorsque vous créez une instance de cette classe, la procédure de fenêtre utilisera automatiquement l’API d’hébergement de contrôles pour créer un objet hôte associé à la fenêtre et le charger avec le contrôle que vous spécifiez comme titre de la fenêtre. 

## <a name="when-do-i-need-to-call-atlaxwininit"></a>Quand dois-je appeler AtlAxWinInit ?

[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) inscrit le **« AtlAxWin80 »** classe de fenêtre (ainsi que de quelques messages de fenêtre personnalisés) pour cette fonction doit être appelée avant d’essayer de créer une fenêtre hôte. Toutefois, vous ne devez toujours appeler cette fonction explicitement, depuis l’API hôtes (et les classes qui les utilisent) appellent souvent cette fonction pour vous. Il n’existe aucun risque à appeler cette fonction plusieurs fois.

## <a name="what-is-a-host-object"></a>Qu’est un objet hôte ?

Un objet hôte est un objet COM qui représente le conteneur de contrôle ActiveX fourni par ATL pour une fenêtre particulière. L’objet hôte sous-classe la fenêtre du conteneur afin qu’il peut refléter des messages au contrôle, il fournit les interfaces de conteneur nécessaires pour être utilisé par le contrôle, et il expose les [interface IAxWinHostWindow](../atl/reference/iaxwinhostwindow-interface.md) et [ IAxWinAmbientDispatch](../atl/reference/iaxwinambientdispatch-interface.md) interfaces vous permet de configurer l’environnement du contrôle.

Vous pouvez utiliser l’objet hôte pour définir les propriétés ambiantes du conteneur.

## <a name="can-i-host-more-than-one-control-in-a-single-window"></a>Puis-je héberger plusieurs contrôles dans une seule fenêtre ?

Il n’est pas possible d’héberger plusieurs contrôles dans une seule fenêtre hôte ATL. Chaque fenêtre hôte est conçu pour contenir exactement un contrôle à la fois (ainsi, un mécanisme simple pour la gestion des propriétés ambiantes message réflexion et par contrôle). Toutefois, si vous avez besoin de l’utilisateur de voir plusieurs contrôles dans une fenêtre unique, il est très simple de créer plusieurs fenêtres de l’hôte en tant qu’enfants de cette fenêtre.

## <a name="can-i-reuse-a-host-window"></a>Puis-je réutiliser une fenêtre hôte ?

Il est déconseillé de réutiliser les fenêtres hôtes. Pour garantir la robustesse de votre code, vous devez lier la durée de vie de votre fenêtre hôte pour la durée de vie d’un contrôle unique.

## <a name="when-do-i-need-to-call-atlaxwinterm"></a>Quand dois-je appeler AtlAxWinTerm ?

[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm) annule l’inscription de le **« AtlAxWin80 »** classe de fenêtre. Vous devez appeler cette fonction (si vous n’avez plus besoin créer des fenêtres de l’hôte) une fois que toutes les fenêtres d’hôte existantes ont été détruits. Si vous n’appelez pas cette fonction, la classe de fenêtre sera annulée automatiquement lorsque le processus se termine.

## <a name="hosting-activex-controls-using-atl-axhost"></a>Hébergement de contrôles ActiveX à l’aide d’ATL AXHost

Dans cette section montre comment créer AXHost et comment héberger un contrôle ActiveX à l’aide de différentes fonctions ATL. Il montre également comment accéder aux événements de contrôle et le récepteur (à l’aide de [IDispEventImpl](../atl/reference/idispeventimpl-class.md)) à partir du contrôle hébergé. L’exemple héberge le contrôle calendrier dans une fenêtre principale ou dans une fenêtre enfant.

Notez que la définition de la `USE_METHOD` symbole. Vous pouvez modifier la valeur de ce symbole pour faire varier entre 1 et 8. La valeur du symbole détermine comment le contrôle sera créé :

- Pour les paires de valeurs de `USE_METHOD`, l’appel pour créer l’hôte sous-classe une fenêtre et le convertit en un hôte de contrôle. Pour les valeurs impaires, le code crée une fenêtre enfant qui agit en tant qu’hôte.

- Pour les valeurs de `USE_METHOD` entre 1 et 4, l’accès au contrôle et la réception des événements sont réalisées dans l’appel qui crée également l’hôte. Valeurs comprises entre 5 et 8 interrogent l’hôte pour les interfaces et la raccordent le récepteur.

Voici un résumé :

|USE_METHOD|Hôte|Contrôler l’accès et la réception d’événements|Fonction démontrée|
|-----------------|----------|--------------------------------------|---------------------------|
|1|Fenêtre enfant|Une seule étape|CreateControlLicEx|
|2|Fenêtre principale|Une seule étape|AtlAxCreateControlLicEx|
|3|Fenêtre enfant|Une seule étape|CreateControlEx|
|4|Fenêtre principale|Une seule étape|AtlAxCreateControlEx|
|5|Fenêtre enfant|Plusieurs étapes|CreateControlLic|
|6|Fenêtre principale|Plusieurs étapes|AtlAxCreateControlLic|
|7|Fenêtre enfant|Plusieurs étapes|CreateControl|
|8|Fenêtre principale|Plusieurs étapes|AtlAxCreateControl|

[!code-cpp[NVC_ATL_AxHost#1](../atl/codesnippet/cpp/hosting-activex-controls-using-atl-axhost_1.cpp)]

## <a name="see-also"></a>Voir aussi

[Forum aux questions sur la contenance de contrôles](../atl/atl-control-containment-faq.md)   
[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)   
[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)   
[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)   
[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)   
[CAxWindow2T classe](../atl/reference/caxwindow2t-class.md)   
[IAxWinHostWindowLic, interface](../atl/reference/iaxwinhostwindowlic-interface.md)