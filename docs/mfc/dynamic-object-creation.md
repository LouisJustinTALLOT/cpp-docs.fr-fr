---
title: Création d'objet dynamique
ms.date: 03/27/2020
helpviewer_keywords:
- object creation [MFC], dynamically at run time
- CObject class [MFC], dynamic object creation
- objects [MFC], creating dynamically at run time
- dynamic object creation [MFC]
ms.assetid: 3e0f51cb-3e24-4231-817f-1c0ce9f2d5df
ms.openlocfilehash: 00e627e6d73e510ca694966291e2ef518fef18b5
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619547"
---
# <a name="dynamic-object-creation"></a>Création d'objet dynamique

Cet article explique comment créer un objet de manière dynamique au moment de l’exécution. La procédure utilise les informations de classe d’exécution, comme indiqué dans l’article [accès aux informations de classe d’exécution](accessing-run-time-class-information.md).

#### <a name="dynamically-create-an-object-given-its-run-time-class"></a>Créer dynamiquement un objet en fonction de sa classe Runtime

1. Utilisez le code suivant pour créer dynamiquement un objet à l’aide `CreateObject` de la fonction de `CRuntimeClass` . En cas d’échec, `CreateObject` retourne **null** au lieu de lever une exception :

   [!code-cpp[NVC_MFCCObjectSample#6](codesnippet/cpp/dynamic-object-creation_1.cpp)]

## <a name="see-also"></a>Voir aussi

[Destruction d’objets fenêtres](tn017-destroying-window-objects.md) 
 [Utilisation de CObject](using-cobject.md)
