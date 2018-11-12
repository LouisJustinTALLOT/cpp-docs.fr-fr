---
title: Propriété modificateur d’un accélérateur (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- Modifier property
ms.assetid: f05a9379-e037-4cfb-b6ef-d2c655bcfa7f
ms.openlocfilehash: f9dfcbde68d2b3d1ebdd1b94aa40339bbc0ff4e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50650674"
---
# <a name="accelerator-modifier-property-c"></a>Propriété modificateur d’un accélérateur (C++)

Les éléments suivants sont des entrées valides pour la propriété Modifier dans la table d’accélérateurs.

|Value|Description|
|-----------|-----------------|
|**Aucun**|Utilisateur appuie sur uniquement le **clé** valeur. Utilisé avec les valeurs ASCII/ANSI 001 à 026, ce qui est ^ A à ^ Z (CTRL-A à CTRL-Z).|
|**Alt**|L’utilisateur doit appuyer sur la **Alt** clé avant du **clé** valeur.|
|**Ctrl**|L’utilisateur doit appuyer sur la **Ctrl** clé avant du **clé** valeur. Non valide avec le Type ASCII.|
|**Maj**|L’utilisateur doit appuyer sur la **MAJ** clé avant du **clé** valeur.|
|**Ctrl + Alt**|L’utilisateur doit appuyer sur le **Ctrl** clé et le **Alt** clé avant du **clé** valeur. Non valide avec le Type ASCII.|
|**CTRL + MAJ**|L’utilisateur doit appuyer sur le **Ctrl** clé et le **MAJ** clé avant du **clé** valeur. Non valide avec le Type ASCII.|
|**ALT + MAJ**|L’utilisateur doit appuyer sur le **Alt** clé et le **MAJ** clé avant du **clé** valeur. Non valide avec le Type ASCII.|
|**Ctrl + Alt + Maj**|L’utilisateur doit appuyer sur **Ctrl**, **Alt**, et **MAJ** avant la **clé** valeur. Non valide avec le Type ASCII.|

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Définition des propriétés d’un accélérateur](../windows/setting-accelerator-properties.md)<br/>
[Éditeur d’accélérateurs](../windows/accelerator-editor.md)