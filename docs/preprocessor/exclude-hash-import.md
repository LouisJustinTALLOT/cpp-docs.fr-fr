---
title: exclure l’attribut d’importation
ms.date: 08/29/2019
f1_keywords:
- exclude
helpviewer_keywords:
- exclude attribute
ms.assetid: 0883248a-d4bf-420e-9848-807b28fa976e
ms.openlocfilehash: 6a3625ee0dd44f3e2731e1240fea5f3dd4ed109e
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218719"
---
# <a name="exclude-import-attribute"></a>exclure l’attribut d’importation

**C++Plus**

Exclut des éléments des fichiers d'en-tête de bibliothèque de types en cours de création.

## <a name="syntax"></a>Syntaxe

> **#import** *bibliothèque de types* **Exclude (** "*nom1*" [ **,** "*nom2*"...] **)**

### <a name="parameters"></a>Paramètres

*Name1*\
Premier élément à exclure.

*Nom2*\
Facultatif Deuxième et dernière éléments à exclure, si nécessaire.

## <a name="remarks"></a>Notes

Les bibliothèques de types peuvent inclure des définitions d'éléments définis dans les en-têtes système ou dans d'autres bibliothèques de types. Cet attribut peut prendre un nombre quelconque d’arguments, où chacun d’eux est un élément de bibliothèque de types de niveau supérieur à exclure.

**Spécifique C++ à la fin**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
