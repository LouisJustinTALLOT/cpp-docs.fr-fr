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
ms.openlocfilehash: ff11e64ae8ec0eb5236369e8322e051ee40b26bd
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2019
ms.locfileid: "57820115"
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

[Options EDITBIN](editbin-options.md)
