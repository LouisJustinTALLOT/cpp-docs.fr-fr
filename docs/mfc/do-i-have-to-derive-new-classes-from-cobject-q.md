---
title: Dois-je dériver les nouvelles classes de CObject ?
ms.date: 11/04/2016
helpviewer_keywords:
- derived classes [MFC], from CObject
- CObject class [MFC], when to use
ms.assetid: 26021031-feaf-424c-80d1-9547c4409d6a
ms.openlocfilehash: d38e589f371fc56f5566c56de7b19c366065a503
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446924"
---
# <a name="do-i-have-to-derive-new-classes-from-cobject"></a>Dois-je dériver les nouvelles classes de CObject ?

Non, ce n’est pas le tout.

Dérivez une classe de [CObject](../mfc/reference/cobject-class.md) lorsque vous avez besoin des fonctionnalités qu’elle fournit, telles que la sérialisation ou la création dynamique. De nombreuses classes de données doivent être sérialisées en fichiers. il est donc souvent judicieux de les dériver de `CObject`. Pour obtenir un exemple de classe dérivée de `CObject`, consultez l' [exemple SCRIBBLE](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Voir aussi

[Classe CObject : Forum Aux Questions](../mfc/cobject-class-frequently-asked-questions.md)
