---
title: Création d'objet dynamique
ms.date: 11/04/2016
helpviewer_keywords:
- object creation [MFC], dynamically at run time
- CObject class [MFC], dynamic object creation
- objects [MFC], creating dynamically at run time
- dynamic object creation [MFC]
ms.assetid: 3e0f51cb-3e24-4231-817f-1c0ce9f2d5df
ms.openlocfilehash: 75d4a055f047abfcac4451c04bcd1cc75650c89a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563721"
---
# <a name="dynamic-object-creation"></a>Création d'objet dynamique

Cet article explique comment créer un objet dynamiquement au moment de l’exécution. La procédure utilise les informations de classe d’exécution, comme indiqué dans l’article [l’accès aux informations sur la classe runtime](../mfc/accessing-run-time-class-information.md).

#### <a name="to-dynamically-create-an-object-given-its-run-time-class"></a>Pour créer dynamiquement un objet en fonction de sa classe d’exécution

1. Utilisez le code suivant pour créer dynamiquement un objet à l’aide de la `CreateObject` fonction de la `CRuntimeClass`. Notez que, en cas d’échec, `CreateObject` retourne **NULL** au lieu de lever une exception :

   [!code-cpp[NVC_MFCCObjectSample#6](../mfc/codesnippet/cpp/dynamic-object-creation_1.cpp)]

## <a name="see-also"></a>Voir aussi

[Utilisation de CObject](../mfc/using-cobject.md)

