---
title: FAQ sur la relation contenant-contenu des contrôles ATL
ms.date: 11/04/2016
helpviewer_keywords:
- hosting controls using ATL
- ActiveX control containers [C++], ATL control hosting
- ATL, hosting ActiveX controls
- ActiveX controls [C++], hosting
- controls [ATL]
ms.assetid: d4bdfbe0-82ca-4f2f-bb95-cb89bdcc9b53
ms.openlocfilehash: 693617589f157d352972485396777cec587a5b8f
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352698"
---
# <a name="atl-control-containment-faq"></a>FAQ sur la relation contenant-contenu des contrôles ATL

## <a name="which-atl-classes-facilitate-activex-control-containment"></a>Quelles sont les classes ATL qui facilitent la contenance de contrôles ActiveX ?

Le code d’hébergement de contrôle ATL ne vous oblige pas à utiliser des classes ATL ; vous pouvez simplement créer une fenêtre **« AtlAxWin80 »** et utiliser l’API d’hébergement de contrôle si nécessaire (pour plus d’informations, consultez **qu’est-ce que l’API d’hébergement de contrôle ATL**. Toutefois, les classes suivantes rendent les fonctionnalités de relation contenant-contenu plus faciles à utiliser.

|Classe|Description|
|-----------|-----------------|
|[CAxWindow](../atl/reference/caxwindow-class.md)|Encapsule une fenêtre **« AtlAxWin80 »** , en fournissant des méthodes pour créer la fenêtre, en créant un contrôle et/ou en joignant un contrôle à la fenêtre, et en extrayant des pointeurs d’interface sur l’objet hôte.|
|[CAxWindow2T](../atl/reference/caxwindow2t-class.md)|Encapsule une fenêtre **« AtlAxWinLic80 »** , en fournissant des méthodes pour créer la fenêtre, en créant un contrôle et/ou en joignant un contrôle sous licence à la fenêtre, et en extrayant des pointeurs d’interface sur l’objet hôte.|
|[CComCompositeControl](../atl/reference/ccomcompositecontrol-class.md)|Agit comme une classe de base pour les classes de contrôles ActiveX basées sur une ressource de boîte de dialogue. Ces contrôles peuvent contenir d’autres contrôles ActiveX.|
|[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)|Agit comme une classe de base pour les classes de boîte de dialogue basées sur une ressource de boîte de dialogue. Ces boîtes de dialogue peuvent contenir des contrôles ActiveX.|
|[CWindow](../atl/reference/cwindow-class.md)|Fournit une méthode, [GetDlgControl](../atl/reference/cwindow-class.md#getdlgcontrol), qui retourne un pointeur d’interface sur un contrôle, en fonction de l’ID de sa fenêtre hôte. En outre, les wrappers d’API Windows exposés par simplifient `CWindow` généralement la gestion des fenêtres.|

## <a name="what-is-the-atl-control-hosting-api"></a>Qu’est-ce que l’API d’hébergement de contrôle ATL ?

L’API d’hébergement de contrôle d’ATL est l’ensemble de fonctions qui permet à n’importe quelle fenêtre d’agir comme un conteneur de contrôles ActiveX. Ces fonctions peuvent être liées de manière statique ou dynamique à votre projet, car elles sont disponibles en tant que code source et exposées par ATL90.dll. Les fonctions d’hébergement de contrôle sont répertoriées dans le tableau ci-dessous.

|Fonction|Description|
|--------------|-----------------|
|[AtlAxAttachControl](reference/composite-control-global-functions.md#atlaxattachcontrol)|Crée un objet hôte, le connecte à la fenêtre fournie, puis attache un contrôle existant.|
|[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)|Crée un objet hôte, le connecte à la fenêtre fournie, puis charge un contrôle.|
|[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)|Crée un contrôle ActiveX sous licence, l’initialise et l’héberge dans la fenêtre spécifiée, similaire à [AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol).|
|[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)|Crée un objet hôte, le connecte à la fenêtre fournie, puis charge un contrôle (permet également la configuration de récepteurs d’événements).|
|[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrollicex)|Crée un contrôle ActiveX sous licence, l’initialise et l’héberge dans la fenêtre spécifiée, similaire à [AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic).|
|[AtlAxCreateDialog](reference/composite-control-global-functions.md#atlaxcreatedialog)|Crée une boîte de dialogue non modale à partir d’une ressource de boîte de dialogue et retourne le handle de fenêtre.|
|[AtlAxDialogBox](reference/composite-control-global-functions.md#atlaxdialogbox)|Crée une boîte de dialogue modale à partir d’une ressource de boîte de dialogue.|
|[AtlAxGetControl](reference/composite-control-global-functions.md#atlaxgetcontrol)|Retourne le pointeur d’interface **IUnknown** du contrôle hébergé dans une fenêtre.|
|[AtlAxGetHost](reference/composite-control-global-functions.md#atlaxgethost)|Retourne le pointeur d’interface **IUnknown** de l’objet hôte connecté à une fenêtre.|
|[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)|Initialise le code d’hébergement de contrôle.|
|[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm)|Désinitialise le code d’hébergement de contrôle.|

Les `HWND` paramètres dans les trois premières fonctions doivent être une fenêtre existante de (presque) tout type. Si vous appelez l’une de ces trois fonctions explicitement (en général, vous n’avez pas besoin de), ne transmettez pas de handle à une fenêtre qui joue déjà le rôle d’hôte (dans ce cas, l’objet hôte existant ne sera pas libéré).

Les sept premières fonctions appellent [AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) implicitement.

> [!NOTE]
> L’API d’hébergement de contrôle constitue la base de la prise en charge d’ATL pour la relation contenant-contenu des contrôles ActiveX. Toutefois, il n’est généralement pas nécessaire d’appeler directement ces fonctions si vous tirez parti de l’utilisation des classes wrapper d’ATL ou que vous utilisez pleinement. Pour plus d’informations, consultez [les classes ATL facilitant la relation contenant-contenu des contrôles ActiveX](#which-atl-classes-facilitate-activex-control-containment).

## <a name="what-is-atlaxwin100"></a>Qu’est-ce que AtlAxWin100 ?

`AtlAxWin100` nom d’une classe de fenêtre qui permet de fournir des fonctionnalités d’hébergement de contrôle ATL. Quand vous créez une instance de cette classe, la procédure de fenêtre utilise automatiquement l’API d’hébergement de contrôle pour créer un objet hôte associé à la fenêtre et la charger avec le contrôle que vous spécifiez comme titre de la fenêtre.

## <a name="when-do-i-need-to-call-atlaxwininit"></a>Quand dois-je appeler AtlAxWinInit ?

[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) enregistre la classe de fenêtre **« AtlAxWin80 »** (ainsi que quelques messages de fenêtre personnalisés). par conséquent, cette fonction doit être appelée avant que vous ne tentiez de créer une fenêtre hôte. Toutefois, vous n’avez pas toujours besoin d’appeler cette fonction explicitement, puisque les API d’hébergement (et les classes qui les utilisent) appellent souvent cette fonction pour vous. L’appel de cette fonction n’a aucun effet plus d’une fois.

## <a name="what-is-a-host-object"></a>Qu’est-ce qu’un objet hôte ?

Un objet hôte est un objet COM qui représente le conteneur de contrôles ActiveX fourni par ATL pour une fenêtre particulière. L’objet hôte sous-classe la fenêtre de conteneur pour qu’il puisse refléter les messages du contrôle, il fournit les interfaces de conteneur nécessaires à utiliser par le contrôle, et il expose les interfaces [IAxWinHostWindow](../atl/reference/iaxwinhostwindow-interface.md) et [IAxWinAmbientDispatch](../atl/reference/iaxwinambientdispatch-interface.md) pour vous permettre de configurer l’environnement du contrôle.

Vous pouvez utiliser l’objet hôte pour définir les propriétés ambiantes du conteneur.

## <a name="can-i-host-more-than-one-control-in-a-single-window"></a>Puis-je héberger plusieurs contrôles dans une seule fenêtre ?

Il n’est pas possible d’héberger plusieurs contrôles dans une même fenêtre hôte ATL. Chaque fenêtre hôte est conçue pour contenir exactement un contrôle à la fois (cela permet un mécanisme simple pour gérer la réflexion de message et les propriétés ambiantes par contrôle). Toutefois, si vous souhaitez que l’utilisateur voit plusieurs contrôles dans une même fenêtre, il est simple de créer plusieurs fenêtres hôtes en tant qu’enfants de cette fenêtre.

## <a name="can-i-reuse-a-host-window"></a>Puis-je réutiliser une fenêtre hôte ?

Il n’est pas recommandé de réutiliser les fenêtres hôtes. Pour garantir la robustesse de votre code, vous devez lier la durée de vie de la fenêtre hôte à la durée de vie d’un contrôle unique.

## <a name="when-do-i-need-to-call-atlaxwinterm"></a>Quand dois-je appeler AtlAxWinTerm ?

[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm) annule l’inscription de la classe de fenêtre **« AtlAxWin80 »** . Vous devez appeler cette fonction (si vous n’avez plus besoin de créer des fenêtres hôtes) une fois que toutes les fenêtres hôtes existantes ont été détruites. Si vous n’appelez pas cette fonction, la classe de fenêtre sera désinscrite automatiquement lorsque le processus se terminera.

## <a name="hosting-activex-controls-using-atl-axhost"></a>Hébergement de contrôles ActiveX à l’aide d’ATL AXHost

L’exemple de cette section montre comment créer AXHost et comment héberger un contrôle ActiveX à l’aide de différentes fonctions ATL. Il montre également comment accéder aux événements de contrôle et de récepteur (à l’aide de [IDispEventImpl](../atl/reference/idispeventimpl-class.md)) à partir du contrôle hébergé. L’exemple héberge le contrôle calendrier dans une fenêtre principale ou dans une fenêtre enfant.

Notez la définition du `USE_METHOD` symbole. Vous pouvez modifier la valeur de ce symbole pour qu’elle varie entre 1 et 8. La valeur du symbole détermine la façon dont le contrôle sera créé :

- Pour les valeurs pair-numérotées de `USE_METHOD` , l’appel pour créer l’hôte sous-classe une fenêtre et le convertit en hôte de contrôle. Pour les valeurs impaires, le code crée une fenêtre enfant qui agit en tant qu’hôte.

- Pour les valeurs `USE_METHOD` comprises entre 1 et 4, l’accès au contrôle et au récepteur d’événements s’effectue dans l’appel qui crée également l’hôte. Les valeurs comprises entre 5 et 8 interrogent l’hôte sur les interfaces et raccordent le récepteur.

Voici un résumé :

|USE_METHOD|Hôte|Contrôler l’accès et la réception d’événements|Fonction illustrée|
|-----------------|----------|--------------------------------------|---------------------------|
|1|Fenêtre enfant|Une étape|CreateControlLicEx|
|2|Fenêtre principale|Une étape|AtlAxCreateControlLicEx|
|3|Fenêtre enfant|Une étape|CreateControlEx|
|4|Fenêtre principale|Une étape|AtlAxCreateControlEx|
|5|Fenêtre enfant|Étapes multiples|CreateControlLic|
|6|Fenêtre principale|Étapes multiples|AtlAxCreateControlLic|
|7|Fenêtre enfant|Étapes multiples|CreateControl|
|8|Fenêtre principale|Étapes multiples|AtlAxCreateControl|

[!code-cpp[NVC_ATL_AxHost#1](../atl/codesnippet/cpp/hosting-activex-controls-using-atl-axhost_1.cpp)]

## <a name="see-also"></a>Voir aussi

[FAQ sur la relation contenant-contenu des contrôles](../atl/atl-control-containment-faq.md)<br/>
[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)<br/>
[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)<br/>
[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)<br/>
[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)<br/>
[CAxWindow2T, classe](../atl/reference/caxwindow2t-class.md)<br/>
[Interface IAxWinHostWindowLic](../atl/reference/iaxwinhostwindowlic-interface.md)
