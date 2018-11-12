---
title: Conteneurs de contrôles ActiveX
ms.date: 09/12/2018
helpviewer_keywords:
- ActiveX control containers [MFC]
- OLE controls [MFC], containers
ms.assetid: 0eb1a713-e607-4c79-a0c7-67c5f1fd5fab
ms.openlocfilehash: 3356c5d94eaf4cef0b44c509144d0de4a5d42abf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549109"
---
# <a name="activex-control-containers"></a>Conteneurs de contrôles ActiveX

Un conteneur de contrôle ActiveX est un conteneur qui prend entièrement en charge les contrôles ActiveX et peut les incorporer dans ses propres fenêtres ou boîtes de dialogue. Un contrôle ActiveX est un composant logiciel réutilisable que vous pouvez utiliser dans les projets de développement. Les contrôles permettent à l'utilisateur de votre application d'accéder à des bases de données, de surveiller des données et d'effectuer des sélections dans vos applications. Pour plus d’informations sur les contrôles ActiveX, consultez l’article [contrôles ActiveX MFC](../mfc/mfc-activex-controls.md).

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour tout nouveau développement. Pour plus d’informations, consultez [contrôles ActiveX](activex-controls.md).

Les conteneurs de contrôle prennent généralement deux formes dans un projet :

- Les boîtes de dialogue et les fenêtres semblables à des boîtes de dialogue comme les modes formulaire, où un contrôle ActiveX est utilisé quelque part dans la boîte de dialogue.

- Les fenêtres d'une application, où un contrôle ActiveX est utilisé dans la barre d'outils, ou tout autre emplacement dans la fenêtre utilisateur.

L’ActiveX conteneur de contrôle interagit avec le contrôle via exposées [méthodes](../mfc/mfc-activex-controls-methods.md) et [propriétés](../mfc/mfc-activex-controls-properties.md). Ces méthodes et propriétés, accessibles et modifiées par le conteneur de contrôle, sont accessibles par le biais d'une classe wrapper dans le projet conteneur de contrôle ActiveX. Le contrôle ActiveX incorporé peut également interagir avec le conteneur en déclenchant (envoyant) [événements](../mfc/mfc-activex-controls-events.md) pour notifier au conteneur qu’une action s’est produite. Le conteneur de contrôle peut choisir de réagir à ces notifications ou non.

D'autres articles décrivent plusieurs rubriques, allant de la création d'un projet conteneur de contrôle ActiveX aux problèmes d'implémentation de base liés aux conteneurs de contrôle ActiveX créés avec Visual C++ :

- [Création d’un conteneur de contrôles ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control-container.md)

- [Conteneurs pour les contrôles ActiveX](../mfc/containers-for-activex-controls.md)

- [Conteneurs de contrôles ActiveX : activation manuelle d’une relation contenant-contenu de contrôle ActiveX](../mfc/activex-control-containers-manually-enabling-activex-control-containment.md)

- [Conteneurs de contrôles ActiveX : insertion d’un contrôle dans une application de conteneur de contrôle](../mfc/inserting-a-control-into-a-control-container-application.md)

- [Conteneurs de contrôles ActiveX : association d’un contrôle ActiveX à une variable membre](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md)

- [Conteneurs de contrôles ActiveX : Contrôler les gestion des événements à partir d’un ActiveX](../mfc/activex-control-containers-handling-events-from-an-activex-control.md)

- [Conteneurs de contrôles ActiveX : consultation et modification des propriétés de contrôle](../mfc/activex-control-containers-viewing-and-modifying-control-properties.md)

- [Conteneurs de contrôles ActiveX : programmation de contrôles ActiveX dans un conteneur de contrôles ActiveX](../mfc/programming-activex-controls-in-a-activex-control-container.md)

- [Conteneurs de contrôles ActiveX : utilisation de contrôles dans un conteneur autre que de boîte de dialogue](../mfc/activex-control-containers-using-controls-in-a-non-dialog-container.md)

Pour plus d’informations sur l’utilisation de contrôles ActiveX dans une boîte de dialogue, consultez la [boîte de dialogue Éditeur](../windows/dialog-editor.md) rubriques.

Pour obtenir la liste des articles qui expliquent les détails du développement de contrôles ActiveX à l’aide de Visual C++ et les classes de contrôles ActiveX MFC, consultez [contrôles ActiveX MFC](../mfc/mfc-activex-controls.md). Les articles sont regroupés par catégories fonctionnelles.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)

