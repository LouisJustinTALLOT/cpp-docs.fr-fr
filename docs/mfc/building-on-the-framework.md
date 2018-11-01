---
title: Génération à partir du Framework
ms.date: 11/04/2016
helpviewer_keywords:
- application-specific classes [MFC]
- application framework [MFC], building applications
- applications [MFC]
- MFC, application development
ms.assetid: 883f0f19-866f-4221-8a3d-5607941dc8d0
ms.openlocfilehash: 511d66821bf23c149fafb0bfd397929077f020ac
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50496237"
---
# <a name="building-on-the-framework"></a>Génération à partir du Framework

Votre rôle dans la configuration d’une application avec l’infrastructure MFC est de fournir le code spécifique à l’application source et pour connecter les composants en définissant les messages et les commandes auxquels ils répondent. Vous permet le langage C++ et les techniques C++ standard pour dériver vos propres classes spécifiques à l’application à partir de celles fournies par la bibliothèque de classes et substituer et enrichir le comportement de la classe de base.

Dans les rubriques connexes, les tableaux suivants décrivent la séquence générale des opérations que généralement suivront et vos responsabilités et les responsabilités de l’infrastructure :

- [Séquence de génération d’une Application avec l’infrastructure](../mfc/sequence-of-operations-for-building-mfc-applications.md)

- [Ordre des opérations pour la création d’applications OLE](../mfc/sequence-of-operations-for-creating-ole-applications.md)

- [Ordre des opérations pour la création de contrôles ActiveX](../mfc/sequence-of-operations-for-creating-activex-controls.md)

- [Ordre des opérations pour la création d’applications de base de données](../mfc/sequence-of-operations-for-creating-database-applications.md)

La plupart du temps, vous pouvez suivre ces tables comme une séquence d’étapes de création d’une application MFC, bien que certaines étapes sont les autres options. Par exemple, la plupart des applications utilisent un seul type de classe d’affichage de plusieurs types disponibles.

## <a name="see-also"></a>Voir aussi

[Rubriques MFC générales](../mfc/general-mfc-topics.md)

