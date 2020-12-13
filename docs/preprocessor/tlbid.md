---
description: 'En savoir plus sur : attribut d’importation TLBID ('
title: TLBID (importer l’attribut
ms.date: 08/29/2019
f1_keywords:
- tlbid
helpviewer_keywords:
- tlbid attribute
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
ms.openlocfilehash: 9bbf15f64c1813013fcd839a2d4f0a34c9872aff
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339050"
---
# <a name="tlbid-import-attribute"></a>TLBID (importer l’attribut

**Section spécifique à C++**

Permet de charger des bibliothèques autres que la bibliothèque de types principale.

## <a name="syntax"></a>Syntaxe

>  *type de #import-bibliothèque-dll* **TLBID ((** *nombre* **)**

### <a name="parameters"></a>Paramètres

*certain*\
Numéro de la bibliothèque de types dans le *type-library-dll*.

## <a name="remarks"></a>Notes

Si plusieurs bibliothèques de types sont générées dans une seule DLL, il est possible de charger des bibliothèques autres que la bibliothèque de types principale à l’aide de **TLBID (**.

Par exemple :

```cpp
#import <MyResource.dll> tlbid(2)
```

équivaut à :

```cpp
LoadTypeLib("MyResource.dll\\2");
```

**FIN de la section spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
