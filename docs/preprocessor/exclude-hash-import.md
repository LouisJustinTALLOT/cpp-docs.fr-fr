---
description: 'En savoir plus sur : exclure l’attribut d’importation'
title: exclure l’attribut d’importation
ms.date: 08/29/2019
f1_keywords:
- exclude
helpviewer_keywords:
- exclude attribute
ms.assetid: 0883248a-d4bf-420e-9848-807b28fa976e
ms.openlocfilehash: e856544f812fd5d0b14676beb8423c4350e40da1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269313"
---
# <a name="exclude-import-attribute"></a>exclure l’attribut d’importation

**Section spécifique à C++**

Exclut des éléments des fichiers d'en-tête de bibliothèque de types en cours de création.

## <a name="syntax"></a>Syntaxe

> **#import** *type-library* **Exclude (** "*nom1*" [ **,** "*nom2*"...] **)**

### <a name="parameters"></a>Paramètres

*Name1*\
Premier élément à exclure.

*Nom2*\
Facultatif Deuxième et dernière éléments à exclure, si nécessaire.

## <a name="remarks"></a>Notes

Les bibliothèques de types peuvent inclure des définitions d'éléments définis dans les en-têtes système ou dans d'autres bibliothèques de types. Cet attribut peut prendre un nombre quelconque d’arguments, où chacun d’eux est un élément de bibliothèque de types de niveau supérieur à exclure.

**FIN de la section spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
