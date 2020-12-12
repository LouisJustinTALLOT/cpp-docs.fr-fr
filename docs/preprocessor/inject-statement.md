---
description: 'En savoir plus sur les éléments suivants : inject_statement l’attribut import'
title: inject_statement l’attribut d’importation
ms.date: 08/29/2019
f1_keywords:
- inject_statement
helpviewer_keywords:
- inject_statement attribute
ms.assetid: 07d6f0f4-d9fb-4e18-aa62-f235f142ff5e
ms.openlocfilehash: b7ab8059e95ed3799857fe1b899ef2efff729ffb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97236423"
---
# <a name="inject_statement-import-attribute"></a>inject_statement l’attribut d’importation

**Section spécifique à C++**

Insère son argument en tant que texte source dans l’en-tête de bibliothèque de types.

## <a name="syntax"></a>Syntaxe

> **#import** *de la bibliothèque de types* **inject_statement (** "*source-Text*" **)**

### <a name="parameters"></a>Paramètres

*texte source*\
Texte source à insérer dans le fichier d'en-tête de bibliothèque de types.

## <a name="remarks"></a>Notes

Le texte est placé au début de la déclaration d’espace de noms qui encapsule le contenu de la *bibliothèque de types* dans le fichier d’en-tête.

**FIN de la section spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
