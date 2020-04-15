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
ms.openlocfilehash: 36ff3381447b46b28908522d65be9f34fe23addf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317400"
---
# <a name="atl-control-containment-faq"></a>FAQ sur la relation contenant-contenu des contrôles ATL

## <a name="which-atl-classes-facilitate-activex-control-containment"></a>Quelles sont les classes ATL qui facilitent la contenance de contrôles ActiveX ?

Le code d’hébergement de contrôle d’ATL ne vous oblige pas à utiliser des cours ATL ; vous pouvez simplement créer une fenêtre **"AtlAxWin80"** et utiliser l’API d’hébergement de contrôle si nécessaire (pour plus d’informations, voir **Qu’est l’API DE contrôle ATL-Hébergement**. Cependant, les classes suivantes facilitent l’utilisation des caractéristiques de confinement.

|Classe|Description|
|-----------|-----------------|
|[CAxWindow](../atl/reference/caxwindow-class.md)|Enveloppe une fenêtre **"AtlAxWin80",** fournissant des méthodes pour créer la fenêtre, créer un contrôle et/ ou attacher un contrôle à la fenêtre, et récupérer des indications d’interface sur l’objet hôte.|
|[CAxWindow2T](../atl/reference/caxwindow2t-class.md)|Enveloppe une fenêtre **"AtlAxWinLic80",** fournissant des méthodes pour créer la fenêtre, créer un contrôle et/ ou attacher un contrôle sous licence à la fenêtre, et récupérer des indications d’interface sur l’objet hôte.|
|[CComCompositeControl](../atl/reference/ccomcompositecontrol-class.md)|Agit comme une classe de base pour les classes de contrôle ActiveX basée sur une ressource de dialogue. Ces contrôles peuvent contenir d’autres contrôles ActiveX.|
|[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)|Agit comme une classe de base pour les classes de dialogue basée sur une ressource de dialogue. Ces dialogues peuvent contenir des contrôles ActiveX.|
|[CWindow (en)](../atl/reference/cwindow-class.md)|Fournit une méthode, [GetDlgControl](../atl/reference/cwindow-class.md#getdlgcontrol), qui retournera un pointeur d’interface sur un contrôle, étant donné l’ID de sa fenêtre hôte. En outre, les emballages Windows `CWindow` API exposés par généralement rendre la gestion des fenêtres plus facile.|

## <a name="what-is-the-atl-control-hosting-api"></a>Qu’est-ce que l’API d’hébergement de contrôle ATL ?

L’API d’hébergement de contrôle d’ATL est l’ensemble de fonctions qui permet à n’importe quelle fenêtre d’agir comme un conteneur de contrôle ActiveX. Ces fonctions peuvent être statiques ou dynamiquement liées à votre projet car elles sont disponibles sous forme de code source et exposées par ATL90.dll. Les fonctions d’hébergement de contrôle sont répertoriées dans le tableau ci-dessous.

|Fonction|Description|
|--------------|-----------------|
|[AtlAxAttachControl](reference/composite-control-global-functions.md#atlaxattachcontrol)|Crée un objet hôte, le connecte à la fenêtre fournie, puis attache un contrôle existant.|
|[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)|Crée un objet hôte, le connecte à la fenêtre fournie, puis charge un contrôle.|
|[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)|Crée un contrôle ActiveX sous licence, l’initialise et l’héberge dans la fenêtre spécifiée, similaire à [AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol).|
|[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)|Crée un objet hôte, le connecte à la fenêtre fournie, puis charge un contrôle (permet également de configurer les éviers d’événements).|
|[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrollicex)|Crée un contrôle ActiveX sous licence, l’initialise et l’héberge dans la fenêtre spécifiée, similaire à [AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic).|
|[AtlAxCreateDialog](reference/composite-control-global-functions.md#atlaxcreatedialog)|Crée une boîte de dialogue sans mode à partir d’une ressource de dialogue et renvoie la poignée de fenêtre.|
|[AtlAxDialogBox](reference/composite-control-global-functions.md#atlaxdialogbox)|Crée une boîte de dialogue modal à partir d’une ressource de dialogue.|
|[AtlAxGetControl](reference/composite-control-global-functions.md#atlaxgetcontrol)|Retourne le pointeur **d’interface IUnknown** du contrôle hébergé dans une fenêtre.|
|[AtlAxGetHost](reference/composite-control-global-functions.md#atlaxgethost)|Retourne le pointeur **d’interface IUnknown** de l’objet hôte connecté à une fenêtre.|
|[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)|Initialise le code d’hébergement de contrôle.|
|[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm)|Uninitialise le code d’hébergement de contrôle.|

Les `HWND` paramètres des trois premières fonctions doivent être une fenêtre existante de (presque) n’importe quel type. Si vous appelez explicitement l’une de ces trois fonctions (généralement, vous n’aurez pas à le faire), ne passez pas une poignée à une fenêtre qui agit déjà en tant qu’hôte (si vous le faites, l’objet hôte existant ne sera pas libéré).

Les sept premières fonctions appellent [implicitement AtlAxWinInit.](reference/composite-control-global-functions.md#atlaxwininit)

> [!NOTE]
> L’API d’hébergement de contrôle constitue la base du support d’ATL pour le confinement de contrôle ActiveX. Cependant, il est généralement peu nécessaire d’appeler ces fonctions directement si vous profitez ou faites pleinement usage des classes d’emballage d’ATL. Pour plus d’informations, voir [quelles classes ATL facilitent le confinement de contrôle ActiveX](which-atl-classes-facilitate-activex-control-containment-q.md).

## <a name="what-is-atlaxwin100"></a>Qu’est-ce que AtlAxWin100 ?

`AtlAxWin100`est le nom d’une classe de fenêtre qui aide à fournir la fonctionnalité d’hébergement de contrôle d’ATL. Lorsque vous créez une instance de cette classe, la procédure de fenêtre utilise automatiquement l’API d’hébergement de contrôle pour créer un objet hôte associé à la fenêtre et le charger avec le contrôle que vous spécifiez comme titre de la fenêtre.

## <a name="when-do-i-need-to-call-atlaxwininit"></a>Quand dois-je appeler AtlAxWinInit ?

[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) enregistre la classe de fenêtre **"AtlAxWin80"** (plus un couple de messages de fenêtre personnalisés) de sorte que cette fonction doit être appelée avant d’essayer de créer une fenêtre hôte. Cependant, vous n’avez pas toujours besoin d’appeler cette fonction explicitement, puisque les API d’hébergement (et les classes qui les utilisent) appellent souvent cette fonction pour vous. Il n’y a aucun mal à appeler cette fonction plus d’une fois.

## <a name="what-is-a-host-object"></a>Qu’est-ce qu’un objet hôte ?

Un objet hôte est un objet COM qui représente le conteneur de commande ActiveX fourni par ATL pour une fenêtre particulière. L’objet hôte sous-classe la fenêtre du conteneur afin qu’il puisse refléter les messages au contrôle, il fournit les interfaces de conteneurs nécessaires pour être utilisé par le contrôle, et il expose les interfaces [IAxWinHostWindow](../atl/reference/iaxwinhostwindow-interface.md) et [IAxWinAmbientDispatch](../atl/reference/iaxwinambientdispatch-interface.md) pour vous permettre de configurer l’environnement du contrôle.

Vous pouvez utiliser l’objet hôte pour définir les propriétés ambiantes du conteneur.

## <a name="can-i-host-more-than-one-control-in-a-single-window"></a>Puis-je héberger plusieurs contrôles dans une seule fenêtre ?

Il n’est pas possible d’héberger plus d’un contrôle dans une seule fenêtre d’hôte ATL. Chaque fenêtre d’hôte est conçue pour contenir exactement un contrôle à la fois (ce qui permet un mécanisme simple pour la manipulation de la réflexion des messages et des propriétés ambiantes par contrôle). Cependant, si vous avez besoin de l’utilisateur pour voir plusieurs contrôles dans une seule fenêtre, c’est une question simple de créer plusieurs fenêtres hôtes comme enfants de cette fenêtre.

## <a name="can-i-reuse-a-host-window"></a>Puis-je réutiliser une fenêtre hôte ?

Il n’est pas recommandé de réutiliser les fenêtres d’hôtes. Pour assurer la robustesse de votre code, vous devez lier la durée de vie de votre fenêtre d’hôte à la durée de vie d’un seul contrôle.

## <a name="when-do-i-need-to-call-atlaxwinterm"></a>Quand dois-je appeler AtlAxWinTerm ?

[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm) désinscrit la classe de fenêtre **"AtlAxWin80".** Vous devez appeler cette fonction (si vous n’avez plus besoin de créer des fenêtres d’hôte) après que toutes les fenêtres d’hôtes existantes ont été détruites. Si vous n’appelez pas cette fonction, la classe de fenêtre ne sera pas enregistrée automatiquement lorsque le processus prendra fin.

## <a name="hosting-activex-controls-using-atl-axhost"></a>Hébergement de contrôles ActiveX à l’aide d’ATL AXHost

L’échantillon de cette section montre comment créer AXHost et comment héberger un contrôle ActiveX en utilisant diverses fonctions ATL. Il montre également comment accéder aux événements de contrôle et d’évier (en utilisant [IDispEventImpl](../atl/reference/idispeventimpl-class.md)) à partir du contrôle qui est hébergé. L’échantillon héberge le contrôle du calendrier dans une fenêtre principale ou dans une fenêtre enfant.

Remarquez la `USE_METHOD` définition du symbole. Vous pouvez modifier la valeur de ce symbole pour varier entre 1 et 8. La valeur du symbole détermine la façon dont le contrôle sera créé :

- Pour les `USE_METHOD`valeurs numérotées de , l’appel pour créer l’hôte sous-classe une fenêtre et la convertit en hôte de contrôle. Pour les valeurs impaires, le code crée une fenêtre pour enfants qui agit comme un hôte.

- Pour les `USE_METHOD` valeurs comprises entre 1 et 4, l’accès au contrôle et au naufrage des événements sont accomplis dans l’appel qui crée également l’hôte. Valeurs entre 5 et 8 requête de l’hôte pour les interfaces et crocheter l’évier.

Voici un résumé :

|USE_METHOD|Host|Contrôlez l’accès et le naufrage d’événements|Fonction démontrée|
|-----------------|----------|--------------------------------------|---------------------------|
|1|Fenêtre d’enfant|Une étape|CreateControlLicEx|
|2|Fenêtre principale|Une étape|AtlAxCreateControlLicEx|
|3|Fenêtre d’enfant|Une étape|CreateControlEx|
|4|Fenêtre principale|Une étape|AtlAxCreateControlEx|
|5|Fenêtre d’enfant|Étapes multiples|CreateControlLic|
|6|Fenêtre principale|Étapes multiples|AtlAxCreateControlLic|
|7|Fenêtre d’enfant|Étapes multiples|CreateControl|
|8|Fenêtre principale|Étapes multiples|AtlAxCreateControl|

[!code-cpp[NVC_ATL_AxHost#1](../atl/codesnippet/cpp/hosting-activex-controls-using-atl-axhost_1.cpp)]

## <a name="see-also"></a>Voir aussi

[FAQ sur la relation contenant-contenu des contrôles](../atl/atl-control-containment-faq.md)<br/>
[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)<br/>
[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)<br/>
[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)<br/>
[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)<br/>
[Classe CAxWindow2T](../atl/reference/caxwindow2t-class.md)<br/>
[IAxWinHostWindowLic Interface](../atl/reference/iaxwinhostwindowlic-interface.md)
