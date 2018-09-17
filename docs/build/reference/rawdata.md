---
title: -RAWDATA | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /rawdata
dev_langs:
- C++
helpviewer_keywords:
- RAWDATA dumpbin option
- raw data
- -RAWDATA dumpbin option
- /RAWDATA dumpbin option
ms.assetid: 41cba845-5e1f-415e-9fe4-604a52235983
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 38677b0e67ddaec5b6ef0e3fcffed1bed27826b6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707172"
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