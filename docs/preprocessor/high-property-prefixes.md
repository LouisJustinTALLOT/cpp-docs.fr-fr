---
description: 'En savoir plus sur les éléments suivants : high_property_prefixes l’attribut import'
title: high_property_prefixes l’attribut d’importation
ms.date: 08/29/2019
f1_keywords:
- high_property_prefixes
helpviewer_keywords:
- high_property_prefixes attribute
ms.assetid: 91c6cc2b-19b6-4aba-8831-d9e5cccb58b5
ms.openlocfilehash: af6835f5835c23dceadbb5152e36b0dabcbb8c98
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167472"
---
# <a name="high_property_prefixes-import-attribute"></a>high_property_prefixes l’attribut d’importation

**Section spécifique à C++**

Spécifie d'autres préfixes pour trois méthodes de propriété.

## <a name="syntax"></a>Syntaxe

> **#import** *de la bibliothèque de types* **high_property_prefixes (** «*GetPrefix*» **,** «*PutPrefix*» **,** «*PutRefPrefix*» **)**

### <a name="parameters"></a>Paramètres

*GetPrefix*\
Préfixe à utiliser pour les `propget` méthodes.

*PutPrefix*\
Préfixe à utiliser pour les `propput` méthodes.

*PutRefPrefix*\
Préfixe à utiliser pour les `propputref` méthodes.

## <a name="remarks"></a>Notes

Par défaut, les méthodes de gestion des erreurs de haut niveau `propget` , `propput` et `propputref` sont exposées par les fonctions membres nommées avec des préfixes `Get` , `Put` et `PutRef` , respectivement.

**FIN de la section spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
