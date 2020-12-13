---
description: 'En savoir plus sur les éléments suivants : no_namespace l’attribut import'
title: no_namespace l’attribut d’importation
ms.date: 08/29/2019
f1_keywords:
- no_namespace
helpviewer_keywords:
- no_namespace attribute
ms.assetid: 5d81b741-a558-451b-b493-1f3b18967337
ms.openlocfilehash: e1503015f455af65a138e4e3e6843fd0516d2773
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333316"
---
# <a name="no_namespace-import-attribute"></a>no_namespace l’attribut d’importation

**Section spécifique à C++**

Spécifie que le compilateur ne génère pas de nom d’espace de noms.

## <a name="syntax"></a>Syntaxe

>  *bibliothèque de types* #import **no_namespace**

## <a name="remarks"></a>Notes

Le contenu de la bibliothèque de types dans le fichier d'en-tête `#import` est normalement défini dans un espace de noms. Le nom de l’espace de noms est spécifié dans l' `library` instruction du fichier IDL d’origine. Si l’attribut **no_namespace** est spécifié, cet espace de noms n’est pas généré par le compilateur.

Si vous souhaitez utiliser un nom d’espace de noms différent, utilisez plutôt l’attribut [rename_namespace](../preprocessor/rename-namespace.md) .

**FIN de la section spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
