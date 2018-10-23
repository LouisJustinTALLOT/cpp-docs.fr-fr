---
title: TLBID | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- tlbid
dev_langs:
- C++
helpviewer_keywords:
- tlbid attribute
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6324ec9a64a0d1c47dab8d1beee021f6c8752a96
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49807976"
---
# <a name="tlbid"></a>tlbid

**Spécifique à C++**

Permet de charger des bibliothèques autres que la bibliothèque de types principale.

## <a name="syntax"></a>Syntaxe

```
tlbid(number)
```

### <a name="parameters"></a>Paramètres

*Nombre*<br/>
Numéro de la bibliothèque de types dans `filename`.

## <a name="remarks"></a>Notes

Si plusieurs bibliothèques de types sont intégrées à une même DLL, il est possible de charger des bibliothèques autres que la bibliothèque de type principal à l’aide de **tlbid**.

Exemple :

```cpp
#import <MyResource.dll> tlbid(2)
```

équivaut à :

```cpp
LoadTypeLib("MyResource.dll\\2");
```

**FIN spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directive #import](../preprocessor/hash-import-directive-cpp.md)