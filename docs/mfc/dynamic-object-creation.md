---
title: Création d'objet dynamique
ms.date: 03/27/2020
helpviewer_keywords:
- object creation [MFC], dynamically at run time
- CObject class [MFC], dynamic object creation
- objects [MFC], creating dynamically at run time
- dynamic object creation [MFC]
ms.assetid: 3e0f51cb-3e24-4231-817f-1c0ce9f2d5df
ms.openlocfilehash: 40a17d3ed458d0634fd5bf27b54d0a36a65e35b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364808"
---
# <a name="dynamic-object-creation"></a>Création d'objet dynamique

Cet article explique comment créer un objet dynamiquement au moment de l’exécution. La procédure utilise des informations de classe en temps d’exécution, comme nous l’avons vu dans l’article [Accessing Run-Time Class Information](../mfc/accessing-run-time-class-information.md).

#### <a name="dynamically-create-an-object-given-its-run-time-class"></a>Créer dynamiquement un objet compte tenu de sa classe de temps d’exécution

1. Utilisez le code suivant pour créer `CreateObject` dynamiquement `CRuntimeClass`un objet en utilisant la fonction de la . En cas `CreateObject` d’échec, les retours **NULL** au lieu de soulever une exception :

   [!code-cpp[NVC_MFCCObjectSample#6](../mfc/codesnippet/cpp/dynamic-object-creation_1.cpp)]

## <a name="see-also"></a>Voir aussi

[Détruire des objets](tn017-destroying-window-objects.md)
de fenêtre[à l’aide de CObject](using-cobject.md)
