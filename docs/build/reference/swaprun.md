---
title: /SWAPRUN
ms.date: 11/04/2016
f1_keywords:
- /swaprun
helpviewer_keywords:
- /SWAPRUN editbin option
- -SWAPRUN editbin option
- SWAPRUN editbin option
ms.assetid: 6eefd7f3-ca47-48e3-8509-323d27cf4ae7
ms.openlocfilehash: 45a682c911a090bd176054e96882904d3bc68269
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57421257"
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
