---
title: raw_property_prefixes importer l’attribut
ms.date: 08/29/2019
f1_keywords:
- raw_property_prefixes
helpviewer_keywords:
- raw_property_prefixes attribute
ms.assetid: 03a0f48c-c460-4175-a762-9f7f8d84b12f
ms.openlocfilehash: d4d91470781e7c5f673fd228c24904322d1db8b3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216041"
---
# <a name="raw_property_prefixes-import-attribute"></a>raw_property_prefixes importer l’attribut

**C++Plus**

Spécifie d'autres préfixes pour trois méthodes de propriété.

## <a name="syntax"></a>Syntaxe

> **#import** *bibliothèque de types* **raw_property_prefixes (** «*GetPrefix*» **,** «*PutPrefix*» **,** «*PutRefPrefix*» **)**

### <a name="parameters"></a>Paramètres

*GetPrefix*\
Préfixe à utiliser pour `propget` les méthodes.

*PutPrefix*\
Préfixe à utiliser pour `propput` les méthodes.

*PutRefPrefix*\
Préfixe à utiliser pour `propputref` les méthodes.

## <a name="remarks"></a>Notes

Par défaut, les méthodes de `propget`bas `propput`niveau, `propputref` et sont exposées par les fonctions membres nommées à l' `get_`aide `put_`de préfixes,, et `putref_`, respectivement. Ces préfixes sont compatibles avec les noms utilisés dans les fichiers d'en-tête générés par MIDL.

**Spécifique C++ à la fin**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
