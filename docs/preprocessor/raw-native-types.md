---
description: 'En savoir plus sur les éléments suivants : raw_native_types l’attribut import'
title: raw_native_types l’attribut d’importation
ms.date: 08/29/2019
f1_keywords:
- raw_native_types
helpviewer_keywords:
- raw_native_types attribute
ms.assetid: 9f38daa8-8dc0-46a5-aff9-f1ff9c1e6f48
ms.openlocfilehash: 64eaadcbb3d9f07d47dd4a33bc16a222cae50f38
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97240531"
---
# <a name="raw_native_types-import-attribute"></a>raw_native_types l’attribut d’importation

**Section spécifique à C++**

Désactive l’utilisation des classes de prise en charge COM dans les fonctions wrapper de haut niveau et force plutôt l’utilisation de types de données de bas niveau.

## <a name="syntax"></a>Syntaxe

>  *bibliothèque de types* #import **raw_native_types**

## <a name="remarks"></a>Notes

Par défaut, les méthodes de gestion des erreurs de haut niveau utilisent les classes de prise en charge COM [_bstr_t](../cpp/bstr-t-class.md) et [_variant_t](../cpp/variant-t-class.md) à la place des `BSTR` types de `VARIANT` données et et des pointeurs d’interface com bruts. Ces classes encapsulent les détails de l'allocation et de la libération du stockage de mémoire pour ces types de données, et simplifient considérablement le casting de type et les opérations de conversion.

**FIN de la section spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
