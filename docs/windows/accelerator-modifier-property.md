---
title: Propriété modificateur d’un accélérateur (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Modifier property
ms.assetid: f05a9379-e037-4cfb-b6ef-d2c655bcfa7f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 793e02b4ac083d6fe84ba2cc76ee340bcf2484e9
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44316053"
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

[Définition des propriétés d’un accélérateur](../windows/setting-accelerator-properties.md)  
[Éditeur d’accélérateurs](../windows/accelerator-editor.md)