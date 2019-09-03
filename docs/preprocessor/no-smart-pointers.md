---
title: no_smart_pointers importer l’attribut
ms.date: 08/29/2019
f1_keywords:
- no_smart_pointers
helpviewer_keywords:
- no_smart_pointers attribute
ms.assetid: d69dd71e-08a8-4446-a3d0-a062dc29cb17
ms.openlocfilehash: 1fca3eb486ff3cfc7403c38e91855b799a698782
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220691"
---
# <a name="no_smart_pointers-import-attribute"></a>no_smart_pointers importer l’attribut

**C++Plus**

Supprime la création des pointeurs intelligents pour toutes les interfaces dans la bibliothèque de types.

## <a name="syntax"></a>Syntaxe

> **#import** *bibliothèque de types* **no_smart_pointers**

## <a name="remarks"></a>Notes

Par défaut, lorsque vous utilisez `#import`, vous obtenez une déclaration de pointeur intelligent pour toutes les interfaces dans la bibliothèque de types. Ces pointeurs intelligents sont de type [_com_ptr_t](../cpp/com-ptr-t-class.md).

**Spécifique C++ à la fin**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
