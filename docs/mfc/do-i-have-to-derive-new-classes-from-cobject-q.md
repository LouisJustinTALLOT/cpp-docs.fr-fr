---
title: Dois-je dériver les nouvelles classes de CObject ? | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CObject
dev_langs:
- C++
helpviewer_keywords:
- derived classes [MFC], from CObject
- CObject class [MFC], when to use
ms.assetid: 26021031-feaf-424c-80d1-9547c4409d6a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ec080e556b57afadbc3d958f4dba5ac6393108aa
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408906"
---
# <a name="do-i-have-to-derive-new-classes-from-cobject"></a>Dois-je dériver les nouvelles classes de CObject ?

Non, vous n’avez pas.

Dérivez une classe de [CObject](../mfc/reference/cobject-class.md) lorsque vous avez besoin des fonctionnalités qu’il fournit, telles que la sérialisation ou de la création dynamique d’objets. De nombreuses classes de données doivent être sérialisés dans des fichiers, il est souvent judicieux de les dériver de `CObject`. Pour un exemple d’une classe dérivée de `CObject`, consultez le [exemple Scribble](../visual-cpp-samples.md).

## <a name="see-also"></a>Voir aussi

[Classe CObject : Forum Aux Questions](../mfc/cobject-class-frequently-asked-questions.md)
