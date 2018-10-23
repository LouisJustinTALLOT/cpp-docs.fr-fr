---
title: raw_method_prefix | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- raw_method_prefix
dev_langs:
- C++
helpviewer_keywords:
- raw_method_prefix attribute
ms.assetid: 71490313-af78-4bb2-b28a-eee67950d30b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 78094053c963f5d836646e91857e171625c447c9
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808548"
---
# <a name="rawmethodprefix"></a>raw_method_prefix

**Spécifique à C++**

Spécifie un préfixe différent pour éviter les collisions de noms.

## <a name="syntax"></a>Syntaxe

```
raw_method_prefix("Prefix")
```

### <a name="parameters"></a>Paramètres

*Prefix*<br/>
Le préfixe à utiliser.

## <a name="remarks"></a>Notes

Propriétés de bas niveau et les méthodes sont exposées par les fonctions membres nommées avec un préfixe par défaut de **raw_** afin d’éviter les collisions de noms avec les fonctions membres de la gestion des erreurs générales.

> [!NOTE]
> Les effets de la **raw_method_prefix** attribut ne sera pas modifié par la présence de la [raw_interfaces_only](#_predir_raw_interfaces_only) attribut. Le **raw_method_prefix** est toujours prioritaire sur `raw_interfaces_only` pour spécifier un préfixe. Si les deux attributs sont utilisés dans le même `#import` instruction, puis le préfixe spécifié par le **raw_method_prefix** attribut est utilisé.

**FIN spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directive #import](../preprocessor/hash-import-directive-cpp.md)