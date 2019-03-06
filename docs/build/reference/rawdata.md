---
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
ms.openlocfilehash: 4e884ba8bca7b3ccdf900c7da2c43dd741c03d12
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57413366"
---
# <a name="rawdata"></a>/RAWDATA

```
/RAWDATA[:{1|2|4|8|NONE[,number]]
```

## <a name="remarks"></a>Notes

Cette option affiche le contenu brut de chaque section dans le fichier. Les arguments de contrôlent le format de l’affichage, comme indiqué ci-dessous :

|Argument|Résultat|
|--------------|------------|
|1|Valeur par défaut. Contenu s’affiche en octets hexadécimales et également en tant que caractères ASCII s’ils ont une représentation sous forme imprimée.|
|2|Contenu s’affiche en tant que valeurs hexadécimales de 2 octets.|
|4|Contenu s’affiche en tant que valeurs hexadécimales de 4 octets.|
|8|Contenu s’affiche en tant que valeurs hexadécimales de 8 octets.|
|NONE|Données brutes sont supprimées. Cet argument est utile pour contrôler la sortie de/ALL.|
|*Nombre*|Les lignes affichées sont définies à une largeur qui contient `number` valeurs par ligne.|

Uniquement les [/HEADERS](../../build/reference/headers.md) (option DUMPBIN) est disponible pour les fichiers générés avec le [/GL](../../build/reference/gl-whole-program-optimization.md) option du compilateur.

## <a name="see-also"></a>Voir aussi

[DUMPBIN, options](../../build/reference/dumpbin-options.md)
