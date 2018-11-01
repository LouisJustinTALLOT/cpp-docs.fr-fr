---
title: Dois-je dériver les nouvelles classes de CObject ?
ms.date: 11/04/2016
f1_keywords:
- CObject
helpviewer_keywords:
- derived classes [MFC], from CObject
- CObject class [MFC], when to use
ms.assetid: 26021031-feaf-424c-80d1-9547c4409d6a
ms.openlocfilehash: c2361967dcfce5e46aeec65ade3d7056b362949d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636603"
---
# <a name="do-i-have-to-derive-new-classes-from-cobject"></a>Dois-je dériver les nouvelles classes de CObject ?

Non, vous n’avez pas.

Dérivez une classe de [CObject](../mfc/reference/cobject-class.md) lorsque vous avez besoin des fonctionnalités qu’il fournit, telles que la sérialisation ou de la création dynamique d’objets. De nombreuses classes de données doivent être sérialisés dans des fichiers, il est souvent judicieux de les dériver de `CObject`. Pour un exemple d’une classe dérivée de `CObject`, consultez le [exemple Scribble](../visual-cpp-samples.md).

## <a name="see-also"></a>Voir aussi

[Classe CObject : Forum Aux Questions](../mfc/cobject-class-frequently-asked-questions.md)
