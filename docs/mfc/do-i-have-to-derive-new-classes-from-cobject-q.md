---
description: 'En savoir plus sur : dois-je dériver de nouvelles classes de CObject ?'
title: Dois-je dériver les nouvelles classes de CObject ?
ms.date: 11/04/2016
helpviewer_keywords:
- derived classes [MFC], from CObject
- CObject class [MFC], when to use
ms.assetid: 26021031-feaf-424c-80d1-9547c4409d6a
ms.openlocfilehash: d37570cb62f1ee274e4cea85fc95a9221c95fd8a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97261305"
---
# <a name="do-i-have-to-derive-new-classes-from-cobject"></a>Dois-je dériver les nouvelles classes de CObject ?

Non, ce n’est pas le tout.

Dérivez une classe de [CObject](reference/cobject-class.md) lorsque vous avez besoin des fonctionnalités qu’elle fournit, telles que la sérialisation ou la création dynamique. De nombreuses classes de données doivent être sérialisées en fichiers. il est donc souvent judicieux de les dériver de `CObject` . Pour obtenir un exemple de classe dérivée de `CObject` , consultez l' [exemple SCRIBBLE](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Voir aussi

[Classe CObject : Forum aux questions](cobject-class-frequently-asked-questions.md)
