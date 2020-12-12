---
description: 'En savoir plus sur les éléments suivants : raw_dispinterfaces l’attribut import'
title: raw_dispinterfaces l’attribut d’importation
ms.date: 08/29/2019
f1_keywords:
- raw_dispinterfaces
helpviewer_keywords:
- raw_dispinterfaces attribute
ms.assetid: f762864d-29bf-445b-825a-ba7b29a95409
ms.openlocfilehash: 447f76bdee16d2719c02ad4a73883f8f176f2584
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202013"
---
# <a name="raw_dispinterfaces-import-attribute"></a>raw_dispinterfaces l’attribut d’importation

**Section spécifique à C++**

Indique au compilateur de générer des fonctions wrapper de bas niveau pour les méthodes dispinterface, et pour les propriétés qui appellent `IDispatch::Invoke` et retournent le code d’erreur HRESULT.

## <a name="syntax"></a>Syntaxe

>  *bibliothèque de types* #import **raw_dispinterfaces**

## <a name="remarks"></a>Notes

Si cet attribut n’est pas spécifié, seuls les wrappers de haut niveau sont générés, ce qui lève des exceptions C++ en cas d’échec.

**FIN de la section spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
