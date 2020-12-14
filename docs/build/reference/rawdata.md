---
description: En savoir plus sur:/RAWDATA
title: /RAWDATA
ms.date: 11/04/2016
f1_keywords:
- /rawdata
helpviewer_keywords:
- RAWDATA dumpbin option
- raw data
- -RAWDATA dumpbin option
- /RAWDATA dumpbin option
ms.assetid: 41cba845-5e1f-415e-9fe4-604a52235983
ms.openlocfilehash: efe2001c0170b8539b98902591849dedaf0fb819
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225373"
---
# <a name="rawdata"></a>/RAWDATA

```
/RAWDATA[:{1|2|4|8|NONE[,number]]
```

## <a name="remarks"></a>Notes

Cette option affiche le contenu brut de chaque section du fichier. Les arguments contrôlent le format de l’affichage, comme indiqué ci-dessous :

|Argument|Résultats|
|--------------|------------|
|1|Valeur par défaut. Le contenu s’affiche en octets hexadécimaux, et également en tant que caractères ASCII s’ils ont une représentation imprimée.|
|2|Le contenu s’affiche sous la forme de valeurs hexadécimales sur 2 octets.|
|4|Le contenu s’affiche sous la forme de valeurs hexadécimales sur 4 octets.|
|8|Le contenu s’affiche sous la forme de valeurs hexadécimales de 8 octets.|
|Aucune|Les données brutes sont supprimées. Cet argument est utile pour contrôler la sortie de/ALL.|
|*Nombre*|Les lignes affichées sont définies sur une largeur qui contient des `number` valeurs par ligne.|

Seule l’option [/HEADERS](headers.md) DUMPBIN peut être utilisée sur les fichiers générés avec l’option du compilateur [/GL](gl-whole-program-optimization.md).

## <a name="see-also"></a>Voir aussi

[Options DUMPBIN](dumpbin-options.md)
