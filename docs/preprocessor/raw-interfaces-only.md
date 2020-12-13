---
description: 'En savoir plus sur les éléments suivants : raw_interfaces_only l’attribut import'
title: raw_interfaces_only l’attribut d’importation
ms.date: 08/29/2019
f1_keywords:
- raw_interfaces_only
helpviewer_keywords:
- raw_interfaces_only attribute
ms.assetid: 87056c6d-3f34-4248-af58-f5775a35bfb7
ms.openlocfilehash: f043bef5cde0454ce9f08f45efb0417aa7fdbb2d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142738"
---
# <a name="raw_interfaces_only-import-attribute"></a>raw_interfaces_only l’attribut d’importation

**Section spécifique à C++**

Supprime la génération des fonctions wrapper de gestion des erreurs, et les déclarations de [propriété](../cpp/property-cpp.md) qui utilisent ces fonctions wrapper.

## <a name="syntax"></a>Syntaxe

>  *bibliothèque de types* #import **raw_interfaces_only**

## <a name="remarks"></a>Notes

L’attribut **raw_interfaces_only** entraîne également le préfixe par défaut utilisé pour nommer les fonctions sans propriété à supprimer. Normalement, le préfixe est `raw_` . Si cet attribut est spécifié, les noms de fonction sont pris directement à partir de la bibliothèque de types.

Cet attribut vous permet d'exposer uniquement le contenu de bas niveau de la bibliothèque de types.

**FIN de la section spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
