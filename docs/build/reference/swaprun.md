---
title: /SWAPRUN
ms.date: 11/04/2016
f1_keywords:
- /swaprun_editbin
helpviewer_keywords:
- /SWAPRUN editbin option
- -SWAPRUN editbin option
- SWAPRUN editbin option
ms.assetid: 6eefd7f3-ca47-48e3-8509-323d27cf4ae7
ms.openlocfilehash: 83aa2cdb445ed1ac6bac5b1237f90a116986b0a9
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438846"
---
# <a name="swaprun"></a>/SWAPRUN

```
/SWAPRUN:{[!]NET|[!]CD}
```

## <a name="remarks"></a>Notes

Cette option modifie l’image pour indiquer au système d’exploitation de copier l’image dans un fichier d’échange et de l’exécuter à partir de là. Utilisez cette option pour les images qui résident sur des réseaux ou des supports amovibles.

Vous pouvez ajouter ou supprimer les qualificateurs NET ou CD :

- NET indique que l’image réside sur un réseau.

- CD indique que l’image se trouve sur un CD-ROM ou un support amovible similaire.

- Utilisez ! NET et ! CD pour inverser les effets du NET et du CD.

## <a name="see-also"></a>Voir aussi

[Options EDITBIN](editbin-options.md)
