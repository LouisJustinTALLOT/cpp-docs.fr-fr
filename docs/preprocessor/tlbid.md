---
title: tlbid
ms.date: 10/18/2018
f1_keywords:
- tlbid
helpviewer_keywords:
- tlbid attribute
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
ms.openlocfilehash: 31b71f7c195a7e2ee649b40197551e4ff5efda2c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584510"
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