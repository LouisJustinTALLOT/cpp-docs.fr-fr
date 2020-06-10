---
title: Génération à partir du Framework
ms.date: 11/04/2016
helpviewer_keywords:
- application-specific classes [MFC]
- application framework [MFC], building applications
- applications [MFC]
- MFC, application development
ms.assetid: 883f0f19-866f-4221-8a3d-5607941dc8d0
ms.openlocfilehash: 2c171b223892c8bca1b32e18c57c09027558c192
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619732"
---
# <a name="building-on-the-framework"></a>Génération à partir du Framework

Votre rôle dans la configuration d’une application avec l’infrastructure MFC consiste à fournir le code source spécifique à l’application et à connecter les composants en définissant les messages et les commandes auxquels ils répondent. Vous utilisez le langage C++ et les techniques C++ standard pour dériver vos propres classes spécifiques à l’application de celles fournies par la bibliothèque de classes et pour substituer et augmenter le comportement de la classe de base.

Dans les rubriques connexes, les tableaux suivants décrivent la séquence générale des opérations que vous suivez généralement et vos responsabilités par rapport aux responsabilités de l’infrastructure :

- [Séquence pour générer une application avec le framework](sequence-of-operations-for-building-mfc-applications.md)

- [Ordre des opérations pour la création d’applications OLE](sequence-of-operations-for-creating-ole-applications.md)

- [Ordre des opérations pour la création de contrôles ActiveX](sequence-of-operations-for-creating-activex-controls.md)

- [Ordre des opérations pour la création d’applications de base de données](sequence-of-operations-for-creating-database-applications.md)

Pour l’essentiel, vous pouvez suivre ces tableaux comme une séquence d’étapes de création d’une application MFC, bien que certaines d’entre elles soient des options alternatives. Par exemple, la plupart des applications utilisent un type de classe d’affichage parmi les différents types disponibles.

## <a name="see-also"></a>Voir aussi

[Rubriques MFC générales](general-mfc-topics.md)
