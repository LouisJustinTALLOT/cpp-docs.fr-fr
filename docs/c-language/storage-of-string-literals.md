---
title: Stockage de littéraux de chaîne
ms.date: 11/04/2016
helpviewer_keywords:
- string literals, storage
ms.assetid: ba5e4d2c-d456-44b3-a8ca-354af547ac50
ms.openlocfilehash: 0d505479f0844122826a2f07b57eaa69f33932e8
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148125"
---
# <a name="storage-of-string-literals"></a>Stockage de littéraux de chaîne

Les caractères d'une chaîne littérale sont stockés dans l'ordre à des emplacements de mémoire contigus. Une séquence d'échappement (telle que **\\\\** ou **\\"**) dans un littéral de chaîne compte comme un caractère unique. Un caractère Null (représenté par la séquence d'échappement **\0**) est ajouté automatiquement et marque la fin de chaque littéral de chaîne. (Cela se produit au cours de la [phase de translation](../preprocessor/phases-of-translation.md) 7.) Notez que le compilateur ne peut pas stocker deux chaînes identiques à deux adresses différentes. [/GF](../build/reference/gf-eliminate-duplicate-strings.md) oblige le compilateur à placer une copie unique des chaînes identiques dans le fichier exécutable.

## <a name="remarks"></a>Remarques

**Section spécifique à Microsoft**

Les chaînes ont une durée de stockage statique. Pour plus d'informations sur la durée de stockage, consultez [Classes de stockage](../c-language/c-storage-classes.md).

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Littéraux de chaîne C](../c-language/c-string-literals.md)
