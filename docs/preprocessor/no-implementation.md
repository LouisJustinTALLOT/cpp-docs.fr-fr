---
description: 'En savoir plus sur les éléments suivants : no_implementation l’attribut import'
title: no_implementation l’attribut d’importation
ms.date: 08/29/2019
f1_keywords:
- no_implementation
helpviewer_keywords:
- no_implementation attribute
ms.assetid: bdc67785-e131-409c-87bc-f4d2f4abb07b
ms.openlocfilehash: 0cfd51b344847d2e5658fd4e4ec1a9f30db51fe6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333330"
---
# <a name="no_implementation-import-attribute"></a>no_implementation l’attribut d’importation

**Section spécifique à C++**

Supprime la génération de l' `.tli` en-tête, qui contient les implémentations des fonctions membres wrapper.

## <a name="syntax"></a>Syntaxe

>  *bibliothèque de types* #import **no_implementation**

## <a name="remarks"></a>Notes

Si cet attribut est spécifié, l' `.tlh` en-tête, avec les déclarations pour exposer des éléments de bibliothèque de types, est généré sans `#include` instruction pour inclure le `.tli` fichier d’en-tête.

Cet attribut est utilisé conjointement avec [implementation_only](../preprocessor/implementation-only.md).

**FIN de la section spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
