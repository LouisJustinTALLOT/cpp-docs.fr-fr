---
description: 'En savoir plus sur les éléments suivants : raw_property_prefixes l’attribut import'
title: raw_property_prefixes l’attribut d’importation
ms.date: 08/29/2019
f1_keywords:
- raw_property_prefixes
helpviewer_keywords:
- raw_property_prefixes attribute
ms.assetid: 03a0f48c-c460-4175-a762-9f7f8d84b12f
ms.openlocfilehash: 7289f9aeba249249ecf78ffb3ad3b32669ac9fe3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142712"
---
# <a name="raw_property_prefixes-import-attribute"></a>raw_property_prefixes l’attribut d’importation

**Section spécifique à C++**

Spécifie d'autres préfixes pour trois méthodes de propriété.

## <a name="syntax"></a>Syntaxe

> **#import** *de la bibliothèque de types* **raw_property_prefixes (** «*GetPrefix*» **,** «*PutPrefix*» **,** «*PutRefPrefix*» **)**

### <a name="parameters"></a>Paramètres

*GetPrefix*\
Préfixe à utiliser pour les `propget` méthodes.

*PutPrefix*\
Préfixe à utiliser pour les `propput` méthodes.

*PutRefPrefix*\
Préfixe à utiliser pour les `propputref` méthodes.

## <a name="remarks"></a>Notes

Par défaut, les méthodes de bas niveau `propget` , `propput` et `propputref` sont exposées par les fonctions membres nommées à l’aide de préfixes `get_` , `put_` , et `putref_` , respectivement. Ces préfixes sont compatibles avec les noms utilisés dans les fichiers d'en-tête générés par MIDL.

**FIN de la section spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
