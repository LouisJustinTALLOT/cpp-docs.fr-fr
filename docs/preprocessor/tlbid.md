---
title: TLBID (importer l’attribut
ms.date: 08/29/2019
f1_keywords:
- tlbid
helpviewer_keywords:
- tlbid attribute
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
ms.openlocfilehash: 364fb224b0f2769cb0933e71d18ff70768189328
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216533"
---
# <a name="tlbid-import-attribute"></a>TLBID (importer l’attribut

**C++Plus**

Permet de charger des bibliothèques autres que la bibliothèque de types principale.

## <a name="syntax"></a>Syntaxe

> **#import** *bibliothèque de types-dll* **TLBID ((** *nombre* **)**

### <a name="parameters"></a>Paramètres

*certain*\
Numéro de la bibliothèque de types dans le *type-library-dll*.

## <a name="remarks"></a>Notes

Si plusieurs bibliothèques de types sont générées dans une seule DLL, il est possible de charger des bibliothèques autres que la bibliothèque de types principale à l’aide de **TLBID (** .

Par exemple :

```cpp
#import <MyResource.dll> tlbid(2)
```

équivaut à :

```cpp
LoadTypeLib("MyResource.dll\\2");
```

**Spécifique C++ à la fin**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
