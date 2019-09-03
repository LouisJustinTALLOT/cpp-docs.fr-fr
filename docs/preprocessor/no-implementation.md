---
title: no_implementation importer l’attribut
ms.date: 08/29/2019
f1_keywords:
- no_implementation
helpviewer_keywords:
- no_implementation attribute
ms.assetid: bdc67785-e131-409c-87bc-f4d2f4abb07b
ms.openlocfilehash: 8f0a7454fdbedc1959b665ccb2a23748d21c342d
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220768"
---
# <a name="no_implementation-import-attribute"></a>no_implementation importer l’attribut

**C++Plus**

Supprime la génération de l' `.tli` en-tête, qui contient les implémentations des fonctions membres wrapper.

## <a name="syntax"></a>Syntaxe

> **#import** *bibliothèque de types* **no_implementation**

## <a name="remarks"></a>Notes

Si cet attribut est spécifié, l' `.tlh` en-tête, avec les déclarations pour exposer des éléments de bibliothèque de types, est `#include` généré sans instruction pour `.tli` inclure le fichier d’en-tête.

Cet attribut est utilisé conjointement avec [implementation_only](../preprocessor/implementation-only.md).

**Spécifique C++ à la fin**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
