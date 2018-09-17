---
title: Structure d’une bibliothèque | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- libraries, structure
ms.assetid: a5fda8e8-4a1b-4499-9095-0df935262ce4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 03c2c66d45ee415ddc4f3ba27b6a100c5e2ec1dc
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702102"
---
# <a name="structure-of-a-library"></a>Structure d'une bibliothèque

Une bibliothèque contient des objets COFF. Les objets dans une bibliothèque de contenir des fonctions et des données qui peuvent être référencées en externe par d’autres objets dans un programme. Un objet dans une bibliothèque est parfois appelé un membre de bibliothèque.

Vous pouvez obtenir des informations supplémentaires sur le contenu d’une bibliothèque en exécutant l’outil DUMPBIN avec l’option /LINKERMEMBER. Pour plus d’informations sur cette option, consultez [Référence DUMPBIN](../../build/reference/dumpbin-reference.md).

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de LIB](../../build/reference/overview-of-lib.md)