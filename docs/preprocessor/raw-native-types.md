---
title: raw_native_types importer l’attribut
ms.date: 08/29/2019
f1_keywords:
- raw_native_types
helpviewer_keywords:
- raw_native_types attribute
ms.assetid: 9f38daa8-8dc0-46a5-aff9-f1ff9c1e6f48
ms.openlocfilehash: eb08a8e7cb081bd7a470c3c1ecf1492a7a65f833
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216071"
---
# <a name="raw_native_types-import-attribute"></a>raw_native_types importer l’attribut

**C++Plus**

Désactive l’utilisation des classes de prise en charge COM dans les fonctions wrapper de haut niveau et force plutôt l’utilisation de types de données de bas niveau.

## <a name="syntax"></a>Syntaxe

> **#import** *bibliothèque de types* **raw_native_types**

## <a name="remarks"></a>Notes

Par défaut, les méthodes de gestion des erreurs de haut niveau utilisent les classes de prise en charge com [_ bstr_t](../cpp/bstr-t-class.md) et `BSTR` [_ variant_t](../cpp/variant-t-class.md) à la place des types de données et `VARIANT` et des pointeurs d’interface com bruts. Ces classes encapsulent les détails de l'allocation et de la libération du stockage de mémoire pour ces types de données, et simplifient considérablement le casting de type et les opérations de conversion.

**Spécifique C++ à la fin**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
