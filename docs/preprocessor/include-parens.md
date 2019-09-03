---
title: attribut d’importation include ()
ms.date: 08/29/2019
f1_keywords:
- include()
helpviewer_keywords:
- include() attribute
ms.assetid: 86c9dcb2-d9e0-4fd5-97d7-0bb3e23d6ecc
ms.openlocfilehash: 39ab63525b2b83781cbcaf86a61742c5fb767b72
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218869"
---
# <a name="include-import-attribute"></a>attribut d’importation include ()

**C++Plus**

Désactive l'exclusion automatique.

## <a name="syntax"></a>Syntaxe

> **#import** *bibliothèque de types* **include ("** _nom1_ **"** [ __, "__ *nom2* __"__ ...] __)__

### <a name="parameters"></a>Paramètres

*Name1*\
Premier élément à inclure de force.

*Nom2*\
Deuxième élément à inclure de force (si nécessaire).

## <a name="remarks"></a>Notes

Les bibliothèques de types peuvent inclure des définitions d'éléments définis dans les en-têtes système ou dans d'autres bibliothèques de types. `#import` tente d'éviter les erreurs de définitions multiples en excluant automatiquement ces éléments. Si certains éléments ne doivent pas être exclus automatiquement, vous pouvez voir [Avertissement du compilateur (niveau 3) C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md). Vous pouvez utiliser cet attribut pour désactiver l’exclusion automatique. Cet attribut peut prendre un nombre quelconque d’arguments, un pour chaque nom d’un élément de bibliothèque de types à inclure.

**Spécifique C++ à la fin**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
