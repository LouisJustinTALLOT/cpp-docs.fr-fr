---
description: 'En savoir plus sur les éléments suivants : no_smart_pointers l’attribut import'
title: no_smart_pointers l’attribut d’importation
ms.date: 08/29/2019
f1_keywords:
- no_smart_pointers
helpviewer_keywords:
- no_smart_pointers attribute
ms.assetid: d69dd71e-08a8-4446-a3d0-a062dc29cb17
ms.openlocfilehash: cf2299668a2e1b24cdf45069766466f448ee9d66
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333280"
---
# <a name="no_smart_pointers-import-attribute"></a>no_smart_pointers l’attribut d’importation

**Section spécifique à C++**

Supprime la création des pointeurs intelligents pour toutes les interfaces dans la bibliothèque de types.

## <a name="syntax"></a>Syntaxe

>  *bibliothèque de types* #import **no_smart_pointers**

## <a name="remarks"></a>Notes

Par défaut, lorsque vous utilisez `#import`, vous obtenez une déclaration de pointeur intelligent pour toutes les interfaces dans la bibliothèque de types. Ces pointeurs intelligents sont de type [_com_ptr_t](../cpp/com-ptr-t-class.md).

**FIN de la section spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
