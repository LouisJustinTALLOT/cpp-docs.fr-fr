---
description: En savoir plus sur:/SWAPRUN
title: /SWAPRUN
ms.date: 11/04/2016
f1_keywords:
- /swaprun_editbin
helpviewer_keywords:
- /SWAPRUN editbin option
- -SWAPRUN editbin option
- SWAPRUN editbin option
ms.assetid: 6eefd7f3-ca47-48e3-8509-323d27cf4ae7
ms.openlocfilehash: 68d53a8d5fa7337fb29f624e26b71790f78d29dd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97230170"
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
