---
title: Stockage de littéraux de chaîne | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- string literals, storage
ms.assetid: ba5e4d2c-d456-44b3-a8ca-354af547ac50
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 111acab00783de67dcb3ecc8b9d45fe112332158
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019522"
---
# <a name="storage-of-string-literals"></a>Stockage de littéraux de chaîne

Les caractères d'une chaîne littérale sont stockés dans l'ordre à des emplacements de mémoire contigus. Une séquence d'échappement (telle que **\\\\** ou **\\"**) dans un littéral de chaîne compte comme un caractère unique. Un caractère Null (représenté par la séquence d'échappement **\0**) est ajouté automatiquement et marque la fin de chaque littéral de chaîne. (Cela se produit au cours de la [phase de translation](../preprocessor/phases-of-translation.md) 7.) Notez que le compilateur ne peut pas stocker deux chaînes identiques à deux adresses différentes. [/GF](../build/reference/gf-eliminate-duplicate-strings.md) oblige le compilateur à placer une copie unique des chaînes identiques dans le fichier exécutable.

## <a name="remarks"></a>Notes

**Section spécifique à Microsoft**

Les chaînes ont une durée de stockage statique. Pour plus d'informations sur la durée de stockage, consultez [Classes de stockage](../c-language/c-storage-classes.md).

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Littéraux de chaîne C](../c-language/c-string-literals.md)