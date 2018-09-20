---
title: Assistant contrôle ActiveX MFC | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.ctl.overview
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [MFC], MFC
- MFC ActiveX controls [MFC], wizards
- OLE controls [MFC], creating
- MFC ActiveX Control Wizard
- OLE controls [MFC]
ms.assetid: f19d698c-bdc3-4c74-af97-3d6ccb441b75
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ccf2da630c72962ee3e74badc250de5cce5f14e2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46407151"
---
# <a name="mfc-activex-control-wizard"></a>Contrôle ActiveX MFC (Assistant)

Un contrôle ActiveX est un type spécifique de [serveur automation](../../mfc/automation-servers.md); c’est un composant réutilisable. L’application qui héberge le contrôle ActiveX est le [client automation](../../mfc/automation-clients.md) de ce contrôle. Si votre objectif est de créer un tel composant réutilisable, utilisez ensuite cet Assistant pour créer votre contrôle. Consultez [contrôles ActiveX MFC](../../mfc/mfc-activex-controls.md) pour plus d’informations.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour tout nouveau développement. Pour plus d’informations sur les technologies modernes qui remplacent les ActiveX, consultez [contrôles ActiveX](../activex-controls.md).

Vous pouvez également créer une automatisation serveur MFC application à l’aide de la [Assistant Application MFC](../../mfc/reference/mfc-application-wizard.md).

Un contrôle ActiveX créé avec cet Assistant peut avoir une interface utilisateur, ou il peut être invisible. Vous pouvez indiquer cette option dans le [paramètres de contrôle](../../mfc/reference/control-settings-mfc-activex-control-wizard.md) page dans l’Assistant. Un contrôle timer est un exemple d’un contrôle ActiveX que vous souhaitez être invisible.

Contrôles ActiveX peuvent avoir une interface utilisateur complexe. Certains contrôles peuvent être telle que des formulaires encapsulés : un seul contrôle contenant de nombreux champs, chacun un contrôle Windows à part entière. Par exemple, un objet de parties automatique implémenté comme un contrôle ActiveX MFC peut présenter une interface utilisateur de type formulaire par le biais duquel les utilisateurs pouvaient lire et modifier le numéro de référence, nom de partie et d’autres informations. Consultez [contrôles ActiveX MFC](../../mfc/mfc-activex-controls.md) pour plus d’informations.

Si vous avez besoin créer un conteneur pour vos objets ActiveX, consultez [créer un conteneur de contrôles ActiveX](../../mfc/reference/creating-an-mfc-activex-control-container.md).

Le programme de démarrage MFC inclut des fichiers sources (.cpp) C++, les fichiers de ressources (.rc) et un fichier projet (.vcxproj). Le code généré dans ces fichiers de démarrage est basé sur la bibliothèque MFC.

L’exemple de liste suivante affiche les tâches et les types d’améliorations pour votre contrôle ActiveX :

- [Optimisation d’un contrôle ActiveX](../../mfc/mfc-activex-controls-optimization.md)

- [Ajout d’événements Stock à un contrôle ActiveX](../../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md)

- [Ajout d’événements personnalisés](../../mfc/mfc-activex-controls-adding-custom-events.md)

- [Ajout de méthodes Stock](../../mfc/mfc-activex-controls-adding-stock-methods.md)

- [Ajout de méthodes personnalisées](../../mfc/mfc-activex-controls-adding-custom-methods.md)

- [Ajout de propriétés Stock](../../mfc/mfc-activex-controls-adding-stock-properties.md)

- [Ajout de propriétés personnalisées](../../mfc/mfc-activex-controls-adding-custom-properties.md)

- [Programmation de contrôles ActiveX dans un conteneur de contrôles ActiveX](../../mfc/programming-activex-controls-in-a-activex-control-container.md)

## <a name="overview"></a>Vue d'ensemble

Cette page de l’Assistant décrit les paramètres de l’application pour le projet de contrôle ActiveX MFC que vous créez. Par défaut, l’Assistant crée un projet comme suit :

- Le projet par défaut ne génère aucun fichier de licence ou à l’aide du moment de l’exécution. Vous pouvez modifier ces paramètres par défaut sur le [paramètres d’Application](../../mfc/reference/application-settings-mfc-activex-control-wizard.md) page. Seules les sélections effectuées dans cette page de l’Assistant contrôle ActiveX sont répercutées le **vue d’ensemble** page.

- Le projet inclut une classe de contrôle et une classe de page de propriétés, en fonction du nom du projet. Vous pouvez modifier les noms de vos noms de projet et le fichier sur le [les noms de contrôle](../../mfc/reference/control-names-mfc-activex-control-wizard.md) page.

- Le contrôle est basé sur aucun contrôle Windows existant, est activé lorsqu’il devienne visible, possède une interface utilisateur et inclut un **sur** boîte de dialogue. Vous pouvez modifier ces paramètres par défaut sur le [paramètres de contrôle](../../mfc/reference/control-settings-mfc-activex-control-wizard.md) page.

## <a name="see-also"></a>Voir aussi

[Création et gestion de projets Visual C++](../../ide/creating-and-managing-visual-cpp-projects.md)<br/>
[Types de projets Visual C++](../../ide/visual-cpp-project-types.md)<br/>
[Concepts](../../atl/active-template-library-atl-concepts.md)

