---
title: inject_statement importer l’attribut
ms.date: 08/29/2019
f1_keywords:
- inject_statement
helpviewer_keywords:
- inject_statement attribute
ms.assetid: 07d6f0f4-d9fb-4e18-aa62-f235f142ff5e
ms.openlocfilehash: 25dee621ff8af2c9a39e605b9da2c29d80f9570a
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220992"
---
# <a name="inject_statement-import-attribute"></a>inject_statement importer l’attribut

**C++Plus**

Insère son argument en tant que texte source dans l’en-tête de bibliothèque de types.

## <a name="syntax"></a>Syntaxe

> **#import** *bibliothèque de types* **inject_statement (** "*source-Text*" **)**

### <a name="parameters"></a>Paramètres

*texte source*\
Texte source à insérer dans le fichier d'en-tête de bibliothèque de types.

## <a name="remarks"></a>Notes

Le texte est placé au début de la déclaration d’espace de noms qui encapsule le contenu de la *bibliothèque de types* dans le fichier d’en-tête.

**Spécifique C++ à la fin**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
