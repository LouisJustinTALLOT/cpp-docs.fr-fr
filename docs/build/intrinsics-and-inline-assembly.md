---
title: Fonctions intrinsèques et Inline Assembly | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8affd4bb-279d-46f3-851f-8be0a9c5ed3f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6a87e577af339099eda56a3b9d91929a05253a43
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716246"
---
# <a name="intrinsics-and-inline-assembly"></a>Assembly de fonctions intrinsèques et inline

Une des contraintes pour le x64 compilateur consiste à n’avoir aucune prise en charge d’assembleur inline. Cela signifie que les fonctions qui ne peuvent pas être écrits en C ou C++ doivent être écrites en tant que sous-routines ou fonctions intrinsèques prises en charge par le compilateur. Certaines fonctions sont sensibles aux performances et d’autres pas. Les fonctions sensibles aux performances doivent être implémentées comme fonctions intrinsèques.

Les fonctions intrinsèques prises en charge par le compilateur sont décrites dans [intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md).

## <a name="see-also"></a>Voir aussi

[Conventions des logiciels x64](../build/x64-software-conventions.md)