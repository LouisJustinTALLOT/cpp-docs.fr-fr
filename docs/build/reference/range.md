---
description: En savoir plus sur:/RANGE
title: /RANGE
ms.date: 11/04/2016
f1_keywords:
- /RANGE
helpviewer_keywords:
- /RANGE dumpbin option
- -RANGE dumpbin option
ms.assetid: 7eeba266-32be-49cc-a350-96bdf541f98a
ms.openlocfilehash: 9af54bddde977e92b5256f0835c31afbff1405d4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225399"
---
# <a name="range"></a>/RANGE

Modifie la sortie de DUMPBIN quand elle est utilisée avec d’autres options DUMPBIN, telles que/RAWDATA ou/DISASM.

## <a name="syntax"></a>Syntaxe

```
/RANGE:vaMin[,vaMax]
```

## <a name="parameters"></a>Paramètres

*vaMin*<br/>
Adresse virtuelle à laquelle vous souhaitez que l’opération DUMPBIN commence.

*vaMax*<br/>
Facultatif Adresse virtuelle à laquelle vous souhaitez que l’opération DUMPBIN se termine. S’il n’est pas spécifié, DUMPBIN passe à la fin du fichier.

## <a name="remarks"></a>Notes

Pour afficher les adresses virtuelles d’une image, utilisez le fichier de mappage pour l’image (RVA + base), l’option **/DISASM** ou **/headers** de DUMPBIN, ou la fenêtre Code machine dans le débogueur Visual Studio.

## <a name="example"></a>Exemple

Dans cet exemple, **/Range** est utilisé pour modifier l’affichage de l’option **/DISASM** . Dans cet exemple, la valeur de départ est exprimée sous la forme d’un nombre décimal et la valeur de fin est spécifiée sous la forme d’un nombre hexadécimal.

```
dumpbin /disasm /range:4219334,0x004061CD t.exe
```

## <a name="see-also"></a>Voir aussi

[Options DUMPBIN](dumpbin-options.md)
