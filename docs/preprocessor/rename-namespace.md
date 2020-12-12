---
description: 'En savoir plus sur les éléments suivants : rename_namespace l’attribut import'
title: rename_namespace l’attribut d’importation
ms.date: 08/29/2019
f1_keywords:
- rename_namespace
helpviewer_keywords:
- rename_namespace attribute
ms.assetid: 45006d2b-36cd-4bec-98b9-3b8ec45299e3
ms.openlocfilehash: 402d9c9cd8dee5979dd71e16fec1a606d8b4b996
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167381"
---
# <a name="rename_namespace-import-attribute"></a>rename_namespace l’attribut d’importation

**Section spécifique à C++**

Renomme l'espace de noms qui contient le contenu de la bibliothèque de types.

## <a name="syntax"></a>Syntaxe

> rename_namespace de la *bibliothèque de types* **#import** **(** "*NewName*" **)**

### <a name="parameters"></a>Paramètres

*NewName*\
Nom du nouvel espace de noms.

## <a name="remarks"></a>Notes

L’attribut **rename_namespace** accepte un argument unique, *NewName*, qui spécifie le nouveau nom de l’espace de noms.

Pour supprimer l’espace de noms, utilisez plutôt l’attribut [no_namespace](../preprocessor/no-namespace.md) .

**FIN de la section spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
