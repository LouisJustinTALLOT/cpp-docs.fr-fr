---
description: 'En savoir plus sur : Assistant contrôle ActiveX MFC'
title: Contrôle ActiveX MFC (Assistant)
ms.date: 09/12/2018
f1_keywords:
- vc.appwiz.mfc.ctl.overview
helpviewer_keywords:
- ActiveX controls [MFC], MFC
- MFC ActiveX controls [MFC], wizards
- OLE controls [MFC], creating
- MFC ActiveX Control Wizard
- OLE controls [MFC]
ms.assetid: f19d698c-bdc3-4c74-af97-3d6ccb441b75
ms.openlocfilehash: f313f2a218c06a20eddbfff33e936109e4be2cf0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97219263"
---
# <a name="mfc-activex-control-wizard"></a>Contrôle ActiveX MFC (Assistant)

Un contrôle ActiveX est un type spécifique de [serveur Automation](../../mfc/automation-servers.md). Il s’agit d’un composant réutilisable. L’application qui héberge le contrôle ActiveX est le [client Automation](../../mfc/automation-clients.md) de ce contrôle. Si votre objectif est de créer un composant réutilisable, utilisez cet Assistant pour créer votre contrôle. Pour plus d’informations, consultez [contrôles ActiveX MFC](../../mfc/mfc-activex-controls.md) .

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour un nouveau développement. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, consultez [contrôles ActiveX](../activex-controls.md).

Vous pouvez également créer une application MFC de serveur Automation à l’aide de l' [Assistant Application MFC](../../mfc/reference/mfc-application-wizard.md).

Un contrôle ActiveX créé avec cet Assistant peut avoir une interface utilisateur, ou il peut être invisible. Vous pouvez indiquer cette option dans la page [paramètres de contrôle](../../mfc/reference/control-settings-mfc-activex-control-wizard.md) de l’Assistant. Un contrôle Timer est un exemple de contrôle ActiveX que vous souhaitez masquer.

Les contrôles ActiveX peuvent avoir une interface utilisateur complexe. Certains contrôles peuvent ressembler à des formulaires encapsulés : un contrôle unique contenant de nombreux champs, chacun un contrôle Windows dans son propre droit. Par exemple, un objet de pièces auto implémentée en tant que contrôle ActiveX MFC peut présenter une interface utilisateur de type formulaire par le biais de laquelle les utilisateurs peuvent lire et modifier le numéro de référence, le nom de la partie et d’autres informations. Pour plus d’informations, consultez [contrôles ActiveX MFC](../../mfc/mfc-activex-controls.md) .

Si vous devez créer un conteneur pour vos objets ActiveX, consultez [créer un conteneur de contrôles ActiveX](../../mfc/reference/creating-an-mfc-activex-control-container.md).

Le programme de démarrage MFC comprend des fichiers sources C++ (. cpp), des fichiers de ressources (. RC) et un fichier projet (. vcxproj). Le code généré dans ces fichiers de démarrage est basé sur MFC.

L’exemple de liste suivant montre les tâches et les types d’améliorations de votre contrôle ActiveX :

- [Optimisation d’un contrôle ActiveX](../../mfc/mfc-activex-controls-optimization.md)

- [Ajout d’événements stock à un contrôle ActiveX](../../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md)

- [Ajout d’événements personnalisés](../../mfc/mfc-activex-controls-adding-custom-events.md)

- [Ajout de méthodes stock](../../mfc/mfc-activex-controls-adding-stock-methods.md)

- [Ajout de méthodes personnalisées](../../mfc/mfc-activex-controls-adding-custom-methods.md)

- [Ajout de propriétés stock](../../mfc/mfc-activex-controls-adding-stock-properties.md)

- [Ajout de propriétés personnalisées](../../mfc/mfc-activex-controls-adding-custom-properties.md)

- [Programmation de contrôles ActiveX dans un conteneur de contrôles ActiveX](../../mfc/programming-activex-controls-in-a-activex-control-container.md)

## <a name="overview"></a>Vue d’ensemble

Cette page de l’Assistant décrit les paramètres d’application actuels pour le projet de contrôle ActiveX MFC que vous créez. Par défaut, l’Assistant crée un projet comme suit :

- Le projet par défaut ne génère aucune licence d’exécution ni aucun fichier d’aide. Vous pouvez modifier ces paramètres par défaut dans la page Paramètres de l' [application](../../mfc/reference/application-settings-mfc-activex-control-wizard.md) . Seules les sélections que vous effectuez sur cette page de l’Assistant contrôle ActiveX sont reflétées dans la page **vue d’ensemble** .

- Le projet comprend une classe de contrôle et une classe de page de propriétés, en fonction du nom du projet. Vous pouvez modifier les noms de votre projet et des noms de fichiers dans la page [noms du contrôle](../../mfc/reference/control-names-mfc-activex-control-wizard.md) .

- Le contrôle est basé sur aucun contrôle Windows existant, est activé lorsqu’il devient visible, possède une interface utilisateur et inclut une boîte de dialogue **à propos** de. Vous pouvez modifier ces paramètres par défaut dans la page [paramètres du contrôle](../../mfc/reference/control-settings-mfc-activex-control-wizard.md) .

## <a name="see-also"></a>Voir aussi

[Projets Visual Studio-C++](../../build/creating-and-managing-visual-cpp-projects.md)<br/>
[Types de projets C++ dans Visual Studio](../../build/reference/visual-cpp-project-types.md)<br/>
[Concepts](../../atl/active-template-library-atl-concepts.md)
