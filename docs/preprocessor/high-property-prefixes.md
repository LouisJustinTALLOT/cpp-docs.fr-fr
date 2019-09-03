---
title: high_property_prefixes importer l’attribut
ms.date: 08/29/2019
f1_keywords:
- high_property_prefixes
helpviewer_keywords:
- high_property_prefixes attribute
ms.assetid: 91c6cc2b-19b6-4aba-8831-d9e5cccb58b5
ms.openlocfilehash: 9e44f6f1afae479f803f4c6d866ef3ee38744561
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219004"
---
# <a name="high_property_prefixes-import-attribute"></a>high_property_prefixes importer l’attribut

**C++Plus**

Spécifie d'autres préfixes pour trois méthodes de propriété.

## <a name="syntax"></a>Syntaxe

> **#import** *bibliothèque de types* **high_property_prefixes (** «*GetPrefix*» **,** «*PutPrefix*» **,** «*PutRefPrefix*» **)**

### <a name="parameters"></a>Paramètres

*GetPrefix*\
Préfixe à utiliser pour les `propget` méthodes.

*PutPrefix*\
Préfixe à utiliser pour les `propput` méthodes.

*PutRefPrefix*\
Préfixe à utiliser pour les `propputref` méthodes.

## <a name="remarks"></a>Notes

Par défaut, les méthodes de `propget`gestion des erreurs de haut niveau, `propput`et `propputref` sont exposées par les fonctions membres nommées `Get`avec `Put`des préfixes, et `PutRef`, respectivement.

**Spécifique C++ à la fin**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
