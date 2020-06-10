---
title: Conteneurs de contrôles ActiveX
ms.date: 09/12/2018
helpviewer_keywords:
- ActiveX control containers [MFC]
- OLE controls [MFC], containers
ms.assetid: 0eb1a713-e607-4c79-a0c7-67c5f1fd5fab
ms.openlocfilehash: 42fa18c41ebd960aa8de080df00556ad5c909d40
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620754"
---
# <a name="activex-control-containers"></a>Conteneurs de contrôles ActiveX

Un conteneur de contrôle ActiveX est un conteneur qui prend entièrement en charge les contrôles ActiveX et peut les incorporer dans ses propres fenêtres ou boîtes de dialogue. Un contrôle ActiveX est un composant logiciel réutilisable que vous pouvez utiliser dans les projets de développement. Les contrôles permettent à l'utilisateur de votre application d'accéder à des bases de données, de surveiller des données et d'effectuer des sélections dans vos applications. Pour plus d’informations sur les contrôles ActiveX, consultez l’article [contrôles ActiveX MFC](mfc-activex-controls.md).

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour un nouveau développement. Pour plus d’informations, consultez [contrôles ActiveX](activex-controls.md).

Les conteneurs de contrôle prennent généralement deux formes dans un projet :

- Les boîtes de dialogue et les fenêtres semblables à des boîtes de dialogue comme les modes formulaire, où un contrôle ActiveX est utilisé quelque part dans la boîte de dialogue.

- Les fenêtres d'une application, où un contrôle ActiveX est utilisé dans la barre d'outils, ou tout autre emplacement dans la fenêtre utilisateur.

Le conteneur de contrôles ActiveX interagit avec le contrôle via des [méthodes](mfc-activex-controls-methods.md) et des [Propriétés](mfc-activex-controls-properties.md)exposées. Ces méthodes et propriétés, accessibles et modifiées par le conteneur de contrôle, sont accessibles par le biais d'une classe wrapper dans le projet conteneur de contrôle ActiveX. Le contrôle ActiveX incorporé peut également interagir avec le conteneur en déclenchant (envoyant) des [événements](mfc-activex-controls-events.md) pour notifier au conteneur qu’une action a eu lieu. Le conteneur de contrôle peut choisir de réagir à ces notifications ou non.

D'autres articles décrivent plusieurs rubriques, allant de la création d'un projet conteneur de contrôle ActiveX aux problèmes d'implémentation de base liés aux conteneurs de contrôle ActiveX créés avec Visual C++ :

- [Création d’un conteneur de contrôles ActiveX MFC](reference/creating-an-mfc-activex-control-container.md)

- [Conteneurs pour les contrôles ActiveX](containers-for-activex-controls.md)

- [Conteneurs de contrôles ActiveX : activation manuelle d’une relation contenant-contenu de contrôle ActiveX](activex-control-containers-manually-enabling-activex-control-containment.md)

- [Conteneurs de contrôles ActiveX : insertion d'un contrôle dans une application de conteneur de contrôle](inserting-a-control-into-a-control-container-application.md)

- [Conteneurs de contrôles ActiveX : association d’un contrôle ActiveX à une variable membre](activex-control-containers-connecting-an-activex-control-to-a-member-variable.md)

- [Conteneurs de contrôles ActiveX : gestion des événements à partir d’un contrôle ActiveX](activex-control-containers-handling-events-from-an-activex-control.md)

- [Conteneurs de contrôles ActiveX : consultation et modification des propriétés de contrôle](activex-control-containers-viewing-and-modifying-control-properties.md)

- [Conteneurs de contrôles ActiveX : programmation de contrôles ActiveX dans un conteneur de contrôles ActiveX](programming-activex-controls-in-a-activex-control-container.md)

- [Conteneurs de contrôles ActiveX : utilisation de contrôles dans un conteneur autre que de boîte de dialogue](activex-control-containers-using-controls-in-a-non-dialog-container.md)

Pour plus d’informations sur l’utilisation des contrôles ActiveX dans une boîte de dialogue, consultez les rubriques de l' [éditeur de boîtes de dialogue](../windows/dialog-editor.md) .

Pour obtenir la liste des articles qui expliquent les détails du développement de contrôles ActiveX à l’aide de Visual C++ et des classes de contrôle ActiveX MFC, consultez [contrôles ActiveX MFC](mfc-activex-controls.md). Les articles sont regroupés par catégories fonctionnelles.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](mfc-activex-controls.md)
