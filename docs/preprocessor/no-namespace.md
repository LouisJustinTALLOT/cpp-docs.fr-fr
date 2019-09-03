---
title: no_namespace importer l’attribut
ms.date: 08/29/2019
f1_keywords:
- no_namespace
helpviewer_keywords:
- no_namespace attribute
ms.assetid: 5d81b741-a558-451b-b493-1f3b18967337
ms.openlocfilehash: ba52aed69cdbb46c135e6de5078d718e93f99c87
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220737"
---
# <a name="no_namespace-import-attribute"></a>no_namespace importer l’attribut

**C++Plus**

Spécifie que le compilateur ne génère pas de nom d’espace de noms.

## <a name="syntax"></a>Syntaxe

> **#import** *bibliothèque de types* **no_namespace**

## <a name="remarks"></a>Notes

Le contenu de la bibliothèque de types dans le fichier d'en-tête `#import` est normalement défini dans un espace de noms. Le nom de l’espace de noms `library` est spécifié dans l’instruction du fichier IDL d’origine. Si l’attribut **no_namespace** est spécifié, cet espace de noms n’est pas généré par le compilateur.

Si vous souhaitez utiliser un nom d’espace de noms différent, utilisez l’attribut [rename_namespace](../preprocessor/rename-namespace.md) à la place.

**Spécifique C++ à la fin**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
