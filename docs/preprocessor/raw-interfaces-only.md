---
title: raw_interfaces_only importer l’attribut
ms.date: 08/29/2019
f1_keywords:
- raw_interfaces_only
helpviewer_keywords:
- raw_interfaces_only attribute
ms.assetid: 87056c6d-3f34-4248-af58-f5775a35bfb7
ms.openlocfilehash: 4b79aa4dbafa204d84f4d6ed7ec78fdec1b81fa7
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216207"
---
# <a name="raw_interfaces_only-import-attribute"></a>raw_interfaces_only importer l’attribut

**C++Plus**

Supprime la génération des fonctions wrapper de gestion des erreurs, et les déclarations de [propriété](../cpp/property-cpp.md) qui utilisent ces fonctions wrapper.

## <a name="syntax"></a>Syntaxe

> **#import** *bibliothèque de types* **raw_interfaces_only**

## <a name="remarks"></a>Notes

L’attribut **raw_interfaces_only** entraîne également le préfixe par défaut utilisé pour nommer les fonctions sans propriété à supprimer. Normalement, le préfixe `raw_`est. Si cet attribut est spécifié, les noms de fonction sont pris directement à partir de la bibliothèque de types.

Cet attribut vous permet d'exposer uniquement le contenu de bas niveau de la bibliothèque de types.

**Spécifique C++ à la fin**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
