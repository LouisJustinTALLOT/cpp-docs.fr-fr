---
title: Dois-je dériver les nouvelles classes de CObject ?
ms.date: 11/04/2016
helpviewer_keywords:
- derived classes [MFC], from CObject
- CObject class [MFC], when to use
ms.assetid: 26021031-feaf-424c-80d1-9547c4409d6a
ms.openlocfilehash: 371ede0f0921182c066b4cb224e66b18eb6f1208
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616738"
---
# <a name="do-i-have-to-derive-new-classes-from-cobject"></a>Dois-je dériver les nouvelles classes de CObject ?

Non, ce n’est pas le tout.

Dérivez une classe de [CObject](reference/cobject-class.md) lorsque vous avez besoin des fonctionnalités qu’elle fournit, telles que la sérialisation ou la création dynamique. De nombreuses classes de données doivent être sérialisées en fichiers. il est donc souvent judicieux de les dériver de `CObject` . Pour obtenir un exemple de classe dérivée de `CObject` , consultez l' [exemple SCRIBBLE](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Voir aussi

[Classe CObject : Forum Aux Questions](cobject-class-frequently-asked-questions.md)
