---
description: 'En savoir plus sur : création d’objets dynamiques'
title: Création d'objet dynamique
ms.date: 03/27/2020
helpviewer_keywords:
- object creation [MFC], dynamically at run time
- CObject class [MFC], dynamic object creation
- objects [MFC], creating dynamically at run time
- dynamic object creation [MFC]
ms.assetid: 3e0f51cb-3e24-4231-817f-1c0ce9f2d5df
ms.openlocfilehash: b39c0561a98807030c471b3de4cd5921883f9f0e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97290971"
---
# <a name="dynamic-object-creation"></a>Création d'objet dynamique

Cet article explique comment créer un objet de manière dynamique au moment de l’exécution. La procédure utilise les informations de classe d’exécution, comme indiqué dans l’article [accès aux informations de classe Run-Time](accessing-run-time-class-information.md).

#### <a name="dynamically-create-an-object-given-its-run-time-class"></a>Créer dynamiquement un objet en fonction de sa classe Runtime

1. Utilisez le code suivant pour créer dynamiquement un objet à l’aide `CreateObject` de la fonction de `CRuntimeClass` . En cas d’échec, `CreateObject` retourne **null** au lieu de lever une exception :

   [!code-cpp[NVC_MFCCObjectSample#6](codesnippet/cpp/dynamic-object-creation_1.cpp)]

## <a name="see-also"></a>Voir aussi

[Destruction d’objets fenêtres](tn017-destroying-window-objects.md) 
 [Utilisation de CObject](using-cobject.md)
