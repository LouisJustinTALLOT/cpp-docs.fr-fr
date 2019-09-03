---
title: rename_namespace importer l’attribut
ms.date: 08/29/2019
f1_keywords:
- rename_namespace
helpviewer_keywords:
- rename_namespace attribute
ms.assetid: 45006d2b-36cd-4bec-98b9-3b8ec45299e3
ms.openlocfilehash: d319d7390e7c7dce070a35be44aad37c7a34e1a0
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216658"
---
# <a name="rename_namespace-import-attribute"></a>rename_namespace importer l’attribut

**C++Plus**

Renomme l'espace de noms qui contient le contenu de la bibliothèque de types.

## <a name="syntax"></a>Syntaxe

> **#import** *bibliothèque de types* **rename_namespace (** «*NewName*» **)**

### <a name="parameters"></a>Paramètres

*NewName*\
Nom du nouvel espace de noms.

## <a name="remarks"></a>Notes

L’attribut **rename_namespace** prend un argument unique, *NewName*, qui spécifie le nouveau nom de l’espace de noms.

Pour supprimer l’espace de noms, utilisez l’attribut [no_namespace](../preprocessor/no-namespace.md) à la place.

**Spécifique C++ à la fin**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
