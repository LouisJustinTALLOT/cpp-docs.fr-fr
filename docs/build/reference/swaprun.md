---
title: -SWAPRUN | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /swaprun
dev_langs:
- C++
helpviewer_keywords:
- /SWAPRUN editbin option
- -SWAPRUN editbin option
- SWAPRUN editbin option
ms.assetid: 6eefd7f3-ca47-48e3-8509-323d27cf4ae7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1a93b854dba2855fa68bb3be163cecdcd3570df0
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723097"
---
# <a name="swaprun"></a>/SWAPRUN

```
/SWAPRUN:{[!]NET|[!]CD}
```

## <a name="remarks"></a>Notes

Cette option modifie l’image pour indiquer au système d’exploitation pour copier l’image vers un fichier d’échange et l’exécuter à partir de là. Utilisez cette option pour les images qui résident sur des réseaux ou un support amovible.

Vous pouvez ajouter ou supprimer les qualificateurs NET ou CD :

- NET indique que l’image se trouve sur un réseau.

- CD indique que l’image se trouve sur un CD-ROM ou un support amovible similaire.

- Utilisez ! NET et ! CD pour inverser les effets de NET et CD.

## <a name="see-also"></a>Voir aussi

[Options EDITBIN](../../build/reference/editbin-options.md)